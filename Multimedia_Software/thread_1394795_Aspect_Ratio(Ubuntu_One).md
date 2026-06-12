---
title: "Aspect Ratio(Ubuntu One)"
date: 2010-01-31
forum: Multimedia Software
---

### Post by linkingeek on 2010-01-31
I have used Ubuntu 9.04 and never faced any problems in-spite i m new to linux ,First interaction of user is with his desktop but version 9.10 detects my monitor for 4:3 display and i use 5:4 monitor therefore aspect ratio is not correct is there anyway to manually adjust the ratio.
"Display Preferences " only shows 4:3 displays and incorrect monitor refresh rate?
I have not observed any xorg.conf file to etc/X11/ therefore i cannot expect creating new config file for xorg will effect, Anyhow i created one
Following [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
"xorg.conf" as(but vain)-

> Section "Monitor"
    Identifier      "External DVI"
    Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    Option          "PreferredMode" "1280x1024_60.00"
EndSection
Section "Device"
    Identifier      "Intel Corporation 82G33/G31 Express Integrated Graphics"
    Driver          "intel"
    Option          "Monitor-DVI-0" "External DVI"
EndSection
Section "Screen"
    Identifier      "Primary Screen"
    Device          "Intel Corporation 82G33/G31 Express Integrated Graphics"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Primary Screen"
EndSection  __________________________________________________________________________
_System_
-Core2duo 2.2Ghz
-Ubuntu on  seperate disk,installed with Wubi
-2GB Ram
-intel graphics chipset(no graphics card)
-intel g33 motherboard

---

