---
title: "Second monitor support for Radeon IGP 320M"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by obrie on 2007-03-13
Hello,

I feel bad asking about this since there are so many tutorials/articles out there regarding it, but I've gone through them all and haven't been able to figure out to enable my second monitor on my HP laptop.  I have an HP Pavilion ze4365 laptop with an ATI Radeon IGP 320 M.  My current setup is that I have an LCD monitor plugged into the VGA connection on the back of the laptop in the hopes that I can get dual-monitor setup.

This video card is not supported by fglrx (I have tried using it, but fails with "no screens found").

I have tried going through the tutorial at [http://www.ubuntuforums.org/showthread.php?p=1773710](http://www.ubuntuforums.org/showthread.php?p=1773710), but haven't had any success.  My current xorg.conf is below:

[PHP]
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon IGP 320 M"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"XAANoOffscreenPixmaps" "1"
	Option		"AGPMode" "4"
	Option		"GARTSize" "64"
	Option		"MergedFB" "true"
	Option		"MonitorLayout" "LVDS, CRT" # Same results with LVDS, AUTO
	Option		"EnablePageFlip" "true"
	Option		"ColorTiling" "true"
	Option		"RenderAccel" "on"
	Option		"CRT2Hsync" "31-85"
	Option		"CRT2VRefresh" "56-75"
	Option		"OverlayOnCRTC2" "true"
	Option		"CRT2Position" "RightOf"
	#Option		"MergedNonRectangular" "true"
	Option		"MetaModes" "1024x768-1024x768"
	Option		"MergedXineramaCRT2IsScreen0" "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon IGP 320 M"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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
		#Virtual	2048 1536
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
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option	"Composite" "Disable"
EndSection

Section "ServerFlags"
	Option	"AIGLX" "off"
EndSection
[/PHP]

Currently, the second monitor is simply blank in this configuration.  When I comment out CRT2Hsync and CRT2VRefresh, the second monitor mirrors the display on the laptop.

I've tried following the Xinerama tutorial at [http://www.ubuntuforums.org/showthread.php?p=1773624](http://www.ubuntuforums.org/showthread.php?p=1773624), but the monitor remained blank.

I'm not looking to use Compiz/Beryl or anything special, just to have the desktop extended onto the second monitor (so that I can drag windows between monitors).  I can drag things into what would be the space on the second monitor, but I obviously can't see them since no video is being sent to the monitor.

Is the configuration I'm following the correct method to use for this setup?  If so, does anyone have any recommendations to try?  I appreciate any help.

Thanks.

---

