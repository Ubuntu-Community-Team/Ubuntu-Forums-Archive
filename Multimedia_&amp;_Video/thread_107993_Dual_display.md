---
title: "Dual display"
date: 2005-12-24
forum: Multimedia &amp; Video
---

### Post by melfaro on 2005-12-24
Hi,

I am trying to connect my Dell 9300 laptop to my plasma screen so I can view movies on the plasma. My video card is NVIDIA 6800. I would like some help in setting up the xorg.conf file:

Here's my xorg.conf file:

[I][SIZE="3"]Section "Files"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV41 [GeForce Go 6800]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option          "RenderAccel" "1"
        Option          "NoLogo" "1"
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
        ModelName       "Dell Inspiron WUXGA 1920x1200 Flat Panel"
	Option		"DPMS"
        Option          "CalcAlgorithm" "CheckDesktopGeometry"
	HorizSync	30-95
	VertRefresh	43-60
        DisplaySize     506 316
EndSection

Section "Modes"
        Identifier      "Modes[0]"
        Modeline        "1024x768" 61.89 1024 1080 1184 1344 768 769 772 794
        Modeline        "1920x1200" 186.57 1920 2048 2256 2592 1200 1201 1204 1241
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"NVIDIA Corporation NV41 [GeForce Go 6800]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
        SubSection "Display"
                Depth 15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen[0]"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
[/SIZE][/I]

Thanks.

---

