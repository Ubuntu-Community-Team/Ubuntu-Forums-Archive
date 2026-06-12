---
title: "SIS Screen Resolution"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by postalservice14 on 2007-07-06
I know lots of people have posted about this, but for some reason, mine seems to be different.  Of course!

I can't get my 1440x900 screen resolution to work.  I have added it to the default xorg.conf restarted X, and nothing.  Run the dpkg-reconfigure, and selected the resolution, and still nothing.  I've made sure that "sis" is the video driver I am using and also tried "vesa" just for the heck of it.  Nothing...

Here is my latest excerpt from xorg.conf.

```

Section "Device"
	Identifier	"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

Thank you and good luck :-)

John

---

