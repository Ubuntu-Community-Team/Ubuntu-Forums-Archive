---
title: "manual setting of xorg.config"
date: 2009-09-18
forum: Multimedia Software
---

### Post by jorgemarmo on 2009-09-18
hey guys, I need some help here, I get a Samsung P2070 LCD monitor and when I plug it on the DVI of my GeFroce4 MX420 (running jackalope), it shrink, it's continiously blinking.... On WinXP I had to set a "custom timing" to CVT-RB to make it work... now on the linux nvidia control panel that option is not there, so I check a lot of forums and I beleive to understand that I have to manually set this on the xorg.conf file, anyone can help me?

*these are my monitor espec*
 General
Model Name
**SyncMaster P2070**, P2070G
LCD Panel
Size
20 inch (49 cm)
Display area
422.8 mm (H) x 249.08 mm (V)
Pixel Pitch
0.2768 mm (H) x 0.2768 mm (V)
[B]Synchronization
Horizontal
30 ~ 81 kHz
Vertical
56 ~ 60 Hz
Display Color
16.7 M
Resolution
Optimum resolution
1600x900@60Hz
Maximum resolution
1600x900@60Hz[/B]
Input Signal, Terminated
DVI(Digital Visual Interface)- I
0.7 Vp-p ±5 %
Separate H/V sync, Composite, SOG
TTL level (V high &#8805; 2.0 V, V low &#8804; 0.8 V)
[B]Maximum Pixel Clock
108MHz (Analog,Digital)[/B]
Power Supply
AC 100 - 240 V~ (+/- 10 %), 50/60 Hz ± 3 Hz
Signal Cable
29pin DVI-A to D-sub cable, Detachable
24pin DVI-D to DVI-D cable, Detachable(Sold separately)
Dimensions (W x H x D) / Weight (Simple Stand)
500 x 325 x 47 mm ( 19.7 x 12.8 x 1.9 inch) (Without Stand)
500 x 382 x 190 mm (19.7 x 15.0 x 7.5 inch) (With Stand) / 3.3 kg (7.3 Ibs)
Environmental considerations
Operating
Temperature : 50&#730;F ~ 104&#730;F (10&#730;C ~ 40&#730;C)
Humidity : 10 % ~ 80 %, non-condensing
Storage
Temperature : -4&#730;F ~ 113&#730;F (-20&#730;C ~ 45&#730;C)
Humidity : 5 % ~ 95 %, non-condensing
Plug and Play Capability
This monitor can be installed on any Plug & Play compatible system. The interaction of the monitor and the computer systems will provide the best operating conditions and monitor settings. In most cases, the monitor installation will proceed automatically, unless the user wishes to select alternate settings.
Dot Acceptable
TFT-LCD panels manufactured by using advanced semiconductor technology with precision of 1ppm (one millionth) above are used for this product. But the pixels of RED, GREEN, BLUE and WHITE color appear to be bright sometimes or some black pixels may be seen. This is not from bad quality and you can use it without any problems.
For example, the number of TFT-LCD sub pixels contained in this product are 4,320,000.
//
[B]Display Mode
VESA, 1600 X 900
Horizontal Frequency (kHz)
60.000
Vertical Frequency (Hz)
60.000
Pixel Clock (MHz)
108.000
Sync Polarity (H/V)
+/+[/B]


I found this one very usefull [http://ubuntuforums.org/showthread.php?t=1053040](http://ubuntuforums.org/showthread.php?t=1053040)

This is my xorg.conf file
######
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
#####

---

