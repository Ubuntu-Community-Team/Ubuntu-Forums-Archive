---
title: "Wrong driver in xorg (Radeon 9000 should be 7500)"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by Sethiano on 2006-06-06
Hi all! 

Xorg thinks, for some reason, that I have the Radeon 9000 card and have therefore this written i the xorg.conf

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
```

Now, the problem is that my card is Radeon 7500! I have tried the 
```
 sudo dpkg-reconfigure xserver-xorg 
``` but with no luck, I can only choose "ati" and not "radeon". When i choose "ati" it says that my card is Radeon 9000.

How should I do to install the proper driver for my Radeon 7500?

---

