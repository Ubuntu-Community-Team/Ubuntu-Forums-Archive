---
title: "accelerated 3d graphics radeonhd 3xxx/4xxx seriesATI r6xx/r7xx drivers ,amd64"
date: 2010-04-28
forum: Multimedia Software
---

### Post by kronictokr on 2010-04-28
IMPORTANT, READ **NOTE** BEFORE CONTINUING!!!!!!!!!
AND BACKUP IMPORTANT INFO!!!!

IF THE   code:    IS NOT SPECIFIED, ITS FOR BOTH LUCID AND KARMIC

LUCID START AT PART 2!!!!!!!!!

**note** this has been tested on hp pavilion dv6/dv7 with amd64 and ati radeon hd 4xxx series, and radeon hd 3xxx series, using r6xx/r7xx drivers.     also, do NOT install enable other graphics drivers, for obvious reasons, simply enable advanced in appearance/visual effects **end note**

IMPORTANT, READ **NOTE** BEFORE CONTINUING!!!!!!!!!
AND BACKUP IMPORTANT INFO!!!!


Code:
mkdir kerneldebs

Code:
cd kerneldebs/

Code:
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_amd64.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb")

Code:
sudo dpkg -i linux*

new terminal

Code:
echo vesafb | sudo tee -a /etc/initramfs-tools/modules

Code:
echo fbcon | sudo tee -a /etc/initramfs-tools/modules

Code:
sudo update-initramfs -u

Code:
sudo update-grub

Code:
sudo reboot


you'll have to reboot in low graphics mode for now, at least untill were done

make sure youre menu.list is recent and up to date
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Manually_add_repositories](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Manually_add_repositories)

this is what i use, for karmic

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic main
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates main
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


now thats done, open another terminal

Code:
sudo aptitude update

Code:
sudo reboot

#############################################################

PART 2                                                      #

#############################################################

Karmic continue her after the reboot, Lucid begin here

if you have a graphics drivers already installed this will work to remove fglrx, or catalyst

code:
sudo sh /usr/share/ati/fglrx-uninstall.sh

code:
sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev

code:
sudo aptitude update

Code:
sudo aptitude install libvirt-bin qemu kvm ubuntu-vm-builder bridge-utils virt-viewer

tab , hit enter, choose "no connection" hit enter

when done, still in terminal

you may not have to do this, but i havent had any problems using it. this is if you plan on using compiz

Code:
mkdir -p $HOME/.config/compiz

Code:
echo 'WHITELIST="$WHITELIST radeonhd"' >> $HOME/.config/compiz/compiz-manager


now we are going to configure a few files to ensure a successfull load of all our programs and drivers.

to do this the easy way, still in our terminal, or open a new one.
we do

code:
gksudo nautilus

click on the left filesystem. go to this path  /etc/default/grub, double clicking the grub file.

Add   radeon.modeset=1    to the end of the line
GRUB_CMDLINE_LINUX_DEFAULT=

like so
GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=1"
replacing,    "soft splash"    otion, which has been known to cause issues.
save, close the file.

still in gksudo, next path,     /etc/grub.d/40_custum     , double clicking   40_custom    file, and add      "radeon.modeset=1"     at the bottom of the file, without the quotes, and without changing anything else, save and exit.

for good measure, and to cut down posible errors
To make sure the radeon modules is initialized before gdm (and X) is starting, insert "modprobe radeon" into your /etc/init/gdm.conf just before the gdm-binary is executed:

    ...
    initctl emit starting-dm DM=gdm

    modprobe radeon
    exec gdm-binary $CONFIG_FILE
end script

like so ^^^^ above, save and exit


now exit nautilus, to bring you back into your terminal

for karmic
Code:
cd /lib/firmware/2.6.33-020633-generic/radeon


new lucid kernel/this path may change as the kernel is updated, it would be a safe bet to double check
Code:
cd /lib/firmware/2.6.32-22-generic/radeon

Code:
sudo wget [http://people.freedesktop.org/~agd5f/radeon_ucode/R600_rlc.bin]("http://people.freedesktop.org/%7Eagd5f/radeon_ucode/R600_rlc.bin") [http://people.freedesktop.org/~agd5f/radeon_ucode/R700_rlc.bin]("http://people.freedesktop.org/%7Eagd5f/radeon_ucode/R700_rlc.bin")


close and open a new terminal

Code:
sudo update-initramfs -u

Code:
sudo update-grub

now we want to add the ppa repos so we can upgrade our drivers and enable 3d accelerated graphics.

open your software sources from administration. the go to add source. and add each of these lines one at a time.

karmic

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main

deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) karmic main

close and reload


lucid

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main

deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main

close and reload



open a terminal and paste in the next line and hit enter

Code:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542

Code:
sudo aptitude install xserver-xorg-video-radeonhd

Code:
sudo aptitude upgrade

now we update/notify our system of changes made

First update modules.dep:

Code:
sudo depmod -a $(uname -r)

then
Update the initramfs:

Code:
sudo update-initramfs -u -k $(uname -r)

code:
sudo update-grub

code:
sudo reboot



###OPTIONAL###

you can boot to recovery at this point, and drop into root. you will have had to set your root password for this option.

this section is to configure you "xorg.conf" file. however it is optional, as you can boot without the file. how ever if you want to produce an acurate xorg.conf which you can configure for other options, that you may not be able to do with kmv, then do the following. 

while in root do the following command

code:
sudo Xorg -configure

then

Code:
sudo depmod -a $(uname -r)

then
Update the initramfs:

Code:
sudo update-initramfs -u -k $(uname -r)

code:
sudo update-grub

code:
sudo reboot

---

### Post by jamiet on 2010-11-13
Hi does the above work (or even necessary) for 10.10 Meerkat?

TIA,

JamieT

---

