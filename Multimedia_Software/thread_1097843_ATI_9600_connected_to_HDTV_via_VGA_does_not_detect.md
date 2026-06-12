---
title: "ATI 9600 connected to HDTV via VGA does not detect monitor....pls help"
date: 2009-03-16
forum: Multimedia Software
---

### Post by MaximCarnage on 2009-03-16
I have a ATI 9600 (opensource ati drivers) connected to my Samsung LN40A550 via VGA. But for some reason it does not detect the HDTV. so I am now using the vesa drivers.

When using the opensource ati drivers everything posts up, grub loads, ubuntu splash seems to finish loading, then the screen turns black. The screen says "Mode Not Supported".

If I use the vesa drivers everything goes smoothly but the resolution is 800x600 ><

How do I get X to detect my monitor and configure it properly ?


How my Xorg Looks.
Section "Device"
	Identifier	"Configured Video Device"
	Driver      	"ati"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by MaximCarnage on 2009-03-18
Nevermind, I had a brainfart.
I figure it out by following this guide:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)


Section "Device"
	Identifier	"ATI Radeon 9600"
	Driver      	"ati"
	BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"  
        	SubSection "Display"
        	 Depth 24
                 Modes "1920x1080" "1600x1200" "1280x1024" "1280x1020" 
       EndSubSection
EndSection

Mark as solved

---

