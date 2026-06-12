---
title: "dual screen, 2 nvidia gfx cards, reinstall drivers after reboot"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by skela on 2007-12-29
i am running ubuntu on a 64 bit computer with 2 graphics cards.
One Nvidia GeForce4 440MX card connected to an LCD.
One Nvidia GeForce 8500GT card connected to my flat screen TV.

The only way I got things working the way I wanted (720p on the TV) was by using the nvidia drivers from nvidia.com.

The problem with my setup is, after every reboot, only the LCD display works.
There's nothing but a blank screen on the TV.
I've managed to get the TV working by rerunning the install file from nvidia.com.
This is obviously frustrating enough, having to do this after every reboot.
Does anyone know how to avoid having to reinstall things after every reboot?

Here's my xorg.conf file:
```

Section "ServerLayout"
	Identifier	"X.org Configured"
  screen 0 "Screen0" 0 0
  screen 1 "Screen1" rightof "Screen0"
	Inputdevice	"Mouse0"	"CorePointer"
	Inputdevice	"Keyboard0"	"CoreKeyboard"
EndSection

Section "Files"
	Rgbpath		"/etc/X11/rgb"
	Modulepath	"/usr/lib/xorg/modules"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/X11R6/lib/X11/fonts/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/X11R6/lib/X11/fonts/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"xtrap"
	Load		"record"
	Load		"glx"
	Load		"dbe"
	Load		"extmod"
	Load		"type1"
EndSection

Section "InputDevice"
	Identifier	"Keyboard0"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
EndSection

Section "InputDevice"
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"Protocol"	"auto"
	Option		"Device"	"/dev/psaux"
	Option		"Emulate3Buttons"	"no"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Vendorname	"Sony"
	Modelname	"SonyTV(DFP0)"
	Horizsync	28.0-65.0
	Vertrefresh	59.0-61.0
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "720p" 73.825 1280 1320 1368 1640 720 722 724 751 +hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1080@60" 148.4 1920 2008 2052 2200 1080 1084 1094 1125 +hsync +vsync interlace
	Gamma	1.0
EndSection


Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Philips"
	Modelname	"Philips 150C5 (15inch)"
	Horizsync	30.0-63.0
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
	Gamma	1.0
EndSection


Section "Device"
	Identifier	"Card1"
	Driver		"nvidia"
	Vendorname	"nVidia Corporation"
	Boardname	"GeForce 8500GT"
	Busid		"PCI:1:0:0"
	Option		"UseEDID"	"True"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"Card0"
	Driver		"nv"
	Vendorname	"nVidia Corporation"
	Boardname	"NV17 [GeForce4 MX 440]"
	Busid		"PCI:5:8:0"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Card0"
	Monitor		"Monitor0"
	SubSection "Display"
		Viewport	0	0
		Depth	24
		#Modes "800x600@56" "800x600@72" "640x480@75" "800x600@75" "640x480@72" "800x600@60" "640x480@60" "832x624@75" "1024x768@75"  "1024x768@70" "1024x768@60"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Card1"
	Monitor		"Monitor1"
	SubSection "Display"
		Viewport	0	0
		Depth	24
		Modes		"720p"	"1920x1080@60"
		#Modes "1280x768@60" "1280x720@60" "720p" "800x600@60" "1280x800@60" "1440x900@60" "1600x1024@60" "1680x1050@60" "1920x1080@60"
	EndSubSection
EndSection


```

---

