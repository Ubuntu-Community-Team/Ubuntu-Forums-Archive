---
title: "Arch LInux WUSB600Nv2"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by Gemu on 2010-11-09
I have WUSB600Nv2 working fine in Ubuntu 10.04 but can't get it to compile in Arch Linux.

By default - target platform is set to PC

#PLATFORM: Target platform
PLATFORM = PC
#PLATFORM = 5VT
#PLATFORM = IKANOS_V160

Which points to this-

ifeq ($(PLATFORM),PC)
# Linux 2.6
LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
#LINUX_SRC = /usr/src/linux-2.4
LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/net/wireless/
CROSS_COMPILE = 
endif

In Arch there is no build file in the /lib/modules/2.6.35-ARCH folder.

So I get an error -file does not exist.

has anyone got this set up in Arch?

---

### Post by Gemu on 2010-11-11
Bump. No one? I am clueless on this issue.

 This is the output of sudo make -

sudo make
Password: 
make -C tools
make[1]: Entering directory `/usr/src/RT3572/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/usr/src/RT3572/tools'
/usr/src/RT3572/tools/bin2h
cp -f os/linux/Makefile.6 /usr/src/RT3572/os/linux/Makefile
make -C /lib/modules/2.6.35-ARCH/build SUBDIRS=/usr/src/RT3572/os/linux modules
make: *** /lib/modules/2.6.35-ARCH/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

---

### Post by Gemu on 2010-11-20
Turns out all I needed was the linux header package from the ARCH package list.  The Makefile asks for /lib/modules/2.6-35-ARCH/build and build doesn't exist within the kernel folder without installing the headers package in ARCH. 

 The file I downloaded from Ralink would still not compile until I did as suggested here -[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/77]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/77").-

 A little file name changing.... 

In order to get the driver to compile, edit ../include/os/rt_linux.h and change all instances of "usb_buffer_alloc" to "usb_alloc_coherent" and all instances of "usb_buffer_free" to "usb_free_coherent". From what I can tell, there is only once occurrence of each, on lines 1077 and 1078, respectively.

 My Ubuntu 10.04 install didn't require this name changing.




  I like to unzip the driver into /usr/src/ and rename it to RT3572 so it is unaffected by system updates.  I run a script titled rt3572_install.sh in my home folder to reinstall it quickly if needed. This script assumes you all ready have it installed. 

 sudo ./rt3572_install 


#!/bin/bash

cd /usr/src/RT3572
make
make install
ifconfig ra0 down
rmmod rt3572sta

cd /lib/modules/`uname -r`/wireless/
sudo mv rt3572sta.ko rt3572sta.ko.dist

cd /usr/src/RT3572/os/linux
sudo cp rt3572sta.ko /lib/modules/`uname -r`/wireless/

sudo modprobe rt3572sta
exit 0

Thanks

---

### Post by uncaspi on 2010-11-20
Good work:D

---

