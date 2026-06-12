---
title: "Hp pavilion dv 6505 resolution problem"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by jH. on 2007-12-21
Trying to make Gutsy work on my HP laptop. One of the biggest issues I'm having problems with is the screen. The resolution just doesn't agree to be any higher than 800x600. Having tried a few of the advice given here (yet not getting any solution to the problem) I decided just to ask it straight.

**Problem**: *can't set my resolution to 1280x800*

Some details:

** Computer:** [I]Hp pavilion dv 6505 -laptop
[B][/I]
 Video card:[/B] *NVIDIA GeForce 7150M*
[B]
screen: [/B]*WXGA BrightView 15.4"* (just can't find the vertical and horizontal frequency rates.. I keep searching, however)

This is what my Xorg.conf looks like:
```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:18:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
EndSection

```

Tried a script given in another related thread. Result:

```

me@mylaptop:~$  sudo xvidtune
Vendor: , Model: 
Num hsync: 1, Num vsync: 1
hsync range 0:  31.50 -  37.90
vsync range 0:  50.00 -  70.00
Video are not settable on this chip

```

What can I do?

---

