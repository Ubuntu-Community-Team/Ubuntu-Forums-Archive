---
title: "Nvidia 5200 &amp; H191W &amp; 1440x900 - Stretched Out"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by JALenon on 2007-02-19
Hi,

Relatively new to Linux.

I've a small fileserver using 6.10 LTS.  Graphics setup include a Nvidia PCI 5200 in a PCI slot, a 19" Widescreen H191W.

I'm able to get 1440x900 Resolution after using the multitude of guides on this forum.

But, on 1440x900, Resolution is stretched out - with the taskbars on top and bottom being mostly off the screen.  This does not happen on 1280x768.  On 1280x800, the bottom taskbar is off screen.

I'm looking for a way to get taskbars displayed in the screen in 1440x900.  Auto adjusting the lcd does not seem to be working.  Any thoughts or suggestions would be appreciated.

I've even downloaded the latest drivers from Nvidia and installed those.

Thanks

**xorg.conf:**

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:0:12:0"
EndSection

Section "Monitor"
	Identifier	"H191W"
	Option		"DPMS"
	HorizSync	31-83
	VertRefresh	56-75
	ModeLine 	"1440x900_60" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"H191W"
	DefaultDepth	24
SubSection "Display"
		Depth		24
		Virtual 	1600 1200
		Modes		"1600x1200" "1440x900" "1280x1024" "1280x800" "1280x768" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by tseliot on 2007-02-20
type:
```
sudo nvidia-settings
```

and set the resolution and refresh from there, then click Apply and don't forget to save your changes.

---

