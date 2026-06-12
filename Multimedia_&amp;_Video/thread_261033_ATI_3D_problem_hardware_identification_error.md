---
title: "ATI 3D problem: hardware identification error?"
date: 2006-09-19
forum: Multimedia &amp; Video
---

### Post by aileen on 2006-09-19
I realize that this is not the first thread on the topic (what an understatement!), but i've been googling and experimenting for days now, and i think i might have some ideas to contribute, or else my problem is not the same as that of the majority. 

dmesg tells me that the fglrx module is loaded, but then appears the error message "Internal AGP not supported in 2.6 kernel.". xorg.0.log contains the following warning & error lines of interest: 

```
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

This is the "Device" sections of my xorg.conf: 
```
Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```

First of all, is it supposed to be two sections with identical names, or is it just the result of different install scripts writing to the file or something? I tried changing BusID from 1:0:0 to 1:0:1 (read that somewhere) but it didn't change anything.

*lsmod | grep agp* gives the following output: 
```
via_agp                10304  0
agpgart                36784  2 fglrx,via_agp
```

Is it correct that the 0 at the end of the via_agp row means that this module is not used by any other modules? Shouldn't it be used by the fglrx module? lspci | grep AGP returns NOTHING. Could it be that the AGP hardware of my motherboard is not detected properly? I have problems autodetecting my harddrive too, have to change (hd2,0) to (hd0,0) in grub everytime i upgrade the kernel.

Lots of info, hope i didn't forget anyting..Thanx!

---

