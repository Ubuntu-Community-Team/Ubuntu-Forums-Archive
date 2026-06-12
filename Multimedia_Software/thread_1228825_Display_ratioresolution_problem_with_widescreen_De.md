---
title: "Display ratio/resolution problem with widescreen Dell monitor"
date: 2009-08-01
forum: Multimedia Software
---

### Post by lilychef on 2009-08-01
Hey, there!    After upgrading to Jaunty, my 22"Dell widescreen monitor does not have the right resolution/display ratio... Everything is all stretched out horizontally... (pictures, etc)  I think I don't have enough options in my display settings panel.... First of all, the display settings panel shows an "unknown monitor" (which doesn't seem too strange), but I cannot change the refresh rate, and my resolution choices only go up to 1280x1024... I'm thinking I need 1440x900, but I'm not sure...  I've been reading that I might need to edit the  HorizSync/VertRefresh settings in xorg... Here's my xorg -- it doesn't look like anybody else's that I've seen! Ha!  Seems that some important info is missing...  Thanks in advance for some insight!  I'm still new to this...

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"vesa"
EndSection

---

### Post by wojox on 2009-08-01
Let's look at something:

```
sudo lshw -C video
```

Run that and post it back up here please.

---

### Post by lilychef on 2009-08-01
Thanks for the quick response!  Here ya go:

*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV516 [Radeon X1300/X1550 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV516 [Radeon X1300/X1550 Series] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0

---

### Post by wojox on 2009-08-01
When you go to System > Administration > Hardware Drivers 
Does it list any drivers and if so is it activated?

---

### Post by lilychef on 2009-08-01
No - it doesn't list any drivers.... I was wondering about that....

---

### Post by lilychef on 2009-08-04
Nobody has any suggestions?   I can't find much in the forums that makes sense to me...

---

