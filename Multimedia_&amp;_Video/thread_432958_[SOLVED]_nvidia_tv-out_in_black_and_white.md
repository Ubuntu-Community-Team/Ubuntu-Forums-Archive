---
title: "[SOLVED] nvidia tv-out in black and white"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by El_Matthews on 2007-05-04
I have a working mythtv setup and now I want to configure the tv out. I have seen many guides but none helped me out.

Whats the problem;
tv-out stays in black and white after nvidia drivers are started.
at boot the asus screen and the progress bar of ubuntu are in colour so cable etc are working.

I am using feisty fawn with latest updates.
nvidia restricted drivers installed with the new restricted drivers module. driver working correctly in glx etc.
I tested this with an svido cable and a compisite cable, both give the same problem.

please help me finding out how to correct this, I really would like to start using my mythbox.

hereby my xorg.conf

```

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
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
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
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	Option 		"TwinView"
	Option         	"TVOutFormat" "SVIDEO"
    	Option         	"TVStandard" "PAL-H" 
EndSection

Section "Monitor"
	Identifier	"3851 FA"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Monitor"
	Identifier      "tv"
	HorizSync 30-50
	VertRefresh 60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
	Monitor		"3851 FA"
	DefaultDepth	24
	Option 		"TVStandard" "PAL-H"
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
 	Identifier "Screen_tv"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
 	Monitor    "tv"
 	DefaultDepth 16
 	SubSection "Display"
 		Depth     16
 		Modes "800x600"
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
```

---

### Post by disturbed1 on 2007-05-04
Try a different PAL standard. I believe in Belgium the standard is PAL B G D H and/or I. Though, not all TVs support every standard.

So, cycle through
PAL-B
PAL-G
PAL-D
PAL-I
Under the "Screen" and "Device" option "TVStandard".

After making changes to your xorg.conf, be sure to restart X. Also back up xorg.conf before making any changes.

---

### Post by klato on 2007-05-04
Also make sure that your TV out format is correct...I know for mine, I use an SVIDEO->COMPOSITE converter and my TV out format is set to COMPOSITE.  Mine also came up black and white before I switched it.  (although I think the driver should automatically detect it anyway...?)

---

### Post by El_Matthews on 2007-05-05
thanks for the tips

I tested with option "TVStandard" to;
PAL-B
PAL-G
PAL-D
PAL-I
changed both under section "Screen" and "Device"  but none of them gave the correct result.

I also tried to change "TVOutFormat" and then I didn't got any image at all anymore so this seems to be correct.

Anybody an other tip?

PS: I always restarted x with ctr + backspace. that should be enough no ?

---

### Post by El_Matthews on 2007-05-10
when connecting directly my svideo cable to my tv I got colour ;) So there was something wrong with my plug that converts svideo to scart.

the problem is now that the tv I want to use has no svideo connection. I have a scart to composite cable but when I use this cable my screen stays black (no image).
I changed following option ```
Option         	"TVOutFormat" "COMPOSITE"
```but still the sceen stays black. Any Ideas?

---

### Post by dodgePT on 2007-05-10
That's definetelly a cable problem. I had a similar problem in my WindowsXP days, and i solved it with another s-video-->scart cable.

> TV OUT using 3rd party S-VIDEO to SCART adapter

PAL or MULTISYSTEM TVs (most often found in European countries)
The symptoms described are not specific to ATI products. This Infobase is provided for the convenience of users especially in Europe. The signal on the TV set may show up black and white using a 3rd party S-VIDEO to SCART adapter.

A SCART connector only supports composite video. If you connect an S-VIDEO cable directly into a SCART adapter, the result will be a black and white signal, regardless of the type of graphics card being used.

There are preferred S-VIDEO to SCART adapters from 3rd party vendors that will properly give you colour display.

I had another solution that seemed more radical, and implies some soldering or connection of 2 pins in scart end.

Check it out here: [http://camp0s.altervista.org/sVideo/how_to.htm](http://camp0s.altervista.org/sVideo/how_to.htm)

The solution is quite simple, but requires some patience and work ;)

---

