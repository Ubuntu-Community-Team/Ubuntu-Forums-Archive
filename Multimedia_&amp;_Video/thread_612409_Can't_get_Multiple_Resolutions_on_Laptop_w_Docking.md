---
title: "Can't get Multiple Resolutions on Laptop w/ Docking Station (ATI)"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by EamonR on 2007-11-13
Hi, I'm using a HP Compaq 6715b Laptop running Ubuntu 7.10 Gutsy,

I have the HP Advanced Docking Station and a HP L2045w 20" Widescreen LCD connected to it (among other things but they're not the problem)

The laptop is 15.4" widescreen

First, minor problem - The LCD only displays if I have the laptop in the docking station before I power up, otherwise if I plug it in while running, I have to reboot (though the LCD does power up when I hit reboot to show me the ubuntu unloading screen haha).
As I said, not a huge problem since I can just reboot to power it up but if someone knows a fix that'd be cool!

Now - my main problem:
I'm trying to get the LCD to display at 1680x1050 resolution since that is its native recommended resolution and fonts are displaying oddly on a lower one, and trying to keep the laptop at its lower one if possible.

I've set it up under Administration --> Screens & Graphics and rebooted and theres been no difference, both screens still run under the same resolution.

Initially I just set the laptop to 1680x1050 till recently but desktop effects run a little slowly at such high resolution so I lowered it. However I'll take readability of fonts over animation speed when I'm at my desk :)

Hope someone can help, this font thing is rather annoying...

Alternatively I'd be happy with just a way to have the resolution of both change to the higher one when the docking station is connected...that would work too.

This is my xorg.conf: (The last couple lines are a fix I read to stop my screen going blank after 20mins of no mouse/keyboard activity while watching movies).

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ie"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Radeon Xpress 1270"
	Boardname	"ati"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
	Screen	0
	Option		"DesktopSetup"	"c"
	Option		"ForceMonitors"	"crt1,crt2"
	Option		"HSync2"	"31.5-65.5"
	Option		"VRefresh2"	"56.0 - 65.0"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"Laptop HP6715b"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon Xpress 1270"
	Monitor		"Laptop HP6715b"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes		"1280x720@60"	"1280x800@60"	"1280x768@60"	"1440x900@60"	"800x600@60"	"1600x1024@60"	"800x600@56"	"1680x1050@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection
Section "device" #      
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
	Screen	1
	Option		"DesktopSetup"	"c"
	Option		"ForceMonitors"	"crt1,crt2"
	Option		"HSync2"	"31.5-65.5"
	Option		"VRefresh2"	"56.0 - 65.0"
EndSection
Section "screen" #      
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" #      
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "ServerFlags"
	Option		"blank time"	"0"
	Option		"standby time"	"0"
	Option		"suspend time"	"0"
	Option		"off time"	"0"
EndSection
```

---

