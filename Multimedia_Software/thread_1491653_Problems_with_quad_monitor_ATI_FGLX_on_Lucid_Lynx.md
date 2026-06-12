---
title: "Problems with quad monitor ATI FGLX on Lucid Lynx"
date: 2010-05-23
forum: Multimedia Software
---

### Post by vladimirc on 2010-05-23
I'm having an annoying issue with my display configuration. I hope someone here could help me out.

Some specs:
Motherboard: MSI 760gm-e51
CPU:         AMD Phenom II 955 Quadcore 
MEM:         8Gbs DDR3
VGA:         ATI Radeon HD4850
             ATI Radeon 3000 (on board)


All four monitors work fine with two X servers ( 2 monitors each instances) on Ubuntu 9.10 with surroundview enabled in the BIOS. I did a fresh install of Ubuntu 10.4 and all i get is 4 blank screens. when i disable surroundview in the BIOS with PCIE as default display the HD4850 work great. I should add that on both installs i used the latest atalyst 10.4. It seems like there's something wrong with Ubuntu 10.04. 

Here's the xorg.conf of the working Ubuntu 9.10:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 1050
	Screen         "amdcccle-Screen[1]-0" 624 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "2048x1152"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "2048x1152"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "2048 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "1-Default monitor"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "640x480"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "1-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1400x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "1-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1400x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1400 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "1-DFP2"
	Option	    "Monitor-CRT1" "1-CRT1"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   4096 2048
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   2800 2800
		Depth     24
	EndSubSection
EndSection

```

Here's a copy of the working xorg.conf of Ubuntu 10.04:

```
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
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "2048x1152"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "2048x1152"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "2048 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   4096 2048
		Depth     24
	EndSubSection
EndSection

```

I hope someone can help me out, thanks!

---

### Post by vladimirc on 2010-05-25
bump

---

### Post by ask@refcapgroup.com on 2010-05-27
Ati catalyst 10.5 just got released yesterday. Try it out. Might solve your problem

---

### Post by vladimirc on 2010-05-27
> **ask@refcapgroup.com said:**
> Ati catalyst 10.5 just got released yesterday. Try it out. Might solve your problem

Thanks, I'll try it out and see what happens.

---

### Post by vladimirc on 2010-05-28
New drivers installed. Nothing still. The driver just won't recognize the onboard vga. Still searching for a solution...

---

