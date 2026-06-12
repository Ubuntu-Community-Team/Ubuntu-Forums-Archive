---
title: "Mach64 TVOut"
date: 2005-11-22
forum: Multimedia &amp; Video
---

### Post by TheMutt on 2005-11-22
Just installed Kubuntu 5.10 on an old Compaq 5670 with an ATI 3D Rage LT Pro video card (mach64).  Got tv out, svideo only no tuner on the card, working with the following xorg.conf changes.

Basically using the vesa driver at 800x600x16, Option TVOut, and rebooting with the monitor disconnected and the tv connected.

Section "Device"
	Identifier	"ATI Technologies, Inc. 3D Rage LT Pro (AGP)"
	Driver		"vesa"
	Option		"TVOut"
	BusID		"PCI:1:0:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage LT Pro (AGP)"
	Monitor		"MX70"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "720x400" "640x480"
	EndSubSection
EndSection

The above also worked in 5.04.

Just wondering if there is a better solution, the included ati*.o drivers did not work (in Mandriva 2006 the included  ati_dri.so and atimisc_dri.so work, only need to add the Option TVOut).  Am limiting resolution to 800x600x16 since NTSC video has less resolution and earlier Retinalburn drivers were limited to 16 bit max.

---

