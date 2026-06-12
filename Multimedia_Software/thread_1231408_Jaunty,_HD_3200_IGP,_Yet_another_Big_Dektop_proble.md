---
title: "Jaunty, HD 3200 IGP, Yet another Big Dektop problem"
date: 2009-08-04
forum: Multimedia Software
---

### Post by leventaksu on 2009-08-04
Hi there,
It has been now days I have been trying to set my ATI with dual monitors. I have tried a lot of things, Googled a lot and gone some distance but still could not get it right.

I have tried all combinations of
[LIST]
[*]Intrepid/Jaunty
[*]stock fglrx from repository/latest fglrx from ati web site.
[/LIST]

I have these:

[LIST]
[*]Samsung 797DF CRT monitor on the left, which can do quite high resolutions without a problem in Windows. 
[*]Acer X233H which is connected through DVI and it can do 1920x1080.
[*]Gigabyte GA-MA78GM-UD2H motherboard which has HD 3200 integrated graphics adapter.
[*]Jaunty 9.04.
[*]64 bits.
[*]Latest fglrx 8.632 from ATI web site: Catalyst 9.7 
[/LIST]

I want to be able to drag windows among the monitors so Big Desktop is the way to go. Windows XP on the other partition can do any resolution with these monitors, without a problem.

I have two problems:

[LIST=1]
[*]I can have my desktop layout etc. as I wanted but I cannot get right resolutions for my monitors. The system starts with in low resolution and mirror mode.
After that, I run amdcccle and it allows me to set big desktop but selectable resolution is 3840x1080. 3840 is 1920*2 and both monitors get 1920x1080 which is correct for Acer, however everything in Samsung becomes slim and tall. I want it to be 1280x1024
[*]The settings don't persist. Upon restarting, it starts at a horrible low resolution, in the mirror mode. I observed that after beginning with a fresh ubuntu installation and some fiddling, system comes to a state that no matter what you modify at xorg.conf, it does not change its behaviour. Feel like some some other configuration just overrides it. (Maybe it is some ghosts or evil souls)     
[/LIST]

Here is my xorg.conf

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	SubSection "Display"
		Virtual   3200 1080
	EndSubSection
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


```

---

### Post by leventaksu on 2009-08-06
Talking to ATI guys revealed that there are problems getting BigDesktop to use different resolutions for different monitors. Xinerama works fine for the time being though compiz does not work with it.

---

