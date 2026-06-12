---
title: "Changes to xorg.conf only stick for one restart"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by panfist on 2008-01-07
Hey, I've been having a boatload of trouble getting ubuntu to display in my LCD TV's native resolution of 1366x768. After working on it for about two hours, and there is no possible way I could tell you what steps I did that finally let this work, I added two lines to my xorg.conf and then the resolution of 1368x768 suddenly became available for me to select in the "screen and graphics" administration window.

This is the xorg.conf I started with and to which I keep being reverted

> Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 420]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"FLX-3202"
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
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 420]"
	Monitor		"FLX-3202"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1280x960@75"	"1400x1050@60"	"1280x1024@60"	"1600x1200@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

I added this line to the monitor section

  Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync

and this item to the display section, in Modes "1366x768@60"

When I restarted X the resolution of 1368x768 became available and my monitor looks great. I restarted again for another reason and my xorg.conf was back to what I started. I've repeated this like 3-4 times using both 1366 and 1368 and I always get 1368x768 available once, then it reverts.

Please help.

---

### Post by wolfen69 on 2008-01-07
did you try sudo dpkg-reconfigure xserver-xorg in the terminal?

---

### Post by panfist on 2008-01-07
The procedure for me to get the video to display at the correct resolution is to do that terminal command, enable proprietary drivers, then add the two items i mentioned to my fresh xorg.conf. When I restart, the xorg.conf goes back to the way it was in between enabling proprietary drivers and adding the two elements to the xorg.conf.

So to answer your question, yes I have done that several times but then I need to manually adjust a few things and it's those manual adjustments which don't stick beyond one restart.

ps the wolfen will come for you. with his laser.

---

### Post by panfist on 2008-01-08
Anybody?

---

### Post by panfist on 2008-01-11
Hello?

---

