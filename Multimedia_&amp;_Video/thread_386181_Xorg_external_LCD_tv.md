---
title: "Xorg external LCD tv"
date: 2007-03-16
forum: Multimedia &amp; Video
---

### Post by iamthemonkeyman on 2007-03-16
Hey all,

First time poster...
I just recently installed kubuntu and have been experiencing some problems editing my xorg.conf to display on an external lcd tv. Everything else I want is working real sweet but this has been bugging me.

Here's what i'm using :

ibm t43 laptop with ati x300 card, using DVI off the dock.
the tv is 1920x1080 :) . laptop 1400x1050
i'm running kubuntu and the ati fglrx driver.

I can get a picture to display on the tv by having the DVI cable in at boot, but it only shows as a box in the centre of the screen (not widescreen or even close to filling the screen). I guess it's just showing the laptop monitor res.

i've had a few (failed) attempts at setting the xorg.conf and reset it back to pretty standard as you will see...

i think my head imploded somewhere around trying to work out what was 'monitor' and what was 'screen'.

```

Section "Device"
	Identifier "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver "ati"
	BusID "PCI:1:0:0"
EndSection

Section "Device"
	Identifier "aticonfig-Device[0]"
	Driver "fglrx"
EndSection

Section "Monitor"
	Identifier "Generic Monitor"
	Option "DPMS"
EndSection

Section "Monitor"
	Identifier "aticonfig-Monitor[0]"
	Option "VendorName" "ATI Proprietary Driver"
	Option "ModelName" "Generic Autodetecting Monitor"
	Option "DPMS" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor "Generic Monitor"
	DefaultDepth 24
	SubSection "Display"
		Depth 1
		Modes "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device "aticonfig-Device[0]"
	Monitor "aticonfig-Monitor[0]"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		ViewPort 0 0
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "aticonfig-Screen[0]"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
	InputDevice "stylus" "SendCoreEvents"
	InputDevice "cursor" "SendCoreEvents"
	InputDevice "eraser" "SendCoreEvents"
	InputDevice "Synaptics Touchpad"
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

Section "DRI"
	Mode 0666
EndSection

```

I don't even really need to get one big desktop across both screens...Just a nice big widescreen desktop with my lappy shut will suffice

SO....anyone know what I need to add?
Any help much appreciated...

---

### Post by iamthemonkeyman on 2007-03-17
*bump*

---

