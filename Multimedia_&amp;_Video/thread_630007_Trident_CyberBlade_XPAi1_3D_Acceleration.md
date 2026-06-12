---
title: "Trident CyberBlade XPAi1 3D Acceleration"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by mulder_edu on 2007-12-02
Anyone know how to get 3D Acceleration to work on a Trident CyberBlade XPAi1?  The graphics card supports it, but apparently the Linux driver will not.  Any ideas how to get it to work?

Here's my xorg.conf output (manually edited):

> Section "Files"
EndSection

Section "Module"
	Load		"dri"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
EndSection

Section "DRI"
	Mode   0666
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Trident Microsystems CyberBlade XPAi1"
	Driver		"trident"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade XPAi1"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by hwertz on 2007-12-03
> **mulder_edu said:**
> Anyone know how to get 3D Acceleration to work on a Trident CyberBlade XPAi1?  The graphics card supports it, but apparently the Linux driver will not.  Any ideas how to get it to work?

Here's my xorg.conf output (manually edited):
     Doubtful.  I think this is like some of the pre-Rage128 Rage chips or the like where it technically supports 3D, but not enough features to really behave that normally.  (I.e. if it did work it'd do glxgears, but not most 3D games or desktop effects.)  On the other hand, I ran an older model CyberBlade in a PII-300, and the video scaler etc. on the card work great.

---

