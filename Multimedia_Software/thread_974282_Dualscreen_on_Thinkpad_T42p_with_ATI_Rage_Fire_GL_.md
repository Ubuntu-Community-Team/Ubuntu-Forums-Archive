---
title: "Dualscreen on Thinkpad T42p with ATI Rage Fire GL T2"
date: 2008-11-07
forum: Multimedia Software
---

### Post by oneafrikan on 2008-11-07
Hi All,

Any and all advice would be awesome ;-)

I've been trying to get a dualscreen working with a Thinkpad T42p running and am having no joy.  

**OBJECTIVE:** is to be able to plug in the 2nd monitor at work and get going - I'm not trying to create an xorg.conf configuration that will be stable from now on - this is to be mobile.

Primary problem is that Ubuntu does not seem to detect the screen (Acer AL1916W 19" LCD) I have attached at all, in the "Screen Resolution" utility.

I've been bouncing around xorg.conf config variations and nothing.  I did have it kinda working once, but when I've tried to replicate it properly, it doesn't work.

My current xorg.conf file is below, which seems to be stable and working, but does not detect the new screen when I attach it, or if I reboot with it attached.

```

Section "Device"
	Identifier	"Configured Video Device"
	BusID       	"PCI:1:0:0"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
#	Device		"ATI MOBILITY FIRE GL T2/T2e"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

#Section "Device"
#	Identifier  	"ATI MOBILITY FIRE GL T2/T2e"
#	BusID       	"PCI:1:0:0"
#	Driver		"fglrx"
#EndSection

```

I can post any of the other variations if needs be.  Am I doing something wrong, or is there something that needs to be added??

Any further ideas?

Thanks in advance!!

Gareth

---

### Post by oneafrikan on 2009-08-24
Bump ;-)

Anyone able to do a Dual Screen on a ThinkPad T42p with Jaunty?

---

