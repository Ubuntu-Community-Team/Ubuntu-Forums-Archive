---
title: "Refresh Rate Issues with ATI Card and 9.04"
date: 2009-05-01
forum: Multimedia Software
---

### Post by shad0w99 on 2009-05-01
Hi guys!

I hope this is the right part of the forum to be posting in.. I figured either here or the hardware section would be the right place. But I reckon this is a software issue.

I have an LG Flatron F900P 19" Monitor (It's a CRT monitor). I run 1280 x 1024 and at that resolution it's capable of 100Hz Refresh Rate. However in Ubuntu it's stuck at 60Hz with no way to change it in the display or ATI Catalyst Control Center

I'm a relative noob to Ubuntu and Linux in general. I've been Googling around for 2 days straight now and I've tried almost everything to solve. I've tried adding modelines to xorg.conf and setting the HSync and Vsync there manually. I've also tried doing that via the aticonfig tool but to no avail.

In the standard Ubuntu display options my monitor is listed as Unknown. Is that maybe the issue? If so, how do I make Ubuntu detect my monitor properly.

I could really use some help on this issue. The new version of Ubuntu seems great but if I can't solve this issue I'm not going to be using it simply because I'll end up damaging my eyes or something haha.

Thanks in advance

---

### Post by CatKiller on 2009-05-01
I found that my monitor was reporting incorrect EDID information. Setting the HorizSync and VertRefresh correctly got me the correct resolution, but I needed to set ```
Option     "UseEDID"     "False"
``` in the "Device" Section to get the maximum refresh rate.

---

### Post by Legace on 2009-05-01
Add something like this:
(NOTE! use values for your monitor)

```
Section "Monitor"
...
    HorizSync     31-101
    VertRefresh    60-160
...
EndSection
```
```

Section "Screen"
...
    SubSection "Display"
        Depth        24
        Modes      "1280x1024_100.00"
    EndSubSection
...
EndSection
```


(if this or the above post doesn't help:
do you have Windows installed on that machine?)

---

### Post by shad0w99 on 2009-05-01
Thanks a lot for the help guys but unfortunately neither of those did the trick :-(

Here's how my xorg.conf looks currently

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	HorizSync    30.0 - 111.0
	VertRefresh  50.0 - 160.0
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseEDID" "False"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
                Depth      24
                Modes      "1280x1024_100.00"
	EndSubSection
EndSection
```

I don't know if that helps isolate the problem at all but I figure it can't hurt.

---

### Post by CatKiller on 2009-05-02
Bleurgh. I hate the way that NVidia's and Ati's configuration programs mangle xorg.conf. They make them look so ugly.

Anyway, you don't need the spaces in your HorizSync and VertRefresh lines. 30-111 and 50-160 should do. /var/log/Xorg.0.log is the log file for X. You can view it with ```
less /var/log/Xorg.0.log
``` (PageUp & PageDown do the obvious, q to quit less) You should be able to find the reason in there for why a particular mode isn't being chosen. If this still doesn't give you enough information, you can use ```
     Option     "ModeDebug"     "True"
``` in the "Device" Section to give you even more information.

---

