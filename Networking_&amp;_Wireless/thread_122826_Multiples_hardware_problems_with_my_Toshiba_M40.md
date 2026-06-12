---
title: "Multiples hardware problems with my Toshiba M40"
date: 2006-01-28
forum: Networking &amp; Wireless
---

### Post by CalvinK on 2006-01-28
I'm an absolute beginner with Linux but I worked some years ago with Unix. 
I have multiple problems with my laptop Toshiba Satellite M40. The ATI MOBILITY RADEON X600 SE video card isn't recognized (It works with "vesa", thank you). The connection with Internet by ethernet network card is impossible : it's a Yukon from Marvell Technology and a driver for Linux is loadable at their Web site. Unfortunately, I cannot compile the driver because I can't have an access to Internet during my Ubuntu session and my gcc isn't the good one. 
I have tried ndiswrapper to use the Windows drivers for the wifi . It freezes my system and I cannot extract the drivers from the .EXE files of Atheros.
My first contact with Linux isn't very gratifying. :-? 
Thank you for your help
CK

---

### Post by Sn4ke on 2006-01-30
Install ubuntu breezy (5.10) and boot with **acpi=noirq** option for connect without installing external driver

---

### Post by mdmarmer on 2006-01-30
See here [http://www.linux-on-laptops.com/toshiba.html](http://www.linux-on-laptops.com/toshiba.html)
Also here [http://linux.toshiba-dme.co.jp/linux/index.htm](http://linux.toshiba-dme.co.jp/linux/index.htm)

I have Toshiba M45-S331 (same PC but integrated Intel video).  I still boot with acpi=off (too many devices on IRQ 11) -- don't remember if I tried acpi=noirq or not.

Everything is working except internal modem and maybe some of the special Toshiba function keys -- if you use GRUB to boot (probably same in LILO) you'll lose buttons for playing CD/DVD -- if you those use Windows boot loader and modify boot.ini to boot Linux.

Note there are special Toshiba utilities toshutils fnfx etc. some require kernel compile.

Mike

---

### Post by Sn4ke on 2006-01-31
[QUOTE=CalvinK]I'm an absolute beginner with Linux but I worked some years ago with Unix. 
I have multiple problems with my laptop Toshiba Satellite M40. The ATI MOBILITY RADEON X600 SE video card isn't recognized (It works with "vesa", thank you). The connection with Internet by ethernet network card is impossible : it's a Yukon from Marvell Technology and a driver for Linux is loadable at their Web site. Unfortunately, I cannot compile the driver because I can't have an access to Internet during my Ubuntu session and my gcc isn't the good one. 
I have tried ndiswrapper to use the Windows drivers for the wifi . It freezes my system and I cannot extract the drivers from the .EXE files of Atheros.
My first contact with Linux isn't very gratifying. :-? 
Thank you for your help
CK[/QUOTE]
I have a toshiba M40 too (282) with the same eth card but ATI MOBILITY X700

I setup correctly both the ethernet card and ATI 3D (for this one follow [these](http://ubuntuforums.org/showthread.php?p=408111) instructions), but when i installed video card, the connection to internet doesn't work anymore .... i must boot with acpi=off option to reconnect again couse with noirq i don't have my internet connection.

Hoping I helped you (also with my "broken" english  :mrgreen: ), bye :)

---

