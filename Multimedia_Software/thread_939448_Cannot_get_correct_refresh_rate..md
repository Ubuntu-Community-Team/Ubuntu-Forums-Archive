---
title: "Cannot get correct refresh rate."
date: 2008-10-05
forum: Multimedia Software
---

### Post by Dark_Jester on 2008-10-05
Hi all, I need help switching my refresh rate, I just can't seem to figure it out.

**Current display mode:** 1440x900@60Hz in 24-bit.
**What I want:** 1440x900@75Hz in 32-bit.

I tried going to [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php) to get a modeline to put in the xorg.conf, but it didn't work out, I just got told that Ubuntu was going to run in low graphics mode because it couldn't detect my settings.
The modeline I tried was "Modeline "**1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync**" and to be honest I'm not sure if this is accurate. I put this piece of information in **Section "Monitor"** of my xorg.conf and that's when it went bad. 

**Display Adapter:** ATI Radeon 9600

**xorg.conf contains:**
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

---

