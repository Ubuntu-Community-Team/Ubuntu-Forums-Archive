---
title: "ATI refreshrate problems ? here's a partial solution"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by juve on 2006-11-11
Here's an excerpt from my xorg.conf including a (partial) solution for the "stuck at 85Hz" refreshrate problem:

```

###############################
# Welcome to ATI-Refresh-Hell #
############################### 
#  Problem 1 (since 8.25):
#        Have to use modelines because fglrx >= 8.25 can't go beyond 85 Hz
#        without them. DDC is probalbly broken
#
#  Problem 2 (since 8.30):
#        can't use this Section anymore. !!! (Problem 1 "solved")
#        using this Mode Section with my primary Monitor will stop Xorg from
#        loading, it shows a blank screen and i can't go back to tty1/2/3
#        i have to reboot in recovery mode afterwards and disable the Mode Section
#
#    Problem (general):
#        Can't use modelines for secondary Screen in BigDesktop mode
#        because you can't use a "Monitor" section for the second screen
#        you are rescricted to the HSync2 VRefresh2 values in the device Section
#        And they do not function as they should
#
#  partial solution:
#        **Use higher min-HorizSync Values in the Monitor Section**:
#        [COLOR=DarkRed]**HorizSync 30-98  -> 85 Hz is maximum**[/COLOR]
#        [COLOR=DarkOliveGreen]**HorizSync 70-98  -> 100 Hz is maximum**[/COLOR]
#        HorizSync 86-98  -> won't work, grrrr!!!
#
#    !!! Proprietary drivers SUCK !!!

Section "Modes"
    Identifier     "120Hz-only"
    ModeLine     "1024x768" 136.5 1024 1072 1312 1408 768 770 782 808
    ModeLine     "800x600" 86.0 800 840 1040 1120 600 602 614 640
    ModeLine     "640x480" 55.9 640 672 832 896 480 482 494 520
    ModeLine     "640x400" 47.3 640 672 832 896 400 402 414 440
    ModeLine     "320x240" 15.1 320 336 416 448 240 242 254 280
    ModeLine     "320x200" 12.9 320 336 416 448 200 202 214 240
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]"
#    UseModes     "120Hz-only"
    DisplaySize  361    271
    **HorizSync    70.0 - 98.0**
    VertRefresh  100.0 - 150.0
    Option        "DPMS"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]"
    BusID       "PCI:1:0:0"
    Driver        "fglrx"
    Option        "DesktopSetup" "Horizontal,reverse"
    Option        "PairModes" "1024x768+800x600"
    **Option        "HSync2" "60-70"**
    Option        "VRefresh2" "100-150"
    Option        "Mode2" "800x600"
EndSection
```If you use [COLOR=Red]8.30[/COLOR] then [COLOR=Red]don't use Modelines anymore[/COLOR] !! Use tweaked HSync2 and HorizSync instead. You will probably have to tweak the values for HSync2 and HorizSync a little bit until you find the right maximum "minimum-values". Modifing the  VertRefresh and VRefresh2 values won't help anything, they are probably ignored by fglrx.

If you use fglrx [COLOR=DarkOliveGreen]8.29[/COLOR] or less you [COLOR=DarkOliveGreen]can still use custom ModeLines[/COLOR] and force at least your primary display to 100Hz or more. (feature now disabled in my config above)

---

### Post by Icarosaurus on 2006-11-24
Thank you for your hints...now I can use 1152x864@100Hz.
HorizSync 86-98, works for me!
(I use fglrx 8.31.5)

```
Section "Monitor"
	Identifier   "F700P"
	#ModeLine     "1024x768@100" 124.8 1024 1088 1240 1528 768 768 771 817
	#ModeLine     "1152x864@100" 167.7 1152 1240 1448 1824 864 864 868 919
	HorizSync    86.0 - 98.0
        VertRefresh  50.0 - 160.0	
	Option	    "VendorName" "LG"
	Option	    "ModelName" "LG F700P"
	Option	    "DPMS" "true"
EndSection
```

But...when I try to change resolution with gnome, it hides 1024x768 and 800x600 even if they're specified in the "screen" section.
Maybe I have to restart the system, not only xorg? I'll let you know.
For istance, my Monitor is an LG F770P capable of 1152x864@100Hz and 1600x1200@75Hz.

---

### Post by desudesudesu on 2007-06-24
Damnit wrong tab.

Can a mod delete this post?

---

### Post by Icarosaurus on 2008-01-20
Finally ATI gave us a decent refresh rate support !
Catalyst 8-1 drivers support custom modelines, but they were no more necessary cause I could set 1024x768@100Hz  on gnome. :)

---

### Post by Toadmund on 2008-01-27
Ahem...Excuse me for butting in.
Earlier today I could not set my refresh rate to 70Hz, 60Hz drives me nuts!
So I spent the day in video graphics/driver hell!

Back to square one, stuck at 60Hz (very productive day, Not!) :mad:

So, how do I edit this to give me an option to get 70Hz in my screens and graphics GUI?
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1024x768@60"	"1024x768@43"	"1024x768@70"	"1152x864@75"	"1024x768@75"	"1280x960@60"	"1024x768@85"	"1280x1024@60"	"832x624@75"	"1400x1050@60"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
```


Thanks.

PS, 1024x768@70 is what I want, what if I just deleted everything else that is 1024x768 in 'Modes'?

---

### Post by Toadmund on 2008-01-28
Never mind, I just manually downloaded the ATI driver instead of using envy, I reset my xorg and everything works now.

---

