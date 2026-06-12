---
title: "Optimizing video playback"
date: 2010-01-09
forum: Multimedia Software
---

### Post by jbraveman on 2010-01-09
I am running ubuntu 9.04 64 bit with the following hardware:
[INDENT]Foxconn A7GM-S AM2+/AM2 AMD 780G HDMI Micro ATX AMD Motherboard
Onboard video - ATI Radeon HD 3200
4 gigs ram
AMD Athlon 64 X2 5000 Brisbane 2.6GHz 2 x 512KB L2 Cache Socket AM2 65W Dual-Core Processor
[/INDENT]
I am using a Panasonic TH-37PD24 plasma as the primary monitor pretty much exclusively for video playback using movie player of handbrake ripped movies (mkw format).

I am not certain how to incorporate my specific monitor settings into my xorg.conf file to optimize the display.

Here is my xorg.conf file:
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
	BusID       "PCI:1:5:0"
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

I am inputting the video via the HDMI input.  From the TV's manual, these are the supported resolutions/frequency:

[http://service.us.panasonic.com/opermanpdf/TH37PD25.pdf](http://service.us.panasonic.com/opermanpdf/TH37PD25.pdf) (page 66)

                      horiz vert  Component/PC/HDMI   
1   525 (480) /60i    15.73 59.94   &#8727;       &#8727;    &#8727;
2   525 (480) /60p    31.47 59.94   &#8727;       &#8727;    &#8727;
3   750 (720) /60p    45.00 60.00   &#8727;
4   1,125 (1,080)/60i 33.75 59.94   &#8727;       &#8727;    &#8727;
5   640 × 400 @70     31.47 70.00   &#8727;
6   640 × 480 @60     31.47 59.94   &#8727;
7   Macintosh13&#8221; (640 × 480) 35.00 66.67 &#8727;
8   640 × 480 @75     37.50 75.00   &#8727;
9   852 × 480 @60     31.50 60.00   &#8727;
10   800 × 600 @60    37.88 60.32   &#8727;
11   800 × 600 @75    46.88 75.00   &#8727;
12   800 × 600 @85    53.67 85.06   &#8727;
13   Macintosh16&#8221; (832 × 624) 49.73 74.55 &#8727;
14   1,024 × 768 @60  48.36 60.00   &#8727;
15   1,024 × 768 @70  56.48 70.07   &#8727;
16   1,024 × 768 @75  60.02 75.03   &#8727;
17   1,024 × 768 @85  68.68 85.00   &#8727;
18   Macintosh21&#8221; (1,152 × 870) 68.68 75.06 &#8727;
19   1,280 × 1,024 @60 63.98 60.02  &#8727;
20   1,280 × 1,024 @75 79.98 75.03  &#8727;
21   1,280 × 1,024 @85 91.15 85.02  &#8727;
22   1,600 × 1,200 @60 75.00 60.00  &#8727;

It would seem that Numbers 1,2, and 4 are the only values applicable to the HDMI input.

My first attempt at messing around with xorg.conf file and using the open-source ATI drivers resulted in the computer hanging during startup.  I've got everything back to where it was using the proprietary flgrx driver.

The video playback is currently pretty good.  However, it is choppy at times during fast action scenes. All the videos are located locally on internal sata drives.  I don't do anything else with this machine except for some file/music serving (no games).  All the desktop effects are turned off.  I'd like to optimize the video playback as much as possible.

My questions are:
1) How to appropriately edit my xorg.conf
2) Are there any other tweaks that might help video performance
3) Would getting a dedicated video card be best.  If so, which one.

Thanks for your help.

---

### Post by jbraveman on 2010-01-10
I figured out how to use the CVT command and updated my xorg.conf file:

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
	Identifier   "Panasonic Plasma"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
	Option          "PreferredMode" "1920x1080_60.00"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "Panasonic Plasma"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1920x1080"
	EndSubSection
EndSection

```

Display preferences still shows the refresh rate at 30hz. The resolution is 1920 by 1080. I still suspect something is not quite right.  Am I heading in the right direction?

Thanks.

---

