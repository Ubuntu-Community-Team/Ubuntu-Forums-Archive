---
title: "drmOpenDevice failed (fglrx)"
date: 2008-06-16
forum: Multimedia Software
---

### Post by sim-value on 2008-06-16
HI !

I am messing around with fglrx for some weeks now and what ever i did Failed either with Mesa drivers or Low graphics mode .

I think there is a kinda more serious Problem cause when using :
```

Option "no_accel" = "no"
Option "no_dri" = "no"
```
forcing X to use fglrx i always get low graphics mode ...

My xorg.conf:
```
Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Synaptics Touchpad"
	Option		"AIGLX"	"on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"fglrx"
	Load		"GLcore"
	Load		"glx"
	Load		"DRI"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"SHMConfig"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"UseFastTLS"	"1"
        //here there would come the above metioned options ...
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"RENDER"	"Enable"
	Option		"DAMAGE"	"Enable"
EndSection

```
My xorg.log is attached ..

any solutions ?
or Tips ?

Greetings /me

---

### Post by sim-value on 2008-06-23
BUMP! 

now im using lates drivers installed with a script ...

---

