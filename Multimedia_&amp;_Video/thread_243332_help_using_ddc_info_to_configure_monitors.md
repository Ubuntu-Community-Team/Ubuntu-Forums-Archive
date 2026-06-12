---
title: "help using ddc info to configure monitors"
date: 2006-08-24
forum: Multimedia &amp; Video
---

### Post by fangorious on 2006-08-24
I'm trying to configure a BigDesktop layout for my HP nw8240 (ati mobility firegl v5000 chipset, fglrx v8.25.18 driver from restricted repo) to use when docked with two HP 1955 LCD monitors attached. One is attached with DVI, the other is attached with VGA. When I start X with the BigDesktop layout, the DVI monitor shows the Screen 1 and the VGA monitor goes blank with an OSD message "Input signal out of range". Using ddcprobe *always* lists just the internal lcd (samsung 1920x1200 analog) regardless of the physical setup. Lookint at the ddc output in Xorg.0.log, when I have the laptop docked/closed and start X, this is what's detected

CRT on primary DAC (the VGA monitor)
LCD on internal LVDS (the internal analog samsung display)
DFP on internal TDMS (the DVI monitor)
Primary Controller - CRT on primary DAC
Primary Controller - LCD on internal LVDS
Secondary Controller - DFP on internal TDMS

The output for the CRT and DFP ('Display{1,2} EDID data' sections) is the same. They have an identical list of supported modes. But at the end of the ddc section, where it is listing actual modelines, there are 11 listed for primary and 29 found for secondary.

I neglected to save the log file before restarting X with a different setup, so I can't post the exact output until tomorrow morning. What I'm hoping to get out of this posting is for someone to tell me what to look for in the ddc section of Xorg.0.log to configure the Screen section of my xorg.conf for the monitor on the analog connection to display something.

Here is my current xorg.conf

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
EndSection

Section "Monitor"
	Identifier	"Samsung LCD"
	Option		"DPMS"
	HorizSync	31.5-91.1
	VertRefresh	60-100
	Modeline	"1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103
	Modeline	"1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946
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

Section "Monitor"
	Identifier	"Viewsonic vx2025wm"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-75
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
	Identifier	"HP 1955"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Work Dock Digital"
	Device		"FireGL 2"
	Monitor		"HP 1955"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Work Dock Analog"
	Device		"FireGL 1"
	Monitor		"HP 1955"
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
	Screen		0 "Work Dock Analog" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

