---
title: "Poor performance with Radeon 7000 pci"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by nostrand on 2007-02-14
I Have a Radeon 7000 pci (i'll guess it's better than the integrated intel i815).

Whenever i play videos or using som GL the screen gets distrupted with blurry text and lines around the application.

I now this isn't at top-of-the-line chipset, but shouldn't Quake 2 be playable?
I get like 10fps or something.

I'm running Ubuntu Edgy, with Linux 2.6.17-11-386 and the radeon driver.

DRI is enabled.

lspci:

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 02)
02:04.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
...

The CPU is a 1GHz Pentium 3

---

### Post by Hiperi0n on 2007-02-17
Hi nostrand. I also have a Radeon 7000, mine is 64MB AGP. I have been trying getting the most performance out of it, because I have seen many users getting beyond 500 fps in glxgears

My device section in xorg.conf looks like this:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "XAANoOffscreenPixmaps"
	#these are the options i have been trying:
	Option	    	"DPMS"	
	Option      	"AGPMode" "2"
	Option      	"AGPFastWrite" "true"
   	Option      	"EnablePageFlip" "true
	Option      	"AccelMethod"   "XAA"
	Option      	"ColorTiling"   "on"
	Option		"AGPFastWrite" 		"true"
	Option		"SubPixelOrder" 	"NONE"
	Option 		"DynamicClocks"		"true"
	Option		"RenderAccel"		"true"

I have been investigating and the reason could be the system switching to the software renderer instead of the hardware one. The games I have played are Quake3 and doomsday, and I get quite slow rates in both. I have uninstalled and reinstalled the free ati drivers and I have broken a couple of times the X. My glxgears fps are ~280fps
I have edgy and a P3 866mhz and 384MB RAM

---

