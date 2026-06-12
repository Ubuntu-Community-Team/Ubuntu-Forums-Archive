---
title: "new 8.10 Ibex user, trouble with Brdcm 4306 and ndiswrapper..."
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by ubigT on 2009-01-31
I have been using Ubuntu for about 1 month on my desktop PC and it"s awesome! But I put it on my laptop this week and the wireless hasn't been working... I thought I'd see if I could fix it, but so far no luck.  I followed this tutorial: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

when I get to step 5 it doesn't work, meaning I get an error.

"trevor@trevor-laptop:~/ndiswrapper-1.46$ make
make -C driver
make[1]: Entering directory `/home/trevor/ndiswrapper-1.46/driver'
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/trevor/ndiswrapper-1.46/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/trevor/ndiswrapper-1.46/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/trevor/ndiswrapper-1.46/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/trevor/ndiswrapper-1.46/driver'
make: *** [all] Error 2 "

I have followed this tutorial to a T and this is the second time I have attempted to get this wireless to work.  The first was in Hardy Heron and I followed a different tutorial, it didn't work at all and I scrapped it and formatted my HD to put Ibex on it (my laptop is just for kicks, and now to learn the Terminal and such in Ubuntu)  Any help or hints would be awesome as I am tied to an ethernet cable right now..... and it's annoying.

More info:

 description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64 module=ssb


I know ssb shouldn't be there... but I have no clue how to fix it.

Thanx in advance for any help!

---

### Post by kevdog on 2009-01-31
Why dont you just use the b43 driver?  Older ndiswrapper versions -- the source needs to be patched -- to run on newer kernels.  Or you could use the open source OpenFwwF driver for 4306:

[http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=46:broadcom-guide-for-ubuntu-hardy-and-newer&catid=34:guides&Itemid=61](http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=46:broadcom-guide-for-ubuntu-hardy-and-newer&catid=34:guides&Itemid=61)

[http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=50:openfwwf-open-firmware-for-wi-fi-networks&catid=34:guides&Itemid=61](http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=50:openfwwf-open-firmware-for-wi-fi-networks&catid=34:guides&Itemid=61)

---

