---
title: "Triple head Xinerama?"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by speek on 2006-10-29
I am currently attempting to get three of my monitors to play nice with each other. One 19 inch wide screen monitor (LCD, main one, in the middle), one 17 inch CRT monitor (on the left), and one 15 inch lcd monitor (on the right).

The middle monitor (19 in) is the sole connection to my ATI radeon 9550 (DVI connection), the other two are both VGA connections in my Nvidia FX 5500.

I looked through many howtos and posts about this kind of stuff... but I just can't seem to get this to work. At the moment, only the right monitor is working as planned, I had it so that the middle and right ones were working at one point... still have that xorg conf but I screwed something up there, it is a lost effort.

I will post my log file and xorg conf to see if someone can tell me what I am overlooking...


> 
Section "Files"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"IMPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"1 ATI"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option "DRI" "true"
        Option "ColorTiling" "on"
        Option "EnablePageFlip" "true"
        Option "AccelMethod" "XAA"
        Option "XAANoOffscreenPixmaps"
        Option "RenderAccel" "true"
        Option "AGPFastWrite" "on"
	Screen 0
	Option "MonitorLayout" "CRT,TMDS,TMDS"
EndSection

Section "Device"
	Identifier	"0 Nvidia"
	Driver		"nvidia"
	BusID		"PCI:02:07:0"
	Screen 1
	Option "MonitorLayout" "CRT,TMDS,TMDS"
EndSection

Section "Device"
	Identifier	"2 Nvidia"
	Driver		"nvidia"
	BusID		"PCI:02:07:0"
	Screen 2
	Option "MonitorLayout" "TMDS,CRT,TMDS"
EndSection

Section "Monitor"
	Identifier "Center"
	#AL1916W
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier "Left"
	#SyncMaster 753DF	
	Option		"DPMS"
	HorizSync 30.0 - 71.0
	VertRefresh 50.0 - 160.0
EndSection

Section "Monitor"
	Identifier "Right"
	#E151FP	
	HorizSync 31.0 - 60.0
	VertRefresh 56.0 - 75.0
	Option		"DPMS"
	
EndSection

Section "Screen"
	Identifier	"Center Screen"
	Device		"1 ATI"
	Monitor		"Center"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1400x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Left Screen"
	Device		"0 Nvidia"
	Monitor		"Left"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Right Screen"
	Device		"2 Nvidia"
	Monitor		"Right"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Multihead Layout"
	#Screen		"Default Screen"	
	Screen		1 "Center Screen"
   	Screen		0 "Left Screen" LeftOf "Center Screen"
	Screen		2 "Right Screen" Rightof "Center Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option "Xinerama" "on"
	#Option "Clone" "on"
EndSection

#Section "ServerFlags"  
#	Option "Xinerama" "true" 
#EndSection

Section "DRI"
	Mode	0666
EndSection





P.S. Sorry bout the tar... it was too big to fit as a normal text...


Be Well,
Marc

---

