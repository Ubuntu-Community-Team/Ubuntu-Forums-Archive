---
title: "Problem with dual screens, different resolutions on monitors"
date: 2008-07-12
forum: Multimedia Software
---

### Post by probl3mchild on 2008-07-12
After googling around for dual screen set ups none of the tutorials really helped me.   My problem is I have a laptop with an external monitor connected to it. When i try to use aticonfig resolution,1=XxX, it tells me screen 1 does not exist in my xorg.conf.  Even though screen1 is not listed in xorg.conf the catalyst driver still recognizes it.  
I have one monitor at 1280x1024 and would like the other at 1024x768.  I have an ATI card running the ati drivers.  Any help would be appreciated.  


Thanks

Below is my relevant xorg.conf

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection
Section "Module"
	Load		"glx"
EndSection


```

---

### Post by DouchesWild on 2008-08-20
Seconding this exact problem. I'm totally willing to reinstall Ubuntu from scratch.

---

