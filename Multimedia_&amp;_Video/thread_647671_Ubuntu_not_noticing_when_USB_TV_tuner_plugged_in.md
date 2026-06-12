---
title: "Ubuntu not noticing when USB TV tuner plugged in"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by Roddy_001 on 2007-12-22
Hi,

I bought a usb tv tuner off ebay and thought that Ubuntu would have at least recognised it when i plugged it in.

The model number off the tuner is DUTV005 - which when a google search is done returns this as the first result: [http://szforwardvideo.en.alibaba.com/product/50120559/200925466/Digital_Ter_DVB_T_TV_Series/Dutv005_Terrestrial_Tv_Receiver.html]("http://szforwardvideo.en.alibaba.com/product/50120559/200925466/Digital_Ter_DVB_T_TV_Series/Dutv005_Terrestrial_Tv_Receiver.html")

When i plug a normal usb stick into the port, Ubuntu automatically mounts it and brings up the drive.

Yet for some reason it isn't with this one. Are there any universal linux tv drivers.. or am i going to have to write drivers myself for it? 

I do have the little software disc that came with it for Windows

however, when i do a "lsusb" the output is as follows.

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 003: ID 8086:9500 Intel Corp.
Bus 006 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 045e:00f1 Microsoft Corp.
Bus 003 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

the USB tv stick is the "Intel Corp", as when i remove it from the computer and do the command again it isn't there

Regards,


Roderick

---

### Post by flehnerz on 2007-12-22
Unfortunately to say your unknown brand tuner probably doesn't work in Linux, or doesn't work easily. I would follow this guide for a tuner that is Linux compatible.
[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)

---

### Post by Roddy_001 on 2007-12-23
Cool

Thanks anyway.. it was only $15 so no real loss :P

---

### Post by reidy90 on 2007-12-23
Sorry to cross post but the same device is discussed in another thread:
[http://ubuntuforums.org/showthread.php?p=3996289](http://ubuntuforums.org/showthread.php?p=3996289)

I can recommend a Kworld 355U usb tuner that I use in my myth setup which runs on a em28xx chipset which has Linux support via an add on module.

---

### Post by moosylog on 2008-07-06
There is no driver for the dutv005

I've collected all information about the device on:
[http://moosy.blogspot.com/2008/07/ce9500b1.html](http://moosy.blogspot.com/2008/07/ce9500b1.html)

---

