---
title: "Oversized Desktops"
date: 2008-07-19
forum: Multimedia Software
---

### Post by inibo on 2008-07-19
I will avoid the rant about Grub wiping out my XP partition and taking over 8 hours to do what Windows does in about 30 seconds because I'm so jazzed about actually getting Xinerama to *almost* work.

My problem is I now have two slightly oversized desktops.

What I mean is both displays extend past the edge of the monitors and they do the [virtual desktop thing]("http://en.wikipedia.org/wiki/Virtual_desktop#Scrolling_desktops") where moving the mouse to the edge causes slight scrolling.  Otherwise, everything is fine.

Any suggestions?

Distro:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
```

Adapters:
```
00:08.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)
```

xorg.conf:
```
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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800X600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
  screen 1 "screen2" rightof "screen1"
	Option		"Xinerama"	"true"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:0:8:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1600x1200@65"	"1024x768@85"	"1600x1200@60"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 711N/712N"
	Horizsync	30-81
	Vertrefresh	56-85
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
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
Section "device" #  
	Identifier	"device2"
	Boardname	"OpenChrome"
	Busid		"PCI:1:0:0"
	Driver		"openchrome"
	Screen	0
EndSection
Section "screen" #  
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1600x1200@65"	"1024x768@85"	"1600x1200@60"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor2"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 711N/712N"
	Horizsync	30-81
	Vertrefresh	56-85
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
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
Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection
Section "device" # 
	Identifier	"device3"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:0:8:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" # 
	Identifier	"screen3"
	Device		"device3"
	Defaultdepth	24
	Monitor		"monitor3"
EndSection
Section "monitor" # 
	Identifier	"monitor3"
	Gamma	1.0
EndSection
```

---

### Post by lukjad on 2008-07-20
Here are a few things that may work for you:
[INDENT]1) Sometimes the screen itself is at fault. There are usually buttons that lead to the horizontal and vertical sizes. Try manipulating them so that your screen doesn't overlap. After that play around with step 2 to make it look better.

2) Go to System->Preferences->Screen Resolution and try changing it from there. Sometime you need to do both steps 1 and 2 to make the screen look good. I hope this works for you.

3) There used to be a way to add a screen resolution to the xorg.conf file but I seem to have either forgotten how or they have changed where the screen resolutions are put. (If someone out there knows how, please post.)
[/INDENT]

I hope these things work for you.

---

### Post by inibo on 2008-07-20
I removed all the modeline entries.  I'm kind of a stickler about about wanting to understand everything in a conf file if at all possible and since I'm not an X guru by any stretch of the imagination I wasn't really sure *exactly* what modeline entries do.  Following my instincts I removed them all and just put
```
SubSection "Display"
   Depth	24
   Modes	"1280x1024"
EndSubSection
```
in each Screen section--**after backing up my xorg.conf** (always do that, you'll thank yourself in the morning).  Lo and behold, that did the trick.  I now have a happy Heron. :)

My guess is the modeline settings were enabling resolutions that my monitor could not support without scrolling, but what do I know other than this morning life is good?

That and this is one of the biggest obstacles I've had to taking the plunge.  I am not a linux newbie by a long shot.  I built my first slackware box 13 years ago, but I'm long since past the age where I enjoy spending an entire weekend doing stuff like this.  The only reason I did was because I tried to update my existing older version, 5.something, to 8.04.1 and grub did a serious number on my XP partition.  If I didn't keep everything except my OS on separate drives I would be in a killing mood right now.  Once I get WINE or some other such emulator/VM thingy going I'll be in ecstasy.  Sometimes life has a way of forcing you to do the things you should, even if you don't want to.

---

### Post by scragar on 2008-07-20
If using the mouse causes the screen to scroll are you sure you don't have the screen magnification thing running, can't remember what it's called, but I remember my young brother accidentaly enabled it once(on gutsy I think), I created a new use and copied all the settings over as opossed to finding an actual solution to the problem though, I couldn't find good enough docs, and the visible portion of the screen was about 300px squared, nothing of any use(good job I enabled the root acount before I gave the PC to him, or that may have been harder than I wanted).

If you post the output of:
```
ps -a
```
back here I may be able to find the offending process, then you can just kill it.

---

### Post by inibo on 2008-07-20
Well, as I said, I fixed it by removing the modeline entries for my monitors.  What lead me to that was turning off xinerama so that I got to separate servers, one for each monitor, and then tried to set the screen resolution via System/Preference (apparently that ap does not work with xinerama enabled).  The second monitor showed "1400x1050" which it does not support and the only place "1400x1050" existed was in the modeline entries I'm assuming the display adapters were going for the higher res.  When I removed all of the modeline entries and renabled xinerama everything came up fine.

For what it is worth, here is my current config in case anyone else is trying to do xinerama with two unlike adapters:
```
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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"1280X1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
  screen 1 "screen2" rightof "screen1"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:0:8:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 711N/712N"
	Horizsync	30-81
	Vertrefresh	56-85
	Gamma	1.0
EndSection

Section "device" #  
	Identifier	"device2"
	Boardname	"OpenChrome"
	Busid		"PCI:1:0:0"
	Driver		"openchrome"
	Screen	0
EndSection
Section "screen" #  
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "monitor" #  
	Identifier	"monitor2"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 711N/712N"
	Horizsync	30-81
	Vertrefresh	56-85
	Gamma	1.0
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"1"
EndSection

Section "device" # 
	Identifier	"device3"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:0:8:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" # 
	Identifier	"screen3"
	Device		"device3"
	Defaultdepth	24
	Monitor		"monitor3"
EndSection
Section "monitor" # 
	Identifier	"monitor3"
	Gamma	1.0
EndSection
```

Now that it is working it appears pretty obvious, but until this process becomes *way* easier linux will continue to be too esoteric for Joe User.  Someone someday is going to come up with something as easy as the right click on a windows box to invoke display configuration.  Until then people are not going to be flocking to linux.  All told it took me almost 12 hours and a lot of grief to do something that is trivial with XP and I've been doing this stuff for almost 25 years.  It sucks, but that's the way it is.

---

### Post by muuramenian on 2008-10-07
Had the same problem, fixed it the same way. Thanks!

---

