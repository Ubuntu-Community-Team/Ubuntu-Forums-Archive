---
title: "Help - problems with NVIDIA 7950GT!"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by NLA on 2007-10-05
So I'm relatively new to Ubuntu, but I have an essentially fresh install of Ubuntu 7.04 (64-bit), and I'm pretty sure I've installed all necessary updates.

Recently, NVIDIA released a new set of drivers, 100.14.19 ([here]("http://www.nvidia.com/object/linux_display_amd64_100.14.19.html")), so after going into terminal and running the installer, Xserver refuses to start. (Very similar to [this topic]("http://ubuntuforums.org/showthread.php?t=446141")). I reconfigured xserver (or so I thought) but I'm sitll getting the same error.

Here's the bit of my xorg.conf file that applies to this, I can't see anything wrong with it:

```
Section "Device"
	Identifier	"NVIDIA GeForce 7950GT"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 7950GT"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Any ideas over what I could be doing wrong?

---

### Post by wolfen69 on 2007-10-05
try changing "vesa" to "nvidia".

---

### Post by wolfen69 on 2007-10-05
also, did you try the nvidia drivers in the Restricted Drivers Manager? i have used them everytime with great results. new doesnt always mean better.

---

