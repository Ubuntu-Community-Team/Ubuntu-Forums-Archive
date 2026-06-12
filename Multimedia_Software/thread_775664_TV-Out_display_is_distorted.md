---
title: "TV-Out display is distorted"
date: 2008-04-30
forum: Multimedia Software
---

### Post by Gotterdammerung on 2008-04-30
Hi,

I have a laptop (Intel Core2Duo T7500, Nvidia 8600M 512MB) running Ubuntu HH 8.04 (nvidia-glx-new and nvtv are installed). I connected my TV to it with a composite cable but the display is distorted. Please, help!

Here is my xorg.conf:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
	Option		"XkbVariant"	"thinkpad"
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
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	Option         	"AllowGLXWithComposite" "True"
	Option		"NoLogo" "True"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"Device[1]"
	Driver		"nvidia"
	Option		"TVOutFormat" "Composite" 
	Option		"TVStandard" "PAL-M" 
	Option		"ConnectedMonitor" "TV" 
	BusID		"PCI:1:0:0" 
	Screen		1
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Monitor		"Monitor[0]"
	Device		"Device[0]"
	Defaultdepth	24
	
	Option         	"AddARGBGLXVisuals" "True"
	Option		"DisableGLXRootClipping" "True"
	
	SubSection     "Display"
		Depth       24
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen[1]"
	Monitor		"TV"
	Device		"Device[1]"
	Defaultdepth	24

	SubSection     "Display"
		Depth       24
		Modes      "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 0	"Screen[0]"
  	Screen 1	"Screen[1]" RightOf "Screen[0]"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection
```

---

### Post by Gotterdammerung on 2008-04-30
up

---

### Post by Gotterdammerung on 2008-04-30
up

---

### Post by Elderon on 2008-05-01
Is your start menu off the bottom of your screen?

A thought I had was that hardy does not seem to scale the UI correctly with tv output. works fine on a normal monitor.

could be just me.

---

### Post by Gotterdammerung on 2008-05-02
> **Elderon said:**
> Is your start menu off the bottom of your screen?

A thought I had was that hardy does not seem to scale the UI correctly with tv output. works fine on a normal monitor.

could be just me.

the tv output looks like a pinky rain. I can't distinguish what is what.

I also tried nvidia-settings application without success.

---

### Post by Gotterdammerung on 2008-05-07
up

---

