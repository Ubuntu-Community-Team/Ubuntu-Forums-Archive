---
title: "1440 x 900 for my external wide monitor"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by obavjestenja on 2008-02-24
i have lg laptop with ati radeon xpress 200 video card and i want to be able to connect my new wide lg monitor to laptop, but with ubuntu gusty (xp and vista work fine) cannot have this resolution .
plese help to solve this.

---

### Post by obavjestenja on 2008-02-24
any direction ?

---

### Post by RawMustard on 2008-02-24
You'll probably need to edit your /etc/X11/xorg.conf file and change the bit that looks something like this.
```
	SubSection "Display"
           Depth        24
           Modes        "1400x900" "1280x1024" "1024x768" "800x600"
	EndSubSection
```

---

### Post by obavjestenja on 2008-02-24
this is my  xorg.conf file, my question is where to insert text you wrote  ?

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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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

### Post by obavjestenja on 2008-02-24
> **RawMustard said:**
> You'll probably need to edit your /etc/X11/xorg.conf file and change the bit that looks something like this.
```
	SubSection "Display"
           Depth        24
           Modes        "1400x900" "1280x1024" "1024x768" "800x600"
	EndSubSection
```

i added this but still no 1440x900 resolution i my laptop for external wide monitor .
some other solution maybe ?

---

