---
title: "Improving NVIDIA FX5200 performance"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by martin_legion on 2007-04-08
Hello everyone 
I have my Nvidia card configured and working fine with acceleration and all, but sometimes I see the performance is not optimal, for example, while watching some avi's, or playing some 3d games, like postal 2 for linux.

There's a **little** difference if I watch the movies in 800x600 instead of 1024x768, but it's anoying and I don't think it should be necesary to it, having 128M of video...

I think that maybe I can tweak a little my xorg.conf by removing stuff that I don't need, of by adding some options, but the thing is I ignore most of the things in the file. For example, I've read somewere that when using the nvidia driver I should disable the option 

> Load	"dri"

on the Module section, but I'm not sure why. 
I commented out that line, but didn't notice any significant difference.

Can anyone give mo some tips about this?
Here's my xorg.conf

**THANKS!**

> Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Driver		"nvidia"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Option		"TVStandard" "PAL-NC"
	Option		"TVOutFormat" "SVIDEO"
	Option		"RenderAccel" "True"
	Option		"ConnectedMonitor" "CRT,TV"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Noc"
	HorizSync 	30-65
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Noc"
	DefaultDepth	24
	Option 		"AddARGBGLXVisuals" "True"
	Option		"TwinView" "on"
	Option		"TwinViewOrientation" "Clone"
	Option		"MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480"
	Option		"SecondMonitorHorizSync" "30 - 96.0"
	Option		"SeconfMonitorVertRefresh" "50 - 120"
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Screen0" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

