---
title: "non matching dual CRT monitor setup problem"
date: 2008-09-29
forum: Multimedia Software
---

### Post by anystupidname on 2008-09-29
Clone mode works fine but any mergedFB, bigdesktop, aticonfig configuration I attempt fails. I've hand crafted about 10 different xorg.conf files without success. I've also attempted to let aticonfig build a couple... I've tried using fglrx both downloaded and compiled from ATI and from the xorg-driver-fglrx as well as the ati (open source) driver and radeonhd driver...

Hardy
ATI Radeon HD 2400 XT
CRT1 ViewSonic P815
CRT2 Dell P991 (Trinitron)

Right now, for instance, (the closest I think I've come lately) is the following xorg.conf which causes a flashing blocky white screen for a short while during 2 attemps followed by a black screen you can't recover from. LiveCD required to get back into the system at that point...

> #   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Device0"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		0
	
EndSection

Section "Device"
	Identifier	"Device1"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	VendorName   "ViewSonic"
	ModelName    "ViewSonic P815"
	HorizSync    30.0 - 115.0
	VertRefresh  50.0 - 160.0
	Gamma        1
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
	ModeLine     "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	ModeLine     "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Vendorname	"Dell"
	Modelname	"Dell P991"
	Horizsync	30.0-107.0
	Vertrefresh	48.0-120.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Device0"
	Monitor		"Monitor0"
	SubSection	"Display"
	Depth		24
	Virtual		3200 1200
	EndSubsection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Device1"
	Monitor		"Monitor1"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	Screen		"Screen1" Rightof "Screen0"
EndSection


I would really appreciate any assistance!

---

### Post by markbuntu on 2008-09-29
When you try to run bigdesktop do you see any errors in Xorg.0.log?
Do you see any errors there at all?

---

### Post by anystupidname on 2008-09-29
I believe "screen not found" was what happened with bigdesktop although I've been through many since. There are 4 different xorg.#.log files as well (some with identical timestamps?!?) making it hard for me to know which one is for the latest xserver session ran.

---

