---
title: "Multiple ServerLayout sections in xorg.conf"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by fangorious on 2006-08-23
I have an HP nw8240 laptop, with a 1920x1200 widescreen display. I'm trying to setup multiple ServerLayout sections corresponding to my three usage scenarios: using the laptop standalone with the builtin display; my home docking station with a Viewsonic vw2025wm flat panel; and my work docking station with two HP 1905 flat panels (everyone's favorite BigDesktop config). I have the first two configured and working. From a a command line I can 'startx -- -layout HomeDock" and X will load with the home docking station config. Just booting normally into gdm and logging in, I get the DefaultLayout for the standalone config with the builtin display. I'll work on perfecting the BigDesktop config later. For now what I'm curious about is a way to select the HomeDock layout from gdm, or something at boot time before gdm starts (a grub kernel option or init script?). Here's my xorg.conf

> 
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"4 5"
	Option		"ButtonMapping"		"1 2 3 6 7"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc.Mobility FireGL v5000"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"FireGL 1"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"DesktopSetup"	"horizontal"
	Screen		0
EndSection

Section "Device"
	Identifier	"FireGL 2"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Samsung LCD"
	Option		"DPMS"
	HorizSync	31.5-91.1
	VertRefresh	60-100
	Modeline	"1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103
	Modeline	"1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946
EndSection

Section "Monitor"
	Identifier	"Viewsonic vx2025wm"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-75
EndSection

Section "Monitor"
	Identifier	"HP 1905"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	50-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc.Mobility FireGL v5000"
	Monitor		"Samsung LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1680x1050@60" "1600x1200" "1440x900@60" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Home Dock"
	Device		"ATI Technologies, Inc.Mobility FireGL v5000"
	Monitor		"Viewsonic vx2025wm"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1280x1024" 
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Work Dock Digital"
	Device		"FireGL 1"
	Monitor		"HP 1905"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Work Dock Analog"
	Device		"FireGL 2"
	Monitor		"HP 1905"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier	"HomeDock"
	Screen		"Home Dock"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier	"WorkDock"
	Screen		0 "Work Dock Digital" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

