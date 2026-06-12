---
title: "dvbt +af9015 +mxl5007t"
date: 2010-07-24
forum: Multimedia Software
---

### Post by rezas on 2010-07-24
Hi dear guys
i have a usb dvbt stick that seems does not have support in linux

it uses af9015 & mxl5007 

it does not work in linux but i can see both driver chips in the kernel

see /usr/src/linux/drivers/media/dvb/dvb-usb/af9015.c 
also /usr/src/linux/drivers/media/common/tuners/mxl5007t.c

> lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick> dmesg |grep 9015
[   13.291257] dvb_usb_af9015 1-1:1.0: usb_probe_interface
[   13.291261] dvb_usb_af9015 1-1:1.0: usb_probe_interface - got id
[   13.687679] af9015: tuner id:177 not supported, please report!
[   13.687762] usbcore: registered new interface driver dvb_usb_af9015
can anyone help???

---

### Post by TopEnder on 2010-07-25
> **rezas said:**
> Hi dear guys
i have a usb dvbt stick that seems does not have support in linux

it uses af9015 & mxl5007 

it does not work in linux but i can see both driver chips in the kernel

see /usr/src/linux/drivers/media/dvb/dvb-usb/af9015.c 
also /usr/src/linux/drivers/media/common/tuners/mxl5007t.c

can anyone help???
G'Day,  What happens if you, with the USB stick plugged in scan for Hardware Drivers?  Using  [COLOR="Blue"]Systems/Adminstration/Hardware Drivers[/COLOR]

---

### Post by rezas on 2010-07-25
HI
thanks for answer
> G'Day,  What happens if you, with the USB stick plugged in scan for Hardware Drivers?  Using  [COLOR=Blue]Systems/Adminstration/Hardware Drivers[/COLOR]it only offers to install dvb firmware 
i have done it before!:(:(

this problem is  deeper  than you imagine

---

### Post by vanlindholm on 2011-03-21
see my post on [http://ubuntuforums.org/showthread.php?t=606487&page=22](http://ubuntuforums.org/showthread.php?t=606487&page=22) . Hopefully this will help you

---

