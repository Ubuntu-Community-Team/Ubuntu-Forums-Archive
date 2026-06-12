---
title: "Envy Driver + OpenGL?"
date: 2008-10-13
forum: Multimedia Software
---

### Post by projectgonewrong on 2008-10-13
I have a ATI Radeon X1300 XGE card.

I installed the ATI driver with Envy, it fixed the resoultion problem and I can have full effects including 3d Windows and Workspace cube.

But I can't run any program that uses OpenGL and can't even run "glxinfo" or "fglrxinfo"without getting a Segmentation Fault.  (Even when I turn off Compiz they still have a SegFault)

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

---

### Post by projectgonewrong on 2008-10-15
Anyone have an idea of why Compiz could run just fine but any OpenGL program won't run?

---

### Post by porchrat on 2008-10-15
may sound a little simple, but are you sure that the aticonfig actually used the xorg.conf?  sometimes (god only know why) it doesn't.

You can force the aticonfig to utilise the xorg.conf like this:

```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

```

just a thought

---

### Post by projectgonewrong on 2008-10-15
Well I didn't configure it Envy-NG did, but I tried that command anyways and then did Ctrl+Alt+Backspace and still OpenGL isn't working and neither is "glxinfo" or "fglrxinfo"

---

### Post by projectgonewrong on 2008-10-16
Well I fixed it.

Turns out Installing ATI drivers in Hardy Heron isn't very hard.  (I never tried since I used Envy previously in older releases where it was hard to configure and Envy was an easy fix)

I just followed this guide and it worked if anyone else has this problem that I did.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Also here is my Xorg.conf now

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"L1975NW"
	SubSection "Display"
		Modes		"1440x1440"	"1440x900"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Option		"UseFastTLS"	"1"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Busid		"PCI:1:0:0"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "ServerLayout"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Monitor"
	Identifier	"L1975NW"
	Option		"DPMS"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "Module"
	Load		"glx"
EndSection
```

---

