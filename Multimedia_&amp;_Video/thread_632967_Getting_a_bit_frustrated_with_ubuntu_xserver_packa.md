---
title: "Getting a bit frustrated with ubuntu xserver packages"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by toupeiro on 2007-12-06
ok..  this is the third time in a row I've downloaded some form of an xserver update through update manager, rebooted my computer and had no bloody video.  I am not using any third party repo's.  I'm getting pretty tired of having to hack xorg every time I get an xserver update released.  A Geforce 7950 and a Samsung flat panel are not what I would consider uncommon components.  Can we please get a little better QA?

If I were running into these things in my company, I would be livid about now.

---

### Post by Saint Angeles on 2007-12-06
if you can startup in recovery mode, you can sudo vim /etc/usplash.conf and set your correct resolution.

that worked for my samsung monitor

---

### Post by toupeiro on 2007-12-06
I wish it were something that simple.  

Unfortunately, the problem has graduated from annoying to ridiculous.

I've done everything from re-installing the driver to restoring 5 known good copies of my xorg file from backups.  Still not seeing my hardware correctly.  I'd consider bad hardware except -- I've only ever experienced this problem with gutsy, and only when an update to xserver-xorg or X11 in general is released.

needless to say, this sucks!

---

### Post by daengbo on 2007-12-06
can you post your xorg.conf?

---

### Post by eye208 on 2007-12-06
> **toupeiro said:**
> A Geforce 7950 and a Samsung flat panel are not what I would consider uncommon components.  Can we please get a little better QA?
I have a Geforce 7900 and never experienced this kind of problem. If this is an issue with the Nvidia driver, there is nothing Ubuntu developers can do about it.

---

### Post by toupeiro on 2007-12-06
This is the xorg.conf which has been working since the end of October -- the last time I had this problem.  There have been no modifications to this file, nor have i installed any new video driver versions.  I have tried reinstalling the 100.14.19 driver, but it has not made any difference.  

> # xorg.conf (xorg X Window System server configuration file)

Section "Files"
EndSection

Section "Module"
	Load		"dbe"
	Load		"dri"
	Load		"glx"
	Load		"vbe"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Buttons"	"9"	
	Option "ButtonMapping" "1 2 3 6 7"
	Option		"Emulate3Buttons"	"false"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
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
		Modes		"1600x1200@65"	"1600x1200@60"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"	"640x480@72"	"640x480@75"	"800x600@56"	"800x600@72"	"800x600@75"	"800x600@60"	"832x624@75"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204B (Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
Option "DPMS"
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
modeline "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
modeline "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
modeline "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
modeline "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
modeline "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
modeline "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
# modeline "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
modeline "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
gamma 1.0

#  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
#  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
#  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
#  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
#  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
#  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
#  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
#  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
#  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
#  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
#  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
#  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
#  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
#  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
#  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
#  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
#  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
#  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
#  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
#	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by toupeiro on 2007-12-06
Well, I guess this thread is closable.  I did everything I could possibly think of.  removed/reinstalled restricted driver, used open driver, downloaded proprietary driver off nvidia's site, reinstalled xorg, redid xorg.conf more times than I can honestly remember.  The system simply would not boot into anything but low-res failsafe mode..

This system started out an ubuntu 6.10 install, upgraded to 7.04 beta, to 7.04 final to 7.10 beta to 7.10 final.  I was planning on rebuilding it when 8.04 was released and making it a 64-bit install.  I guess that rebuild just got expedited and became a 7.10 64 bit

Happy to report that the SAME xorg file I was using previously is working perfectly.  Whatever was in the last set of updates killed my video hard.

---

