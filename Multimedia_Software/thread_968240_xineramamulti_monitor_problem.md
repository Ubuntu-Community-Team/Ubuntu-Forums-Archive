---
title: "xinerama/multi monitor problem"
date: 2008-11-02
forum: Multimedia Software
---

### Post by roflmaomayo on 2008-11-02
I have 2 video cards- one AGP nvidia which works fine, and am ATI radeon 7500 PCI card.

I have one flat panel display connected to the nvidia, and two flat panels connected to the ati- one with a vga connection, and one with a flat-panel connnection- the card is dual-headed or whatever.

I can't setup the xorg file to work with all 3 monitors- at the moment I don't care if the two ATI cards display the same thing- as long as I have 2 monitors to work on, it will be a start.

I have re-written the xorg.conf file so many times it ain't funny anymore.

So, right now, here is the latest that I have, where only the nvidia display works at full 1440x900 resolution-

ANY help will be greatly appreciated.
Thank you.
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
	Identifier	"nvidia_dev"
	Driver		"nvidia"
	BusID		"PCI:01:00:0"
	Screen 0
#	Option "MonitorLayout" "TMDS, TMDS"
EndSection
Section "Device"
	Identifier	"ati_dev"
	Driver		"ati"
	BusID		"PCI:02:04:0"
	Screen 1
#	Option "MonitorLayout" "TMDS, TMDS"
EndSection

Section "Monitor"
	Identifier	"0_mon"
EndSection
Section "Monitor"
	Identifier	"1_mon"
EndSection

Section "Screen"
	Identifier	"0_screen"
	Monitor		"0_mon"
	Device		"0_dev"
	Defaultdepth	24
EndSection
Section "Screen"
	Identifier	"1_screen"
	Monitor		"1_mon"
	Device		"1_dev"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"dual"
	screen	0	"0_screen"
	screen	1	"1_screen" RightOf "0_screen"
	Option "xinerama" "true"
EndSection

Section "Module"
	Load		"glx"
EndSection


By the way, I have already tried using the main xinerama setup walkthru ([http://www.ubuntuforums.org/showthread.php?p=1773624](http://www.ubuntuforums.org/showthread.php?p=1773624))

thanks

---

### Post by roflmaomayo on 2008-11-02
Alright, I have all 3 monitors working individually. If I enable xinerama, it will only let me use one card.

heres the current xorg.conf file...
```


# ********************LAYOUT**********************************************


Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
  screen 1 "screen2" leftof "screen1"
  screen 2 "screen3" rightof "screen1"
#	Option "Xinerama" "True"
EndSection
# ********************DEVICE***************************************
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection
Section "device" #  
	Identifier	"device2"
	Boardname	"ATI Radeon"
	Busid		"PCI:2:4:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
# ********************LAYOUT**********************************************


Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
  screen 1 "screen2" leftof "screen1"
  screen 2 "screen3" rightof "screen1"
#	Option "Xinerama" "True"
EndSection
# ********************DEVICE***************************************
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection
Section "device" #  
	Identifier	"device2"
	Boardname	"ATI Radeon"
	Busid		"PCI:2:4:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "device" #  
	Identifier	"device3"
	Boardname	"1 ATI Radeon"
	Busid		"PCI:2:4:0"
	Driver		"ati"
	Screen	1
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

# *********************SCREEN*****************************************
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
	Defaultdepth	24
EndSection
Section "screen"
	Identifier	"screen3"
	Device		"device3"
	Defaultdepth	24
	Monitor		"monitor3"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1440x900@75"	"1440x900@60"	"1280x800@60"	"1600x1024@60"	"1280x768@75"	"1680x1050@60"	"1280x800@75"	"1920x1200@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"720x400@85"	"640x350@85"	"640x400@85"
	EndSubSection
EndSection
Section "screen" #  
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	SubSection "Display"
		Depth	24
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
# *************************MONITOR***************************
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Gateway"
	Modelname	"Gateway FPD1700 R1"
	Horizsync	31.0-80.0
	Vertrefresh	56.0-85.0
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
Section "monitor" #  
	Identifier	"monitor2"
	Vendorname	"Gateway"
	Modelname	"Gateway FPD1700 R1"
	Horizsync	31.0-80.0
	Vertrefresh	56.0-85.0
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
Section "monitor" #  
	Identifier	"monitor3"
	Vendorname	"Gateway"
	Modelname	"Gateway FPD1700 R1"
	Horizsync	31.0-80.0
	Vertrefresh	56.0-85.0
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
# **************************************FLAGS
Section "ServerFlags"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
	Load		"xgl"
EndSection
# ***********************STAtic
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
EndSection
Section "device" #  
	Identifier	"device3"
	Boardname	"1 ATI Radeon"
	Busid		"PCI:2:4:0"
	Driver		"ati"
	Screen	1
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

# *********************SCREEN*****************************************
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
	Defaultdepth	24
EndSection
Section "screen"
	Identifier	"screen3"
	Device		"device3"
	Defaultdepth	24
	Monitor		"monitor3"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1440x900@75"	"1440x900@60"	"1280x800@60"	"1600x1024@60"	"1280x768@75"	"1680x1050@60"	"1280x800@75"	"1920x1200@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"720x400@85"	"640x350@85"	"640x400@85"
	EndSubSection
EndSection
Section "screen" #  
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	SubSection "Display"
		Depth	24
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
# *************************MONITOR***************************
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Gateway"
	Modelname	"Gateway FPD1700 R1"
	Horizsync	31.0-80.0
	Vertrefresh	56.0-85.0
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
Section "monitor" #  
	Identifier	"monitor2"
	Vendorname	"Gateway"
	Modelname	"Gateway FPD1700 R1"
	Horizsync	31.0-80.0
	Vertrefresh	56.0-85.0
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
Section "monitor" #  
	Identifier	"monitor3"
	Vendorname	"Gateway"
	Modelname	"Gateway FPD1700 R1"
	Horizsync	31.0-80.0
	Vertrefresh	56.0-85.0
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
# **************************************FLAGS
Section "ServerFlags"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
	Load		"xgl"
EndSection
# ***********************STAtic
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

```

---

