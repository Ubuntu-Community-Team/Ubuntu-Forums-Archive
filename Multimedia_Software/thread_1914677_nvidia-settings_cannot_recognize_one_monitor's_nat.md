---
title: "nvidia-settings cannot recognize one monitor's native resolution."
date: 2012-01-24
forum: Multimedia Software
---

### Post by MXIIA on 2012-01-24
I have 2 monitors. On the left I have a Dell 1704FPT and on the right I have a Dell E177FP. My GPU is a GeForce6800.
The left monitor is plugged in directly via VGA while the right one is plugged in to a VGA -> DVI adapter.
Both have a native resolution of 1280x1024.
nvidia-settings recognizes the right one's native resolution (the E177FP in DVI port) at 1280x1024.
However, it fails to allow me to select the same resolution on the left monitor. 
The highest resolution I can select is 1024x768. If I do Advanced, and set the resolution manually the result is the monitor being zoomed in and not showing everything (basically the monitor still thinks it's a 1024x768 and I have to move around the monitor with my mouse to see the whole screen).

Any help is appreciated.

This problem has all of the sudden shown up on all the distros I have tried in past weeks.
I am on 11.10 now, but I did have this issue in Arch, Debian, and Fedora over the past week. 
Previously I had an 11.10 install and this problem was not occuring.

---

### Post by rick_james on 2012-01-26
> However, it fails to allow me to select the same resolution on the left monitor. 
The highest resolution I can select is 1024x768.

The same thing happened to me with my Dell IN1920 LCD monitor that only has a VGA connector.  It thinks it is a CRT and it was stuck at 1024x768.

I had to edit the xorg.conf file to make it work.

Here's mine:

```
Section "Monitor"
	Identifier "DELL IN1920"
	Option "PreferredMode" "1360x768_60.00"
	HorizSync	30-83
	VertRefresh	50-75
	VendorName      "Dell"
	Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
EndSection

Section "Screen"
	Device "nVidia Corporation NV34 [GeForce FX 5500]"
	Identifier "Default Screen"
	Option "ModeValidation" "NoMaxPClkCheck"
	Monitor "DELL IN1920"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1360x768_60"
	EndSubSection
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5500]"
	BoardName	"nvidia"
	VendorName      "NVIDIA Corporation"
	Option	"NoLogo"	"True"
EndSection
```

What made it work was adding a line under "Screen" that says Option "ModeValidation" "NoMaxPClkCheck"

and I also added a modeline under "Monitor" that says Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

I can't say it'll work for you but this fixed it well enough for me. :-)

Regards,
Paul

---

### Post by MXIIA on 2012-01-27
I tried that.. and nothing.
Here's my current xorg.conf
[http://pastebin.com/LRuV5a8T](http://pastebin.com/LRuV5a8T)

---

