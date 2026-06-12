---
title: "Chrome 9 HC IGP: Broken lines while playing movie"
date: 2008-12-05
forum: Multimedia Software
---

### Post by siddharthseth on 2008-12-05
Hi 

I am running Ubuntu 8.04 on Fujitsu Siemens Amilo Li1705. While playing movies, a section of screen is rendered as broken horizontal lines.

Here is the output of lshw:
> 
*-display UNCLAIMED
                description: VGA compatible controller
                product: Chrome9 HC IGP
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: latency=16 mingnt=2


The chipset is P4M900. Is this a driver issue ? I cannot figure out which driver is it using ? Xorg.conf looks funny. There is nothing in "Device" section. Still the UI works .. i wonder how ??

> 
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection


---

### Post by inobe on 2008-12-05
run glxgears in terminal, tell me how many frames you get.


also how much vram have you allocated for onboard video in the system bios ?

---

### Post by siddharthseth on 2008-12-05
glxgears:
> 
sid@Desert:~$ glxgears 
2338 frames in 5.0 seconds = 467.103 FPS
1880 frames in 5.0 seconds = 374.336 FPS
2100 frames in 5.0 seconds = 417.745 FPS
2160 frames in 5.0 seconds = 431.755 FPS
2000 frames in 5.0 seconds = 399.233 FPS
2480 frames in 5.0 seconds = 495.702 FPS


how do you check for the amount of vram? From the BIOS i could find this:
System memory: 640KB
Extended memory: 785408 KB

cheers

---

### Post by siddharthseth on 2008-12-05
Managed to find the amount of vram 

> (==) CHROME(0): Depth 24, (==) framebuffer bpp 32
(==) CHROME(0): RGB weight 888
(==) CHROME(0): Default visual is TrueColor
(--) CHROME(0): Chipset: "P4M900/VN896/CN896"
(--) CHROME(0): Chipset revision: 0
(--) CHROME(0): Probed amount of VideoRAM = 262144 kB


had to skim through the Xorg.0.log .. phew !!! that was quite some work. 

cheers

---

### Post by inobe on 2008-12-05
disable desktop affects then play that video

---

### Post by siddharthseth on 2008-12-06
The desktop effects were never enabled . Supposedly i cannot enable them, but that's a different story. I was running awn. So i switched it off and turned off metacity. Still no success, I can still see a patch on the right side of screen rendered as lines.

---

### Post by inobe on 2008-12-06
its has to be the driver

looks like the vram is 256, that doesn't seem to be the problem now.

from the frame rates and desktop affects being off' it certainly has issues with 3d, in that log' did it say yes to direct rendering ?

---

### Post by siddharthseth on 2008-12-06
Hi 

> cat /var/log/Xorg.0.log | grep direct
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(II) CHROME(0): direct rendering disabled


No direct rendering

---

