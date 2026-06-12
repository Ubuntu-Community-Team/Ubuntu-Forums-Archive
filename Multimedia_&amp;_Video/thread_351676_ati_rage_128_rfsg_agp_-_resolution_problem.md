---
title: "ati rage 128 rf/sg agp - resolution problem"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by drohhyn on 2007-02-02
Hy folks,

Heres my prob: I installed ubuntu 6.10 yesterday. Everything is working fine except my video card: the highest resolution is 800x600 -_-

This is my video card (said lspci | grep VGA ;)): 
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

The interesting part of xorg.conf:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 RF/SG AGP"
	Driver		"ati"
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
	Device		"ATI Technologies, Inc. Rage 128 RF/SG AGP"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x786" "800x600" "640x480" "1x1"
	EndSubSection
EndSection
```

I've changed the driver, tried "vesa" and "r128" but nothing changed.
I also added the resolution "1024x786" at the Display with Depth = 24.

My screen is a Dell ES-17 (50/60Hz)
But i still have these options under system -> config -> screen resolution (dont know if these are the right english names, cause my system is german):
resolution: 800x600 640x480
refresh rate: 60Hz 56Hz

may somebody help me?

---

### Post by az on 2007-02-02
How much memory does the card have?

Try this.  Boot into recover mode adnr un

dpkg-reconfigure xserver-xorg

Pick a color depth of 16 and pick a resolution of 1024x768.


Continue to the end and then run

init 2

to get back to the desktop.

---

### Post by drohhyn on 2007-02-02
tried this before -> error
tried it again -> works

thanks!

(now i have a prob with 1 hd, but i ll try on my own :))

---

