---
title: "Compiz-Fusion Not Working On Radeon X300"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by eternalperson on 2007-10-06
Help! I'm using An ATI Radeon X300 graphics card, with the "fglrx" driver.
I'm on Gutsy. Everything works, but Compiz-Fusion. It says "Desktop Effects could not be enabled".

Here is my "xorg.conf" file output.
```
Section "Files"
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
	Identifier	"ATI Technologies Inc RS482 [Radeon Xpress 200]"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "Monitor"
	Identifier	"eView 17s"
	Option		"DPMS"
	HorizSync	30-60
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS482 [Radeon Xpress 200]"
	Monitor		"eView 17s"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600" "640x480"
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
EndSection
```

---

### Post by Forlong on 2007-10-06
You need to install Xgl:
```
sudo apt-get install xserver-xgl
```

---

### Post by eternalperson on 2007-10-06
> **Forlong said:**
> You need to install Xgl:
```
sudo apt-get install xserver-xgl
```

Thanks so much. That worked.

---

### Post by eternalperson on 2007-10-22
Hey admins, I made a mistake in the title, can 'X300' be replaced with 'X200' 

Thanks in advance!

---

