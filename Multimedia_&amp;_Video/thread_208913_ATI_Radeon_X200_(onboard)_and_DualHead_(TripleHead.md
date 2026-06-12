---
title: "ATI Radeon X200 (onboard) and DualHead (TripleHead)"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by D0minik on 2006-07-04
Hi!

I'm trying to get Dual-Head working for hours now and I really don't know what I can do anymore:

I have one ATi X200 on my mainboard (64Bit AMD system), with DVI and VGA out and also an old PCI Matrox Millenium or so (VGA out, of course). And I have also 3 flatpanels which I want to use in Xinerama mode. I cannot use the fglrx drivers, because they freeze my Computer every time I quit X, so I cannot shutdown or anything else, it just freezes. But thats no problem, I dont need 3D support, so I can use the "ati" drivers.

Now my problem: I cannot get the two monitors connected to the onboard graphic display _different_ things, they are always in CLONE MODE! I can change whatever I want in the xorg.conf, they do *always* display the same. Dual-Head with the Matrox PCI card works, but the other 2 big screens display the same. I also tried aticonfig of course, doesn't work. 2 screens, same picture :(

I really don't know what to do :/ pls help!

This config "works", but as I said, in "Clone Mode". I also can uncomment the commented lines, nothing happens (after X restart ;-)). I removed the Matrox stuff, for the first step I only want to get dualhead with the X200 working:

> Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
#	Load	"extmod"
	Load	"freetype"
#	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"

	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
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

Section "Device"
	Identifier	"ati-onboard-1"
	Driver		"ati"
	BusID		"PCI:1:5:0"
#	Option		"DesktopSetup"   "0x00000000"    #dual head
#	Option		"CloneMode" "false"
	Screen		0
EndSection
	
Section "Device"
	Identifier	"ati-onboard-2"
	Driver		"ati"
	BusID		"PCI:1:5:1"
#	Option		"DesktopSetup"   "0x00000000"    #dual head
#	Option		"CloneMode" "false"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"tft19-1"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"tft19-2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"ati-onboard-1"
	Monitor		"tft19-1"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen2"
	Device		"ati-onboard-2"
	Monitor		"tft19-2"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"dreikopf"

	Screen		"screen1" 0 0
	Screen		"screen2" RightOf "screen1"

	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

         Option  "Xinerama" "true"
         Option  "Clone" "false"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection


---

