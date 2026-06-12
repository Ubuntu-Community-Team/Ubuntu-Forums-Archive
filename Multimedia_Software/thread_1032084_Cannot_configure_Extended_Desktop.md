---
title: "Cannot configure Extended Desktop"
date: 2009-01-06
forum: Multimedia Software
---

### Post by Ulysses on 2009-01-06
Hello,

ASUS 2.8 Ghz
2 gb RAM
Volari V3 video card (64mb)
Playing with Ubuntu 8.04

I have been trying for hours to figure this out
Cannot find a driver to make this card work
And I want to have an extended desktop, not a mirorred desktop
Currently, the mirrored desktop is easy. Worked out of the box.
Extended desktop, not so much.

I've tried all the following how-tos (and they are rockin good, by the way)

Xinerama
[http://ubuntuforums.org/showthread.php?p=1773624]("http://ubuntuforums.org/showthread.php?p=1773624")
Twinview
[http://ubuntuforums.org/showthread.php?p=1773584]("http://ubuntuforums.org/showthread.php?p=1773584")
Merged FB
[http://ubuntuforums.org/showthread.php?p=1773710]("http://ubuntuforums.org/showthread.php?p=1773710")
Big Desktop
[http://ubuntuforums.org/showthread.php?p=1773544]("http://ubuntuforums.org/showthread.php?p=1773544")

And the Xinerama is the one that seems that should work for me (I tried them all, just to be sure), but it's the drivers that are killing me.
And the vesa ones, they don't want to work for me.

For those that are interested, I can post the xorg.conf that I have been working with (at the very bottom of the post, so the curious and the skilled can maybe help me out). Maybe I got something wrong there.

Whatever information can be provided to help would be of immense appreciation.

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
	Option		"CorePointer"
EndSection

Section "Device"
	Option "DDCMode" "True"
	Option "MonitorLayout" "primary monitor,secondary monitor" #replace primary monitor with the following:Ati Driver:
	Identifier	"0 Configured Video Device"
	Boardname	"SiS generic"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Screen	0
	Vendorname	"SiS"
EndSection

Section "Device"
	Option "DDCMode" "True"
	Option "MonitorLayout" "primary monitor,secondary monitor" #replace primary monitor with the following:Ati Driver:
	Identifier	"1 Configured Video Device"
	Boardname	"SiS generic"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Screen	1
	Vendorname	"SiS"
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Vendorname	"Hewlett-Packard"
	Modelname	"HP L1740 LCD Flat Panel Monitor"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-76.0
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
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Monitor		"Main Monitor"
	Device		"0 Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1400x1050@75"	"832x624@75"	"1600x1200@65"	"800x600@60"	"1600x1200@60"	"800x600@75"	"1792x1344@60"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection	
EndSection

Section "Monitor"
	# second monitor TTX monitor from the iCute
	Identifier	"Second Monitor"
	Vendor Name	"TTX"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Monitor		"Second Monitor"
	Device		"1 Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
	
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        0   "Main Screen"
    Screen        1   "Second Screen" RightOf "Main Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    Option "Xinerama" "true
EndSection
```

---

