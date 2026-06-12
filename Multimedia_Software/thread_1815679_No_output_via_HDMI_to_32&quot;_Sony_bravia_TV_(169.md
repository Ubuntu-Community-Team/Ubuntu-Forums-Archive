---
title: "No output via HDMI to 32&quot; Sony bravia TV (16:9)"
date: 2011-07-31
forum: Multimedia Software
---

### Post by Kennes on 2011-07-31
Hi guys,

Ive seen quite some back and forth around this topic but I just cant seem to get any headway with the issue:(.

Im able to detect the monitor on the laptop once connected but the monitor indicates "No Input". I've tried rebooting the computer with the HDMI cable connected with no avail. I have also tried out a host of other solutions offered in different forume with absolutely no change.


I have a HP pavilion dv6 3310si with 32-bit Ubuntu 11.04, an ATI HD Radeon 5600 with latest ATI radeon driver installed and this is my xorg.conf;

My xorg.conf:
Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Any help will be highly appreciated :)

---

### Post by Kennes on 2011-08-01
Anyone?...Guyz?...

---

### Post by 4Orbs on 2011-08-01
I think you need to open the ati Catalyst Control Center (as admin) and change the settings in order to enable the hdmi output to an external monitor.

---

