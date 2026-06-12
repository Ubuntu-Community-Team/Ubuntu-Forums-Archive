---
title: "Screen Fuzzy After installing nvidia-glx"
date: 2006-03-05
forum: Multimedia &amp; Video
---

### Post by Maverick88 on 2006-03-05
I just installed Breezy Badger.  The first package I installed was nvidia-glx.  I also ran nvidia-glx-config which changed one entry in my xorg.conf file.  Driver "nv" was changed to Driver "nvidia".  

When I was using the nv driver that came with Breezy Badger, a screen resolution of 1440x900 was set.  But after I installed nvidia-glx, the screen resolutionn was set to 1280x768.  I tried changing the screen resolution using "System - Preferences - Screen Resolution", but the highest screen resolution available is 1280x800. 

I also noticed that other resolutions that were previously available are also gone like 1052x768.

Is there a way to add other resolutions like 1440x900, 1052x768 with the nvidia binary driver?  Or will I have to just use the Breezy Badger free nv driver?

Rob

---

### Post by Maverick88 on 2006-03-05
FYI - Below is my xorg.conf file.  It only lists one resolution 1440X900.  

As mentioned earlier, the only difference between the original xorg.cong file installed by Breezy and the new xorg.conf file upadted by nvidia-glx-config is a small change --- Driver "nv" was changed to Driver "nvidia".

Here is my xorg.conf file:

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Maverick88 on 2006-03-06
I fixed it by adding the following modeline to the Section "Monitor" of my xorg.conf file:

Modeline        "1440x900" 97.54  1440 1472 1840 1872 900 919 927 946

I used the modeline calculator at [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

In the optional top part of the online form, I used the Vert and Horz rates as noted above in my xorg.conf file.  In the  middle part of the online form, I used the 1440x900 desired resolution, left the dot clock freq as 0, but instead of using a 60 Hz refresh rate, I used a refresh rate of 55 Hz.  That did the trick.  The resulting modeline when added to my xorg.cong file enabled me to finally have a 144x900 screen resolution with the non-free Nvidia driver.

Rob

---

