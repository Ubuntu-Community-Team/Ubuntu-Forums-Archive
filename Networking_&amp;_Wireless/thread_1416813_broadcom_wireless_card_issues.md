---
title: "broadcom wireless card issues"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by pman860507 on 2010-02-26
frist off let me say im still pretty new to ubuntu.

i am trying to install the b43 driver for my wireless card.  the card i have is broadcom 802.11b/g Wlan


```
lspci -n | grep 14e4
01:00.0 0280: 14e4:4315 (rev 01)
```
> If 14e4:XXXX is 4301, 4307, 4311, 4312, 4318, 4319, 4320, 4321 (aka 4306 802.11b/g? only), 4324, or 4325, the card is supported with b43 driver.

All others are with 4313, 4315 (4310?), 4328 (4321 802.11n dualband), 4329 (4321 802.11n 2.4GHz), 432a (4321 802.11 5GHz), 432b (4322), 432c, 432d can only use broadcom's linux_sta driver, which is similar to using ndiswrapper.i did try this but i couldn't get anywhere with is.

sources:
```
http://ubuntuforums.org/showthread.php?t=1266620
``````
https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper
```> b43 driver for linux-2.6.24 (Ultimate Edition 1.8/Ubuntu 8.04)
If you are using the b43 driver from linux-2.6.24, follow these instructions. 
Use version 011 of b43-fwcutter. 
Download, extract the b43-fwcutter tarball and build it: 

```
wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011\
make
cd ..
```Use version 4.80.53.0 of Broadcom's proprietary driver. 
Download and extract the firmware from this driver tarball: 

```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```Note that you must adjust the FIRMWARE_INSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place.```
http://forumubuntusoftware.info/viewtopic.php?f=7&t=1047
```on this one i can only get this part done

```
wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011\
make
cd ..
```once i get to the make command i dont know what to do. 

and for the next set of commands i dont really understand the export command.  if i need to provide any more information let me know thanks in advance.

---

### Post by pastalavista on 2010-02-26
after the make command (in the same directory) enter```
make install
```then open System|Administration|Hardware Drivers and the driver should be ready to activate.

---

### Post by pman860507 on 2010-02-26
```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources...0.53.0.tar.bz2]("http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2")
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```What about this part. i got it installed. but i still cant figure out that export part. or do i not need it

---

### Post by pastalavista on 2010-02-26
I believe that the export command is only to make sure the files are extracted to the correct directory in case certain OS's require it. Ubuntu will use it wherever you install it. If it is not in your home dirrectory, you'll need to use sudo before the make and make install commands.

---

### Post by pman860507 on 2010-02-26
is there a command i can type in to activate the driver? because i dont believe im doing it right. i rebooted and my iwconfig says no wireless extensions.

---

### Post by pastalavista on 2010-02-26
Use the Hardware Drivers tool to activate it.

---

### Post by pman860507 on 2010-02-26
when i run 

```
sudo lshw -C network

*-network
description: Network controller
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:01:00.0
version:01
width 64 bits
clock: 33MHz
capabilites: pm msi pciexpress bus_master cap_list
configeration: driver=b43-pci-bridge latency=0
```

---

