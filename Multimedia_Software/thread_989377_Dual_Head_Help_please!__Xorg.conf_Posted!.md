---
title: "Dual Head Help please!  Xorg.conf Posted!"
date: 2008-11-21
forum: Multimedia Software
---

### Post by nitecon on 2008-11-21
Okay here goes...

I have followed and read up on so many guides for dual head that I am now tired and out of options.

I am currently running Kubuntu 8.10, with all the latest patches, fglrx and ati drivers act the exact same way.  I did download the latest ati drivers to test with but neither fglrx or ati does what I need it to.

First off let me copy and paste my xorg.conf file...

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	screen 0
EndSection
Section "Device"
	Identifier	"Device[1]"
	Driver		"ati"
	Option		"ConnectedMonitor"	"Monitor[1]"
	BusID		"PCI:1:0:1"
	Screen 1
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #MAG
	Option		"DPMS"
	HorizSync	55.47-70.64
	  VertRefresh	59.90-74.98
EndSection
Section "Monitor"
	Identifier 	"Monitor[1]" #Samsung
	Option		"DPMS"
	HorizSync	30-81
	  VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Monitor		"Monitor[0]"
	Device		"Device[0]"
	DefaultDepth	24
	SubSection "Display"
	    Depth	24
	    Modes "1440x900"
	EndSubSection
EndSection
Section "Screen"
	Device		"Device[1]"
	Identifier	"Screen[1]"
	Monitor		"Monitor[1]"
	DefaultDepth	24
	SubSection "Display"
	    Depth	24
	    Modes "1440x900"
	EndSubSection
EndSection
Section "ServerLayout"
  Identifier	"Simple Layout"
    Screen 	0	"Screen[0]"
    Screen	1	"Screen[1]"	RightOf		"Screen[0]"
  InputDevice	"Configured Mouse"	"CorePointer"
  InputDevice	"Generic Keyboard"	"CoreKeyboard"
EndSection
```

Now here is my problem.  I am trying to set up an extended monitor setup...  Where my primary monitor is the MAG, and secondary is Samsung, both are running at the same resolution etc.  The MAG is to the left of the samsung.  What I would like is to have each desktop be independent of the other, not just a large extended desktop.  The xorg.conf does work, but it is still in cloned mode.

I am trying to have it where my MAG is the primary "Workspace" and when I move my mouse cursor to the furthest right position it goes into "Workspace" 2!

Any idea's would be greatly appreciated.  The options for input devices isn't in yet because I just wanted to get a working xorg.conf first.

Thanks in advance.

---

### Post by CHaoSlayeR on 2008-12-04
Hi nitecon,

I struggled myself a lot with the fglrx driver to get dual-head working. I own two CRTs and not LCDs but that wouldn't matter I think.

As I can see you have specified two "Device" sections that would produce two separate desktops and you wouldn't be able to drag windows from one into the other. So I suggest you try my setup. I used only one "Device" section for that. I tried to adapt your monitor settings for this configuration but you may have to tweak them for you to work:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Logitech Dual Action"
EndSection

Section "Files"
EndSection

Section "Module"

#	Load  "bitmap"
#	Load  "ddc"
	Load  "vbe"
#	Load  "i2c"
	Load  "extmod"
	Load  "GLcore"
	Load  "dbe"
#	Load  "v4l"
	Load  "freetype"
#	Load  "int10"
	Load  "glx"
	Load  "dri"
	Load  "drm"
EndSection

[...]

Section "Device"
	Identifier  "Device0"
	Driver      "fglrx"
	BoardName   "ATI Radeon HD2400 Pro"
	Option	    "DesktopSetup" "horizontal"
	Option	    "EnableMonitor" "tmds1,tmds2"
	Option	    "HSync2" "30.0 - 81.0" #This sets the horizontal sync for the secondary display.
	Option	    "VRefresh2" "56.0 - 75.0" #This sets the refresh rate of the secondary display.
	Option	    "PairModes" "1440x900+1440x900"
	[...]
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Device0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1440x900" "1440x900"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

In addition have you tried using the aticonfig utility first? E.g. "aticonfig --initial=dual-head" creates a basic setup using the BigDesktop mode (one desktop stretched over both monitors). This utility always creates a backup of the existing xorg.conf so you can experiment as much as you want.

Greetz,

C]-[aoZ

---

