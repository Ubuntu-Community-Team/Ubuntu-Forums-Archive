---
title: "XFCE freezes?"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by krtek on 2006-08-27
hi,
i've just installed Xubuntu 6.06 and i have a problem.
when i try login in GDM and I type a character in login text box, character appears few times. i can't login :|. 
once in a blue moon there's all ok. (1 key pressed = 1 character displayed in login textbox).
when I changed preferences to autologin, my X strarts and everything look OK until i press mouse button. After that action XFCE not responding (but i can still move mouse cursor)
so where i can find the bug? help me
(i hope that you understand my poor english)

(on Mandrake 9 everything is ok)
```
My xorg.conf

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
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc103"
	Option		"XkbLayout"	"pl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/ttyS0"
	Option		"Protocol"		"Microsoft"
	Option		"ZAxisMapping"		"4 5"
EndSection


Section "Device"
	Identifier	"Silicon Integrated Systems (SiS) 86C326 5598/6326"
	Driver		"sis"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	53.67
	VertRefresh	85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems (SiS) 86C326 5598/6326"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by KrakensDen on 2006-08-27
What kind of hardware do you have? Is this a laptop?

What is your native language, and what kind of keyboard layout are you using? 

If you aren't comfortable using english, there are Ubuntu forums available in [several languages]("http://www.ubuntu.com/community/forums").

---

### Post by krtek on 2006-08-27
i have PC (not laptop) :
Graphic card: SIS 6326
CPU: Celeron 333
Memory RAM: 192MB
and serial mouse! (maybe that's problem,huh?)

and i boot my Xubuntu with pci=noacpi option.


I'm from Poland and my language is Polish.


I tried to find solution on polish Ubuntu forum, but nobody knows how to solve my problem.

---

