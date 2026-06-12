---
title: "Wacom pressure sensitivity issue"
date: 2007-11-28
forum: Multimedia Production
---

### Post by fluoblack on 2007-11-28
I'm the happy owner of both a Wacom Graphire USB tablet and Ubuntu Gutsy. Both worked great and make me a happy penguin until lately, (actually until I upgraded to gutsy)
The pressure senitivity is working step by step, instead of smoothly as you can see on [this picture]("http://pix.nofrag.com/5/0/1/1aa9342cc0fdfaa57a49ef8111548.html")
Is my tablet getting old or did I miss something?


The stylus, cursor and eraser are set in window mode in GIMP and here is xorg.conf:

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV25 [GeForce4 Ti 4200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV25 [GeForce4 Ti 4200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Module"
	Load		"glx"
EndSection
```

---

### Post by Creative2 on 2007-11-29
i dont know if you have whell or button in your wacom but if you have 2 button and a wheell i suggest to read here :
[http://ubuntuforums.org/showthread.php?t=573890](http://ubuntuforums.org/showthread.php?t=573890)

pressure... what do you use ? gimp ? because if you have problem only with gimp maybe you have set it bad instead... i know one time it happend to me..



if you have to change pressure sensitivity read 

here([http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom))

or

i have extract from the last article for you this:


If you want to know what the current (or default) pressure sensitivity setting is, then:

    [jej@ayukawa linuxwacom]$xsetwacom -s get Stylus PressCurve (output in xsetwacom format)
    xsetwacom set stylus PressCurve "0 15 85 100"
    or
    [jej@ayukawa linuxwacom]$xsetwacom -x get Stylus PressCurve (output in xorg.conf Option format)
            Option  "PressCurve"    "0,15,85,100"

    [jej@ayukawa linuxwacom]$xsetwacom -x getdefault Stylus PressCurve 
            Option  "PressCurve"    "0,0,100,100"

If you want to set the pressure sensitivity a bit softer, then:

    [jej@ayukawa linuxwacom]$xsetwacom set Stylus PressCurve 0 15 85 100

---

### Post by fluoblack on 2007-11-29
I tried to set the pressure curve with other values but I get this error (I tried with and without sudo):

```
$ xsetwacom set stylus PressCurve "0 15 85 100"
Set: Value '0 15 85 100' is invalid.
```


So I edited directly xorg.conf adding this to the device "stylus"

```
        Option  "PressCurve"    "0,15,85,100"
```

Yet it still doesn't work :/

I tried with Inkscape, the cuve seems ok but I cannot swear that it's not due to Inkscape post processing the tablet input. 
I also tried with Gogh, and the issue is the same as with GIMP: still not smooth.

By the way, it's a 2 buttons tablet, no pad, no wheel.

---

### Post by Creative2 on 2007-11-29
mm have you restart after replacing ? ( ctrl alt backspace , or restat pc)

have you installated wacom-tools ? i think yes but... 

try to get default settings:

xsetwacom -x getdefault Stylus PressCurve 

=( sorry i can't do more than this

---

### Post by yourpalal on 2008-01-05
if it is working well in other programs perhaps this is the gimp issue:
the gimp takes pressure information and outputs that into a shape, set by you (the default is a circle) with corresponding color,opacity,size etc.. depending on which options you have enabled. You may change the frequency with which the gimp generates these shapes, resulting in a possibly smoother image :D i hope this helps... also i read somewhere.. ( I forget where) that Gimp only has 256 levels of pressure sensitivity, as opposed to 512 you tablet likely supports

---

### Post by yourpalal on 2008-01-23
hi me again.. i was thinking and did you say you made that curve in inkscape? because if so it will be smoother no matter what as inkscape uses vectors and renders them into pixels for the screen, therefore they are always at max resolution/smoothness.. also here is a handy app for tablets:
[http://alexmac.cc/tablet-apps/](http://alexmac.cc/tablet-apps/)
hope it helps

---

