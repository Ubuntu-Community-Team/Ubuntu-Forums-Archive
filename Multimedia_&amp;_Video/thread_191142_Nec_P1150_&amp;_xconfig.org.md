---
title: "Nec P1150 &amp; xconfig.org"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by pcolamar on 2006-06-07
Hi,
 I am useless trying to get the 1280x1024@85 out of my old 21" NEC P1150 but the Screen Resolution panel does not show it . Actually the monitor has planty more modes:
------------
Horizontal: 31 kHz to 94 kHz
Vertical: 55 Hz to 160 Hz
Bandwidth: 202 MHz
Resolutions Supported:
640 x 480: 55 to 160 Hz
800 x 600: 55 to 149 Hz
832 x 624: 55 to 141 Hz
1024 X 768: 55 to 117 Hz
1152 x 870: 55 to 103 Hz
1280 x 1024: 55 to 88 Hz
1600 x 1200: 55 to 75 Hz
--------------
The video card is a Matrox G100 4MB that should be able to support it.
( I was not able to find the complete spec's though)

What should I do ?

Thanks 
-Palmer

Hereby my xconfig.org dump
------------------xconfig.org -------------
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
	Identifier	"Matrox Graphics, Inc. MGA G100 [Productiva] AGP"
	Driver		"mga"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"NEC P1150"
	Option		"DPMS"
	HorizSync 31-94
	VertRefresh 55-88
	
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Matrox Graphics, Inc. MGA G100 [Productiva] AGP"
	Monitor		"NEC P1150"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

