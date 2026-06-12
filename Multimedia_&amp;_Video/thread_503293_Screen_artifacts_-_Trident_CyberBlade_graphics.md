---
title: "Screen artifacts - Trident CyberBlade graphics"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by shawnrusso on 2007-07-17
Hello, all,

I'm an experienced Windows user but brand new to Linux/Ubuntu 7.0.4.  I've installed Ubuntu on an older Compaq Presario laptop and am getting screen artifacts intermittently (enough to prevent reading the screen at times). The artifacts look like strips or oblong boxes of garbled pixels.  Also getting a "shimmer" (text looks like it's trying to beam to another planet) but that is tolerable and was there when I had Windows installed (I never bothered to upgrade the video driver). 

Would you recommend trying to install an upgraded video driver? If so, which package (if that's the right term) should I use or do I need to do it manually?

Or do I need to tweak some video settings? No clue how to do that either.

I do have universe and multiverse enabled. I noticed something called "Restricted Driver Manager" but when I open that dialog there are not buttons to add or edit drivers.

Laptop specs are at [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00009224&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00009224&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

Snippet from xorg file is below:

Section "Device"
	Identifier	"Trident Microsystems CyberBlade i1"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-40
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade i1"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600"
	EndSubSection
EndSection


Many thanks!

---

