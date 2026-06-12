---
title: "Is my video properly configured?"
date: 2009-07-14
forum: Multimedia Software
---

### Post by geofffox on 2009-07-14
I have a Xubuntu 9.04 installation on this IBM PC with Intel i865g video.  Everything works reasonably well, but I am suspicious the video isn't properly implemented.

Any time I reboot the display (1280x1024) reverts to 1440x900.  When I check xorg.conf is functionally empty:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


Am I OK but too cautious or is this less than fully configured?

Thanks.

---

### Post by kerry_s on 2009-07-14
that means your screens native resolution is 1440x900.

---

### Post by geofffox on 2009-07-14
It thinks it is--but it is not.  This is a 19" 'old school' LCD.  It is natively 1280x1024.  That's part of the reason I suspect something is up... or maybe not up.

---

### Post by kerry_s on 2009-07-14
give the monitor info & i'll look up the specs just to be sure.

---

### Post by geofffox on 2009-07-14
Product Name  	PL1910M
Planar Part Number 	997-2797-00 (Black)
Viewable Size 	19" diagonal (14.81" horizontal x 11.85" vertical)
Aspect Ratio 	4:3
Contrast Ratio (Typical) 	1000:1
Viewing Angle (Typical) 	160° H,V (specified at CR>10:1)
Response Time (Typical) 	5 ms
Brightness (Typical) 	300 cd/m²
Display Type 	LCD Active Matrix Flat Panel Display (TFT)
Display Resolution 	SXGA (1280 x 1024), XGA (1024 x 768), SVGA (800 x 600), VGA (640 x 480), and others

---

### Post by kerry_s on 2009-07-14
alright, press-> **alt-f2**
type-> **gksudo gedit /etc/X11/xorg.conf**
put:

```

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
[B]SubSection "Display"
Modes "1280x1024" 
EndSubSection[/B]
EndSection



```

---

### Post by geofffox on 2009-07-14
OK --

I need no specific driver or configuration for this Intel i865g video?

---

### Post by kerry_s on 2009-07-14
> **geofffox said:**
> OK --

I need no specific driver or configuration for this Intel i865g video?

i'm not sure what you mean? the only thing wrong was the screen size right? 
check your /var/log/Xorg.0.log it should already be loading the intel driver.

there are also tweaks for the intel driver, that might improve performance. i haven't tried any myself, i have:
```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```

---

### Post by geofffox on 2009-07-14
This is the last complete cycle in the log.  Everything that's initialized is then removed.  The resolution change you suggested I make isn't here as I haven't reinitialized the Xserver.

(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "AVO", prod id 4112
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0  108.00  1440 1520 1672 1904  900 903 909 934 +hsync +vsync (56.7 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.00  1680 1784 1960 2240  1050 1053 1059 1089 +hsync +vsync (65.2 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz)
(II) intel(0): Modeline "1600x1200"x0.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (93.8 kHz)
(II) intel(0): Modeline "1360x765"x60.0   84.39  1360 1424 1568 1776  765 766 769 792 -hsync +vsync (47.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) intel(0): Modeline "848x477"x60.0   31.30  848 864 952 1056  477 478 481 494 -hsync +vsync (29.6 kHz)
(II) intel(0): Modeline "1920x1200"x0.0  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync (74.6 kHz)
(II) intel(0): Modeline "1920x1440"x0.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) intel(0): EDID vendor "AVO", prod id 4112

---

### Post by kerry_s on 2009-07-14
yeah, you should try some of the other tweaks, just google it. mines the i915 so my settings might be different from yours, i'm also using debian testing, not ubuntu.

i just tweaked mine, first i googled for tips, than i checked the log, to see if it was on or off in the log, then made the tweaks & checked the log to see if they was used, some say "not used" so i did away with those tweaks.

anyways heres what i ended up with on mine.

---

