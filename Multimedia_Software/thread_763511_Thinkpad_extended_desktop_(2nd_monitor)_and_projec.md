---
title: "Thinkpad extended desktop (2nd monitor) and projector mode"
date: 2008-04-23
forum: Multimedia Software
---

### Post by jdabgotra on 2008-04-23
I have a Thinkpad which I use for giving powerpoint presentations on projectors, and plug into a 20" LCD monitor. Now, I haven't tried the projector yet, but would like advice first, because after trying the monitor, its been messing up my conf. I never got it to work great, and I had to restore an old xorg.conf to get booting again. The monitor should run at 1680 by 1050 at 60 hz, while the laptop runs at 1024 768 at 60 hz. Now I would like to switch easily between profiles without having any scary boot up problems. What's the proper way to do this? Plug in a VGA cable with a laptop on? or do you have to switch user first or what?

Below is my xorg.conf relevant sections

Now, I have a second related newbie question. I have a LCD TV that has the ol' 1366 by 768 resolution. Yet ubuntu displays 1024 by 768. On that machine (not the laptop) I'm running an Nvidia driver. 



[INDENT]Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "720x400" "640x480"
	EndSubSection
EndSection
[/INDENT]

---

