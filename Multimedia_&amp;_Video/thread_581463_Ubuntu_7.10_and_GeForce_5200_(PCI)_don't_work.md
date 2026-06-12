---
title: "Ubuntu 7.10 and GeForce 5200 (PCI) don't work"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by hoopotus on 2007-10-19
Hello,

As some background information about me I'd like to say that I'm new at this forum but I'm quite familiar with Ubuntu. I noticed there have been several questions about the same graphics card but not any problem like mine.


Using a driver downloaded from nVidia, the X server crashes quite soon crashing the whole machine.

Using a driver downloaded with **Restricted drivers manager**, starting of X ends with following messages in **/var/log/Xorg.0.log**:

[I](EE) Screen(s) found, but none have a usable configuration. 

Fatal server error: 
no screens found 
[/I]

Complete log file:
[http://www.hytti.uku.fi/~kristola/Xorg.0.log](http://www.hytti.uku.fi/~kristola/Xorg.0.log)

**Xorg.conf**, made by restricted drivers manager:
[http://www.hytti.uku.fi/~kristola/xorg.conf](http://www.hytti.uku.fi/~kristola/xorg.conf)

The graphics adapter I've been using earlier is integrated on the motherboard (ASUS something). The Bios setup program has an option which graphics adapter is primary. I've also tried if something would be coming out of the integrated card's connector altough the text mode works on GeForce - but nothing.

I have no earlier experience about this card because I decided to wait for the new version of Ubuntu before installing it. However, the graphical mode works during startup showing the Ubuntu logo with a progress bar. In the console I run command **/etc/init.c/gdm start** to start the X server.

Do you have any ideas?

---

### Post by juniorsonny on 2007-10-19
I used the newest version of Envy released on 10/18/07.  It helped my games work but it won't wake up from sleep mode.  Then just a minute ago I read a post that said installing the "xserver-xgl" package helps. I haven't done that yet but was going to try later.

---

### Post by juniorsonny on 2007-10-19
I noticed in your xorg.config that it didn't have the name of your card listed.

Section "Device"
	Identifier	"Tyypillinen nÃ¤ytÃ¶nohjain"  
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

 it should be something like
Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"  
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection



At least that's what mine has. Not sure if this will help.  That name needs to be the same as the name your Xorg.0.log.

(II) Bus 5: bridge is at (0:19:1), (0,5,5), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfaf00000 - 0xfbffffff (0x1100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(--) PCI:*(5:6:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfb000000/24, 0xd0000000/27, BIOS @ 0xfafe0000/1


Still have to do my test. I'll post my results later.
I also think that the Busid*pci:1:0:0* needs to be Busid*pci:5:6:0 this one i'm not quite sure of.

---

### Post by juniorsonny on 2007-10-19
Found something else. Vesa driver are installed and assingned to your pci bus 5:6:0 found it here.


LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 05:06:0
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found

---

### Post by hoopotus on 2007-10-20
Thanks for replies. I'll be trying it soon.

---

### Post by hoopotus on 2007-10-20
I did the things you mentioned and reinstalled following packets:

linux-restricted-modules-common 
linux-restricted-modules-2.6.22-14-generic
libglu1-mesa


Now the card works including 3d effects, but the mouse cursor is still out of order:

[http://www.hytti.uku.fi/~kristola/cur1.jpg](http://www.hytti.uku.fi/~kristola/cur1.jpg)
[http://www.hytti.uku.fi/~kristola/cur2.jpg](http://www.hytti.uku.fi/~kristola/cur2.jpg)

Very funny, and furthermore, I don't find the settings for mouse cursor anymore in the new ubuntu.(?)

---

