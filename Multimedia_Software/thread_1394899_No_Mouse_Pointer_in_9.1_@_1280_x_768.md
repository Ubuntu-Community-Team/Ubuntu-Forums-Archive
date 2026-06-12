---
title: "No Mouse Pointer in 9.1 @ 1280 x 768"
date: 2010-01-31
forum: Multimedia Software
---

### Post by Shinken69 on 2010-01-31
Hi,
I just installed Ubuntu 9.1 on my Dell Dimension 2400.
Everything worked fine once I found the appropriate boot settings.
However, I use a Sony 32" LCD as my monitor.
When I change the resolution to the native 1280 X 768 (my previous XP setting), the mouse pointer disappears never to return.
The mouse is still working, I just can't see the pointer.
I have enabled the "Show pointer when control key is pressed" feature in the mouse settings.
This works and is the only way the system is usable.
Any ideas????

---

### Post by gnepets on 2010-01-31
> **Shinken69 said:**
> Hi,
I just installed Ubuntu 9.1 on my Dell Dimension 2400.
Everything worked fine once I found the appropriate boot settings.
However, I use a Sony 32" LCD as my monitor.
When I change the resolution to the native 1280 X 768 (my previous XP setting), the mouse pointer disappears never to return.
The mouse is still working, I just can't see the pointer.
I have enabled the "Show pointer when control key is pressed" feature in the mouse settings.
This works and is the only way the system is usable.
Any ideas????

I have the same problem at 1920 x 1080 since last reboot. I found the same when control clicked thing.

I am going to find a bug and try to report this. guh.

---

### Post by Shinken69 on 2010-01-31
Bizarrely, the mouse reappears if I run BBC iPlayer?????????????:confused:

---

### Post by 02ak on 2010-03-08
same problem with 1366 x 768 HP Pavilion dv6 1199ee 

i installed ubuntu updated + installed kde then restarted and mouse pointer got boom, tried customising appearance. 

here is my xorg

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

### Post by _nikolaos on 2010-03-23
Same here.
Just installed my video card driver.
Mouse works, but no cursor appears.

---

