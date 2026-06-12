---
title: "Dell 2405fwp and 6800GT problems"
date: 2005-11-03
forum: Multimedia &amp; Video
---

### Post by shrike on 2005-11-03
Hello,

I've atempted to follow various pieces of info how to get this monitor recognized by this OS.  I've tried different modelines and every concievable configuration of xorg.conf... My main problem comes from the fact that this panel has a max resolution of 1920x1200@60hz, which is the max that the DVI standard is capable of transmitting.  When I look in the /var/log/xorg.0.log is indicates that all resolutions above 1280x1024 are out of range.:???: 

The following are the contents of the xorg.conf file:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	#Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
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

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
#	Option		"ZAxisMapping"		"4 5"
#EndSection

Section "InputDevice"
        Identifier	"Configured Mouse"
        Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
	Option		"Dev Phys"		"usb-0000:00:1d.1-2/input0"
        Option		"Device"			"/dev/input/event2"
	Option		"Buttons"		"10"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "Monitor"
	Identifier      		"Monitor0"
	VendorName		"Dell"
	ModelName		"2405FWP"
        Option          		"DPMS"
	 Option 			"IgnoreEDID" 	"true"
        DisplaySize     		524 324
        HorizSync       		30-81
        VertRefresh     		56-76
       UseModes			"Modes[0]"
EndSection

Section "Modes"
	Identifier     "Modes[0]"
	ModeLine      "1920x1200" 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +Hsync -Vsync
	Modeline      "1600x1200" 160.96 1600 1704 1880 2160 1200 1201 1204 1242 +Hsync -Vsync
	Modeline      "1280x1024" 138.54 1280 1368 1504 1728 1024 1025 1028 1069 +Hsync -Vsync
EndSection

Section "Device"
	Identifier		"Card0"
	Driver			"nv"
	VendorName	"NVIDIA Corporation"
	BoardName		"NV40 [GeForce 6800 GT]"
	Option          		"ConnectedMonitor"      		"DFP"
        Option          		"IgnoreDisplayDevices" 		"CRT,TV"
        Option          		"ExactModeTimingsDVI"  	 	"True"  #Force use of ModeLine
        Option         		"UseEdidFreqs"          			"False" #Override Monitor section
        Option        		"IgnoreEDID"           			"True"  #Don't probe monitor
        Option         		"NoBandWidthTest"       		"True"  #Don't test memory speed
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Card0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

:confused:

---

### Post by shrike on 2005-11-03
Ok solved my own problem found someone with a different videocard that had a different modeline that worked plus I was a dope and put "nv" in instead of "nvidia" for the driver under the Device section.

BTW it took a lot more then just google to figure this one out...:D 

here is the working version.

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	#Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
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
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
	Option		"Dev Phys"		"usb-0000:00:1d.1-2/input0"
        Option		"Device"			"/dev/input/event2"
	Option		"Buttons"		"10"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "Monitor"
	DisplaySize 520 330
	HorizSync 30-81
	VertRefresh 56-76
	Identifier "Monitor[0]"
	ModelName "DELL 2405FPW"
	Option "DPMS"
	VendorName "DEL"
	Modeline "1920x1200_60.00" 154 1920 1968 2000 2080 1200 1203 1209 1235 +HSync -VSync
	Modeline "1680x1050_60.00" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -HSync +Vsync
EndSection


Section "Device"
	BoardName "GeForce 6800 GT"
	BusID "1:0:0"
	Driver "nvidia"
	Identifier "Device[0]"
	Option "XaaNoPixmapCache" "on"
	Option "XaaNoOffScreenPixmaps" "on"
	VendorName "NVidia"
EndSection


Section "Screen"
	DefaultDepth 24
	SubSection "Display"
		Viewport 0 0
		Depth 24
		Modes "1920x1200_60.00" "1680x1050_60.00"
	EndSubSection
	Device "Device[0]"
	Identifier "Screen[0]"
	Monitor "Monitor[0]"
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen[0]"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

---

### Post by xturmn8r on 2005-11-06
I'm tryin to get mine to work, but just a heads up: it's a 2405fpw, not fwp. ;)

** edit... it's alive!   here's my xorg.conf (it's essentially the same, just a different bus)

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option		"NoLogo"
	Option "XaaNoPixmapCache" "on"
	Option "XaaNoOffScreenPixmaps" "on"
EndSection

Section "Monitor"
	DisplaySize 520 330
	HorizSync 30-81
	VertRefresh 56-76
	Identifier "Monitor[0]"
	ModelName "DELL 2405FPW"
	Option "DPMS"
	VendorName "DEL"
	Modeline "1920x1200_60.00" 154 1920 1968 2000 2080 1200 1203 	1209 1235 +HSync -VSync
	Modeline "1680x1050_60.00" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -HSync +Vsync
EndSection

Section "Screen"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth 24
		Modes "1920x1200_60.00" "1680x1050_60.00"
	EndSubSection
	Device "Device[0]"
	Identifier "Screen[0]"
	Monitor "Monitor[0]"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen[0]"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


***
where I was having problems was I had the nvidia named something else (under device, it was Nvidia NV40 or something similar, and when I you referenced device[0] it didn't like it...)   Anyway, THANKS!

---

