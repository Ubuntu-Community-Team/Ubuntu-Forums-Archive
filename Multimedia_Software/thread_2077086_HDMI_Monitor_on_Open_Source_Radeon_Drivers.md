---
title: "HDMI Monitor on Open Source Radeon Drivers"
date: 2012-10-27
forum: Multimedia Software
---

### Post by msaglietto on 2012-10-27
Hello fellas, 

Two weeks ago I buyed a brand new monitor for my laptop.   

I have a HP Envy 14 : [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02664907&tmp_task=prodinfoCategory&cc=ca&dlc=en&jumpid=reg_r1002_usen_c-001_title_r0003&lc=en&product=5054124](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02664907&tmp_task=prodinfoCategory&cc=ca&dlc=en&jumpid=reg_r1002_usen_c-001_title_r0003&lc=en&product=5054124)

It come with a Integrate Intel graphic card and a AMD Radeon 5650.

I was with a Ubuntu 12.04 + gnome-shell  and tried follow every tutorial that I found on the web... Till someone said that fglrx dosent wotk with muxless devices  which is my case .
"(EE) this is a Muxless PX A+I platform, we doesn't supported it"

So then I  installed Ubuntu 12.10 Gnome Remix and start trying with the radeon open source drivers and the xorg.cfg 

So now i have 2 problems:
1. On Radeon drivers gnome-shell fallback to classic mode =(
2. On one screen I have  the top bar and the mouse pointer and in the other monitor I have the login and  I cant move the cursor to the other monitor

Here is my last try with xorg.conf
```

Section "Monitor"
        Identifier   "HDMI-0"
        VendorName   "LG"
        ModelName    "Flatron"
        HorizSync    30.0 - 83.0
        VertRefresh  56.0 - 75.0
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "Primary" "false"
	Option	    "Position" "1366 0"
EndSection

Section "Monitor"
		Identifier 	"LVDS"
		Option 		"VendorName" "Generic"
		Option 		"ModelName" "Generic Autodetecting Monitor"
		Option	    "DPMS" "true"
		Option		"Primary" "false"
		Option		"PreferredMode" "1366x768"
		Option		"TargetRefresh" "60"
		Option		"Disable" "false"
		Option		"Primary" "true"
		Option		"Position" "0 0"
EndSection

Section "Device"
        Identifier     "Card0"
        Driver          "intel"
        BusID           "PCI:0:2:0"
 	Option 		"AccelMethod" "sna"
EndSection

Section "Device"
        Identifier      "Card1"
        BusID           "PCI:1:0:0"
	Driver			"radeon"
EndSection
																  
Section "Screen"
		Identifier "Screen1"
		Device "Card0"
		Monitor "LVDS"
		DefaultDepth 24
		SubSection "Display"
			Depth 		24
		EndSubSection
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card1"
        Monitor    "HDMI-0"
        DefaultDepth    24
        SubSection "Display"
			Depth     	24
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier     	"Layout0"
	Screen		"Screen1"  0 0
	Screen		"Screen0"  1366 0
EndSection

```

Any help will be appreciated 

Best regards

---

### Post by msaglietto on 2012-10-28
I noticed something curious.  With this config I have like 2 screen in one  on the HDMI monitor.

So diggin on the Xorg.0.log i found this:
Radeon is detecting the 2 outputs:
[    17.160] (II) RADEON(0): Output LVDS using monitor section LVDS
[    17.240] (II) RADEON(0): Output HDMI-0 using monitor section HDMI-0
And then Intel is detecting another output:
[    17.449] (II) intel(1): Output LVDS2 using monitor section LVDS

What it could be? Any ideas?

---

