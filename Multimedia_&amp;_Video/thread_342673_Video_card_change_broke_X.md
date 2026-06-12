---
title: "Video card change broke X"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by steve0921 on 2007-01-20
After a recent power surge (I think) the geforce2 on my old desktop stopped rendering anything properly so I've pulled it out and am trying to use the SiS integrated card on my motherboard.

X has not worked since then. Originally, it failed with the error 
```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```
but some searching indicated that I should remove the nvidia-glx package that wasn't doing me any good.

Now I get a new error that baffles me, and I have been unable to find any pertinent information:
```
Error of failed request: badlength (poly request too large or internal xlib length error)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 1 (X_GLXRender)
Serial number of failed requeset: 185
Current serial number in output stream: 186
```
Or, if I try not using the glx module
```
Fatal server error:
no GLX visuals available
```

The video configuration on this computer may be a little messed up because I have done some playing with aiglx on it. Any help would be greatly appreciated; I don't need anything fancy, just a normal 2D desktop that works.

Here is my xorg.conf:

```
Section "Module"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"IBM G54"
	Option		"DPMS"
	HorizSync	30-69
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
	Monitor		"IBM G54"
	DefaultDepth	24
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

```

---

### Post by taurus on 2007-01-20
Try to reconfigure X again with

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by steve0921 on 2007-01-20
I'm sorry, I forgot to mention that I'd done that. The above xorg.conf is the result of the reconfiguration with only two changes that I'd made afterwards in other attempts. I've commented out the DRI stuff (no noticeable effect) and removed that "wacom" input device entries that my system doesn't need.

---

### Post by steve0921 on 2007-01-20
Hmm, 

I'd been trying to start X up again through gdm using '/etc/init.d/gdm restart' but just for kicks I decided to run 'startx' instead.

And it works. It doesn't work great: it's only 640x480 and I can't appear to change that, but it appears my problems have been with gdm misbehaving and not X being configured wrong.

This state of affairs is bearable, but I think I will spend some time seeing if I can fix gdm. A point in the right direction would be nice too (if anyone has some insight).

Thanks taurus.

---

