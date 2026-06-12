---
title: "Blank lines down sides on a Sony Bravia TV"
date: 2011-12-29
forum: Multimedia Software
---

### Post by ianxmorris on 2011-12-29
I am having problems with the display on my Sony Bravia TV via its monitor port.
 
The manual lists the avalable monitor modes as
 
1360 x 768 horizontal freq 47.7 vertical freq 60hz 
 
However it does not seem to pass EDID info so I have had to setup a xorg.conf manually. This works however I have unused bars on the screen down either side that I cannot seem to get rid off. 
 
When using windows it uses a res of 1366 x 768 and displays correctly without the bars at either side however I have been unable to get this working with Ubuntu 11.04.
 
My xorg.conf looks like this. Any ideas?
 
 Section "Monitor"
    Identifier      "External DVI"
    Modeline        "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 +hsync +vsync
    Option          "PreferredMode" "1360x768_60.00"
EndSection
Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
Section "Screen"
        Identifier      "Default Screen"
 Device   "Default Device"
        DefaultDepth    24
     SubSection "Display"
        Depth           24
        Modes   "1360x768"
    EndSubSection
EndSection
 
Thanks
 
Ian

---

