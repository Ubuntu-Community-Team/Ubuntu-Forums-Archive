---
title: "[SOLVED] DEll 1704FPT monitor  resolution issues"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by markbann on 2008-01-07
New installation ubuntu 7.10
video card PNY GEForce TI 4600 with default nv drivers

I changed monitors to a Dell 1704FPT  17" flat panel, but cannot get resultion over 800x600.
Ubuntu detects the monitor just fine but either won't display other resolutions or if it does it will fail video tests on restart and not display a higher resolution.  I tried running:
sudo dpkg-reconfigure xserver-xorg
but on restart the settings failed and it reverted to 800x600.
I am a newbie, but I did a good bit of searching.  Nothing I found so far seems to be helping.
This appears to be the entry for the dell monitor inxorg.conf but none of the listed resoltions show up in the system/screen & graphics program:

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Dell"
	Modelname	"Dell 1704FPT (Digital)"
	Horizsync	30.0-81.0
	Vertrefresh	56.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Any help would be appreciated.  Thanks

---

### Post by markbann on 2008-01-09
Would installing the correct nvidia driver help?

---

### Post by markbann on 2008-01-09
> **markbann said:**
> Would installing the correct nvidia driver help?

I used Envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) to add the correct nvidia drivers and that fixed the problem.

---

