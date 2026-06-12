---
title: "atheros (attansic) ethernet adaptor drivers"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by chrislegg on 2009-11-09
After one year happily testing Ubuntu (8.04, now upgraded to 9.10) on asus eee1000, decided to go for full desktop and do all my work in Linux. Specified no operating system, but new computer delivered with Windows Vista. Installed Ubuntu 8.04 from DVD, with intention of upgrading from Internet. No Internet connection in Ubuntu, but works in Windows. Found that ethernet adaptor is Attansic (now Atheros), not supported in 8.04. Tried to install driver, with much help from various Ubuntu forums. Installation failed repeatedly. Below are results of failed installation:-

#atl1e drivers from l1e-linux-v1.0.1.0
list of files
at_ethtool.c  atl1e.7      at_main.o   kcompat_ethtool.c  Module.symvers
at_ethtool.o  atl1e.ko     at_osdep.h  kcompat.h          readme
at.h          atl1e.mod.c  at_param.c  kcompat.o
at_hw.c       atl1e.mod.o  at_param.o  ldistrib.txt
at_hw.h       atl1e.o      copying     Makefile
at_hw.o       at_main.c    kcompat.c   Makefile~

christopher@christopher-desktop:~$ cd drivers
christopher@christopher-desktop:~/drivers$ sudo make
[sudo] password for christopher: 
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/christopher/drivers modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
christopher@christopher-desktop:~/drivers$ sudo make install
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/christopher/drivers modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** No rule to make target `../atl1e.7', needed by `atl1e.7.gz'. Stop.
christopher@christopher-desktop:~/drivers$ cd

#atl1e drivers from l1e-l2e-linux-v1.0.0.4
list of files
at_ethtool.c  at_hw.o      at_main.c   kcompat.c          Module.symvers
at_ethtool.o  atl1e.ko     at_main.o   kcompat_ethtool.c
at.h          atl1e.mod.c  at_osdep.h  kcompat.h
at_hw.c       atl1e.mod.o  at_param.c  kcompat.o
at_hw.h       atl1e.o      at_param.o  Makefile

christopher@christopher-desktop:~$ cd src
christopher@christopher-desktop:~/src$ sudo make
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/christopher/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not open /home/christopher/src/at_main.c: Invalid argument
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
christopher@christopher-desktop:~/src$ sudo make install
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/christopher/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not open /home/christopher/src/at_main.c: Invalid argument
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** No rule to make target `../atl1e.7', needed by `atl1e.7.gz'. Stop.
christopher@christopher-desktop:~/src$ cd
christopher@christopher-desktop:~$ 

I obtained drivers from two different sources. Installation was not successful (no new driver files created in .../drivers/net/) and insmod did not work. It looks to me as though makefile (attached) has error, but I cannot decipher it

In desperation, I decided to try to upgrade Ubuntu to 9.10 using USB flash drive. I had used this installation method for my eee 1000, so made a new bootable stick using 9.10 ISO. My computer refuses to recognise the USB stick as boot drive. Perhaps because there is already a Ubuntu partition?

I need help. I rely on the new machine for my work, and without internet connection I cannot work in Ubuntu. I do not wish to be forced to use Vista! I need either to install correct driver for Atheros, and then upgrade Ubuntu via web, or else to install 9.10 directly, hopefully then with Atheros support.

---

### Post by NotWindowsXPagain50 on 2009-11-09
Ubuntu 8.04 is old:!:

Upgrade to 9.10:!:

This means better driver and program support

Edit: How does the beans system work?

---

### Post by chrislegg on 2009-11-10
The whole point is that I am trying to upgrade  to 9.10, but  cannot without internet connection, and for that I need a driver

---

