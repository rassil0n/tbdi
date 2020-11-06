# tbdi - the bootstrap debian install

The script will install a full config of Debian (stable, testing, unstable) via debootstrap on your machine.

The configs come from [here](https://github.com/fl0-1337/dots).

I know the code is a quite a mess, but it works ;) I do my very best to optimize and clean the code.

## ATTENTION

Mind the following points:

- In the current state only legacy-boot is tested and viable.
- The UEFI-Install is not tested, so no warranty.
- Custom partitions are not implemented yet
- The script will wipe your complete harddrive, so please be careful

## install

In oder to install boot your machine with any debian-based live distro and follow this steps:

1. `git clone https://github.com/fl0-1337/tbdi && cd tbdi`
2. `sudo su`
3. `./install`

## custom partitions (not implemented yet)

The script will do the partitoning automatically in this layout:

- /dev/sdX1 - boot-partition # if you choose efi-install
- /dev/sdX2 - swap-partition # if you choose to have one
- /dev/sdX3 - root-partition # will be 30G
- /dev/sdX4 - home-partition # will be the rest of your harddrive

The first two partitions are optional, depending on your choice in the install process.

If you want to have a custom layout, follow this steps:

- make partitions
- mount the root-partition to `/mnt`
- mount the boot-partition to `/mnt/boot`
- make `swapon` if you have a swap partion
- run `./install -c`

### installprocess

Through the installation you will be asked which architecture, bootoption, swapsize, packages you want to install.

After this the script runs almost complete for itself, besides queries for timezone-, locales- and keyboard-configuration.

## create additional user

If you want to create another user after installing tbdi, run the following command:

`./tbdi/bin/tbdi_user <USERNAME>`
