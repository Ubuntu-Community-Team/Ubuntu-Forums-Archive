---
title: "Matrox graphics driver install"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by knudsenUK on 2008-03-11
Ubuntu 6.06 LTS LAMP - HP Proliant ML110 G4
I seem to be caught in a frustrating cycle of getting nowhere. I can't seem to get the display resolution to above 640x480. I can't allow local login of root as I can't access any form buttons (not visible).
I have tried to install the matrox graphics driver using  sudo ./install.sh

Get error message "could not find x server driver install path" 
Any advice would be much appreciated.

Regards Rik

---

### Post by NT4usB on 2008-03-11
I have a box in the closet I put a Matrox Millennium card (out of an old HP box) I'll dig it out and see what driver it used. iirc, it had a driver already installed, just had to use it.
Post your xorg.conf.

---

### Post by knudsenUK on 2008-03-11
Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:3:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"800x600@72"	"800x600@75"	"800x600@56"	"800x600@60"	"640x480@75"	"832x624@75"	"640x480@72"	"1024x768@75"	"640x480@60"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"

---

### Post by NT4usB on 2008-03-11
Have you tried?:```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If you can't get to a graphical login, Ctrl+Alt+F1.
Login and run the command. 
Then restart gdm```
sudo /etc/init.d/gdm restart
```

Looks like the driver should be: mga

---

### Post by knudsenUK on 2008-03-12
Thanks I have tried several things and the odd thing is that if I start in recovery mode, the graphics come up fine. But I can't seem to discover where this config info comes from to apply to the regular bootup process. I dont need 3d as this is a server, just the ability to see more than one letter at a time lol! 

In fact if it wasn't for the dbus error and reduced functionality in recovery mode I would be happy with it as is!!

---

### Post by NoPane on 2008-03-13
I've just hit the same problem while installing Debian 4.0. I cured it by changing the driver type to "mga" and setting the colour depth to 16. (That seems to be the important bit). I can't get anything better than 1024x768, but it's enough for what I want to do. Hope this helps.

---

