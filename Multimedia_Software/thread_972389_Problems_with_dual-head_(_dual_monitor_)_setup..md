---
title: "Problems with dual-head ( dual monitor ) setup."
date: 2008-11-05
forum: Multimedia Software
---

### Post by bapfreak on 2008-11-05
To start, here are the specs of my computer:

OS: Ubuntu 8.10 Ibex x64
CPU: Phenom 9950
RAM: 4GB of OCZ 1066
VGA: Sapphire ATI 3650 PCIe
MOBO: K9A2 Platinum
MONITORS: 2 x Gateway VX1120

My problem is that when I change from clone mode to big desktop the ability to change the resolution disappears in ATI Catalyst Control Center. This is a fairly modest graphics card that can handle things just fine at 1600x1200. But once it is forced into the monitors highest graphics mode, 2048x1536, the graphics slow down quite a bit. I have tried manually edit xorg.conf, but that didn't work. I have tried using aticonfig, which WORKS, but after I login into my user, the desktop and menu bars don't appear. All I get is a nice 1600x1200 on each monitor, dual monitor display. Strangely enough, the big X appears when the mouse is placed on the right monitor, but not when it is over the left. Next time I buy a graphics card it will be a NVidia. Any help would be appreciated, below is my xorg.conf that was automatically created after installing the restricted hardware driver. As you can see it is quite odd.

=============================================
xorg.conf
=============================================
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	Monitor    "amdcccle-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
=============================================

---

### Post by markayler on 2008-11-06
sorry, I can't help you figure out your problem but I have a similar configuration and when configuring Big Desktop my settings don't stick after rebooting. 
Did you run into this problem? I might just copy your xorg and see if that helps.


bump

---

