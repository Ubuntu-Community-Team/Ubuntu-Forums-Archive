---
title: "I'm trying to get my wireless to work and need help"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by NacDrummer on 2009-06-25
I have a Dell Inspirion 1300 with a                            Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) that what i'm trying to connent though i'm running Ubuntu 9.04 i have got the ndiswrapper going(also when to dell and got the driver for my comp there) and i got to this point here's a copy of what i see what do i do?(ps) im a new user so not sure where to start


nathan@nathan-laptop:~$ sudo apt-get install build-essential
[sudo] password for nathan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nathan@nathan-laptop:~$ cd Desktop
nathan@nathan-laptop:~/Desktop$ cd ndiswrapper-1.54
nathan@nathan-laptop:~/Desktop/ndiswrapper-1.54$ ls
AUTHORS    driver   loadndisdriver.8  ndiswrapper.8     README
ChangeLog  INSTALL  Makefile          ndiswrapper.spec  utils
nathan@nathan-laptop:~/Desktop/ndiswrapper-1.54$ make
make -C driver
make[1]: Entering directory `/home/nathan/Desktop/ndiswrapper-1.54/driver'
make -C /usr/src/linux-headers-2.6.28-13-generic M=/home/nathan/Desktop/ndiswrapper-1.54/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  LD      /home/nathan/Desktop/ndiswrapper-1.54/driver/built-in.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/crt_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/crt.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/hal_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/hal.o
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/iw_ndis.o
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/loader.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/ndis_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/ndis.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/ntoskernel_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/ntoskernel.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/ntoskernel_io_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/ntoskernel_io.o
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/pe_linker.o
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/pnp.o
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/proc.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/rtl_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/rtl.o
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/wrapmem.o
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/wrapndis.o
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/wrapper.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/usb_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/usb.o
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/divdi3.o
  LD [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/nathan/Desktop/ndiswrapper-1.54/driver/ndiswrapper.mod.o
  LD [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make[1]: Leaving directory `/home/nathan/Desktop/ndiswrapper-1.54/driver'
make -C utils
make[1]: Entering directory `/home/nathan/Desktop/ndiswrapper-1.54/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/nathan/Desktop/ndiswrapper-1.54/utils'
nathan@nathan-laptop:~/Desktop/ndiswrapper-1.54$ sudo make install
make -C driver install
make[1]: Entering directory `/home/nathan/Desktop/ndiswrapper-1.54/driver'
make -C /usr/src/linux-headers-2.6.28-13-generic M=/home/nathan/Desktop/ndiswrapper-1.54/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/crt_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/crt.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/hal_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/hal.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/ndis_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/ndis.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/ntoskernel_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/ntoskernel.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/ntoskernel_io_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/ntoskernel_io.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/rtl_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/rtl.o
  MKEXPORT /home/nathan/Desktop/ndiswrapper-1.54/driver/usb_exports.h
  CC [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/usb.o
  LD [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/nathan/Desktop/ndiswrapper-1.54/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
echo /lib/modules/2.6.28-13-generic/misc
/lib/modules/2.6.28-13-generic/misc
mkdir -p /lib/modules/2.6.28-13-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.28-13-generic/misc
/sbin/depmod -a 2.6.28-13-generic -b /
make[1]: Leaving directory `/home/nathan/Desktop/ndiswrapper-1.54/driver'
make -C utils install
make[1]: Entering directory `/home/nathan/Desktop/ndiswrapper-1.54/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/nathan/Desktop/ndiswrapper-1.54/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
nathan@nathan-laptop:~/Desktop/ndiswrapper-1.54$ ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
nathan@nathan-laptop:~/Desktop/ndiswrapper-1.54$ -i R108904.exe
bash: -i: command not found
nathan@nathan-laptop:~/Desktop/ndiswrapper-1.54$

---

### Post by NacDrummer on 2009-06-26
i really want my wireless work it been 2 days trying to do the for like 6hrs each day...i'm getting very mad about that. I like linux but errrrrrrrr plz someone help me

---

### Post by dBuster on 2009-06-26
Have you done a search in the forum?  I am sure you are not the only one with that Broadcom wifi issue and just a quick search, one looking like a solution:  

[+JAUNTY"]http://ubuntuforums.org/showthread.php?t=1139412&highlight=BCM4318+[AirForce+54g]+JAUNTY]("http://ubuntuforums.org/showthread.php?t=1139412&highlight=BCM4318+[AirForce+54g)

---

### Post by Iowan on 2009-06-26
[Another]("http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/") link I found (although it is for Intrepid).

---

### Post by superprash2003 on 2009-06-27
have you tried this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) and what about system->admin->hardware drivers

---

