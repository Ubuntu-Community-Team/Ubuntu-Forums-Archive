---
title: "[SOLVED] Only 2 monitors detected on 4850 X2"
date: 2008-12-15
forum: Multimedia Software
---

### Post by Mattventura on 2008-12-15
I recently got a 4850 X2 and three monitors. The 4850 X2 has 4 DVI outputs. CCC and other tools only seem to detect one card and therefore only see 2 monitors. Is there a way to make it detect monitors plugged in to the other side? (Any monitor plugged in the the left side works but not on the right).

This is on Intrepid 64 bit. I have also tried manually writing an xorg.conf, but whenever I try to configure the second GPU (on the same card) the X server will not start. Any suggestions? Could this be crossfire related? (The card AFAIK can internally connect its 2 GPUs in crossfire mode).

More info:
Card: Sapphire 4850 X2
Relevant lines from lspci:
07:00.0 VGA compatible controller: ATI Technologies Inc Device 9443
08:00.0 Display controller: ATI Technologies Inc Device 9443
package "xorg-driver-fglrx" is version 2:8.543-0ubuntu4

---

### Post by locksley on 2008-12-17
Well I dont have answer unfortunately;

However i am having exactly the same problem with 2 4850's but single GPU. They are also on a board with an onboard 3300. 

The strange thing is because i have specific PCI addresses for each card. I can can check that they are all working and low and behold each one independently works fine. 

With one caveat i do not see two desktops for each card rather one large desktop that includes both monitors that are connected to the card currently configured? This may be normal for ATI (im usually an Nvidia guy, you always see two desktops)

I will update this post if i find anything.

---

### Post by Mattventura on 2008-12-18
I initially tried to do my xorg.conf entirely by hand as I have done for my previous dual-head setup, but that proved problematic with a triple-head on one card. 

Anyway, I got this issue fixed, but now my issue is that the left monitor and the right two function as different displahs, so I cannot drag windows between the left one and the other two. Enabling Xinerama breaks the layout completely. My xorg.conf looks like this:

```

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[7]-0" 1680 0
	Screen         "amdcccle-Screen[7]-2" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[7]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[7]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[7]-2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[7]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection
Section "Device"
	Identifier  "amdcccle-Device[7]-0"
	Driver      "fglrx"
	Option	    "EnableMonitor" "crt1,lvds,tv,tmds1,crt2,tmds2,cv,tmds2i"
	BusID       "PCI:7:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[7]-1"
	Driver      "fglrx"
	BusID       "PCI:7:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[7]-2"
	Driver      "fglrx"
	BusID       "PCI:8:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[7]-1"
	Driver      "fglrx"
	BusID       "PCI:7:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[7]-0"
	Device     "amdcccle-Device[7]-0"
	Monitor    "amdcccle-Monitor[7]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[7]-1"
	Device     "amdcccle-Device[7]-1"
	Monitor    "amdcccle-Monitor[7]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[7]-2"
	Device     "amdcccle-Device[7]-2"
	Monitor    "amdcccle-Monitor[7]-2"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[7]-1"
	Device     "amdcccle-Device[7]-1"
	Monitor    "amdcccle-Monitor[7]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection



```

---

### Post by locksley on 2009-02-05
Well still here,

I have now got all monitors working but alas as separate screens. Ati;s drivers suck. I tried the new 9.1 today and have spent the entire day trying to get them running, with no luck.

Anyone got any ideas?

This is a pain as i spend most of my time in Vista only because i cant get this going :(

System/Problem

Onboard RadeonHD 3300 dual head 
1 X DVI 
1 X HDMI (i dont currently use)

Dual 4850's (so 2 individual 4850 cards 1G)
2 X DVI
2 X DVI

I run 5 monitors (Its a dual boot with Vista, everything works in vista)

As soon as i can get all 5 running as one big monitor which i have done in the past with an older system (no crazy ATI BS) i shed Vista.

As mentioned currently running Ubuntu 8.1 X64 and getting very frustrated.

Any help greatly appreciated, even if it is use other drives / what ever.

---

### Post by Mattventura on 2009-02-09
I am actually running a 5 monitor setup now. The way you can get it working is by using the "aticonfig" program. What I did for 4 monitors (one is driven by an nvidia card) is this:

```
aticonfig -f --initial=dual-head --adapter=0
aticonfig --initial=dual-head --adapter=1
```

and so for you, assuming that the card with one monitor is the last card,

```
aticonfig --initial --adapter=2
```

Now, in order to be able to configure the cards in the CCC, change everything in xorg.conf that says "aticonfig" to "amdccc" or whatever it is supposed to be (just check what CCC puts in for everything before you do aticonfig).

Edit: search for posts by me to find out my Xinerama issues. This might get your setup working, just not exactly the way you expected.

---

