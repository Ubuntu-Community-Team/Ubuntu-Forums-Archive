---
title: "NV driver returns wrong panel size"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by pcraven on 2007-04-16
I've got a Dell 2001FP monitor that runs 1600x1200 fine with 6.06 ubuntu. I'm trying to get it working under Fiesty. (Installed with Herd 5, all on-line updates applied.) But when I start, I can only get resolutions up to 1280x1024. The nvidia driver doesn't work at all (it did with the prev version.)

(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1280 x 1024
(II) NV(0): Panel is TMDS
(--) NV(0): VideoRAM: 262144 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Monitor2: Using hsync range of 31.00-80.00 kHz
(II) NV(0): Monitor2: Using vrefresh range of 56.00-76.00 Hz
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)

My xorg file:

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"vbe"
	Load	"glx"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Nvidia"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	VideoRam	256000
EndSection

   Section "Monitor"
       Identifier      "Monitor2"
       DisplaySize     408 306
       Option          "DPMS"
       HorizSync       31-80
       VertRefresh     56-76
       ModeLine        "1600x1200" 160.00 1600 1664 1856 2160 1200 1201 1204 1250
   EndSection
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-160	
	VertRefresh	43-170
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia"
	Monitor		"Monitor2"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Inigo Montoya on 2007-04-17
I guess something changed in the way Xorg's nvidia driver handles some options.
The two following lines
```
(II) NV(0): Not using mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
```
make me suggest you to comment out the following lines like this:
```

Section "Monitor"
Identifier "Monitor2"
# DisplaySize 408 306
Option "DPMS"
HorizSync 31-80
VertRefresh 56-76
# ModeLine "1600x1200" 160.00 1600 1664 1856 2160 1200 1201 1204 1250
EndSection

```
Restat Xorg (there is an option in the login screens drop down menu) and see if it helps.
btw. the commented out lines are not/should not be vital for your Xorg configuration.

greetings
im

---

### Post by pcraven on 2007-04-17
Commenting out those lines unfortunately does not fix the problem. Personally, I wonder where this line comes from:

> (--) NV(0): Panel size is 1280 x 1024

I'd like to convince the driver that really isn't my panel size.

---

### Post by Inigo Montoya on 2007-04-18
There is a thread regarding your monitor starting here:
[http://www.ale.org/archive/ale/ale-2004-06/msg00299.html](http://www.ale.org/archive/ale/ale-2004-06/msg00299.html)
The therein mentioned solution is:
> I would try, instead, setting the vertical, horizontal, and resolution and let 
it figure out the modeline.

in the "Monitor" section set
HorizSyc 60
VertRefresh 75

Then in the "Screen" section have
	Modes "1600x1200"

Let the X server figure out the modeline.  

Michael
Just to have it mentioned...
Don't forget to restart your Xorg server.

---

### Post by pcraven on 2007-04-19
Thanks for the suggestion, it still didn't work though. Usually I could always get it to work by playing with the xorg file but not this time. "Herd 5" actually did work, but one of the updates broke it, and it never went back to working.

---

