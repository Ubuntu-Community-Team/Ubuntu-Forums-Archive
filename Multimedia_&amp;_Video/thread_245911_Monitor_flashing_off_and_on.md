---
title: "Monitor flashing off and on"
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by rv8 on 2006-08-28
I've got an Apple G4 Dual 1.42, running Dapper 6.06.  It has an ATI Radeon 9000 Pro (rv250) video card with 64 MB of RAM, driving two monitors.  Screen0 is an Apple 15" LCD with a 1024x768 resolution.  Screen1 is an NEC 70GX2 LCD with a 1280x1024 resolution.

The Apple monitor is working perfectly.  The NEC (screen1) keeps going blank for a second or less.  Sometimes it does this every second or so, other times it will go 20 or 30 seconds before blanking.  I've looked in various logs, but can't find any clues.  I've checked the cable connections.  It works perfectly when I'm booted in OS X, so that tells me it is not a hardware or connection problem.

Here is my xorg.conf, in case someone can see a problem:

```
Section "ServerFlags"
    Option "DefaultServerLayout"  "Multihead"
#   Option "DefaultServerLayout" "Single_monitor"
EndSection

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
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ati0"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"ati1"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"70GX2"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-60
EndSection

Section "Monitor"
	Identifier	"Apple_Studio_15"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"ati1"
	Monitor		"70GX2"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen0"
	Device		"ati0"
	Monitor		"Apple_Studio_15"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Single_monitor"
	Screen		"screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "ServerLayout"
        Identifier "Multihead"
        Screen  "screen0"
        Screen  "screen1" LeftOf "screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	Option "Xinerama" # allows single xserver to drive both displays.
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

```

I've spent hours digging through this forum, and the wiki, but I am stumped.  Any advice would be greatly appreciated.

Thanks,
Kevin

---

### Post by Ziox on 2006-08-28
I would change the horizsync rate and vertrefresh rate...and use this option if your monitors give out DDC information:

 Option "DDCMode" "boolean"

add that to your device section and monitor section (I'm not sure which one, if either, works...)

---

### Post by rv8 on 2006-08-29
Thanks for the suggestions.

The monitor's on-screen display says that is already at the horizontal and vertical refresh rates that work nicely when I am running OS X.  I tried both 60 and 75 Hz - I'll try messing around with the other axis tonight, as I've got to run to work now.

Putting Option "DDCMode" in the monitor section added a bunch of new resolutions to the options in the Screen Resolution panel, but the monitor wasn't any happier with any of the other ones either.

---

### Post by rv8 on 2006-08-29
So far, the only thing that works is to select the resolution on the NEC monitor to something substantially less than 1280x1024, e.g. 800x600.  This at least gives me a second monitor, but it looks like crud, and I've lost a lot of screen real estate.

But, I have other bigger issues to sort out, such as getting both processors working.  I'll put the dual monitor issues on hold for now, and come back later.

---

