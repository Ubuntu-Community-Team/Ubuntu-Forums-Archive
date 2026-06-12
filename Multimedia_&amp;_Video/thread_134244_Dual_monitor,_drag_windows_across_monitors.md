---
title: "Dual monitor, drag windows across monitors?"
date: 2006-02-21
forum: Multimedia &amp; Video
---

### Post by zazery on 2006-02-21
SOLVED: A friend of mine pointed out that I need to put Option "Xinerama" in the ServerLayout section, it works fine now.


I've got a dual monitor setup and my mouse can go between the 2 monitors just fine. However when I try to move, say a Firefox window over to the other monitor it will wrap around the monitor it's currently on and when I let go it's still in that position but my mouse is in the other monitor. I'm wondering how I could set it up so that I could drag windows between the screens.

Here is my xorg.conf

```
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
	Load	"dbe"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"type1"
	Load	"v4l"
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
	Identifier	"device0"
	VendorName	"ATI"
	BoardName	"ATI Radeon"
	Driver		"ati"
	#Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen 		0
EndSection

Section "Device"
	Identifier	"device1"
	VendorName	"ATI"
	BoardName	"ATI Radeon"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"Hitachi"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"ViewSonic"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Hitachi Screen"
	Device		"device0"
	Monitor		"Hitachi"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"ViewSonic Screen"
	Device		"device1"
	Monitor		"ViewSonic"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Multihead layout"
	Screen	"Hitachi Screen" 0 0
	Screen	"ViewSonic Screen" RightOf "Hitachi Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Edit:
A friend of mine pointed out that I need to put Option "Xinerama" in the ServerLayout section, it works fine now.

---

