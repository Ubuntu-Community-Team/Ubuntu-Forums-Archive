---
title: "Refresh setting driving me mad :("
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by colinw on 2006-07-15
I done a clean install of ubuntu 6.06 on my main pc, then got all the updates, then installed automatix and selected most things. I have an nvidia 6800gt so i installed the nvidia drivers in automatix. So when i next load up linux i now have a screen mode of 1024x768 at 75hz.

My objective is to have 1280x1024 at 60hz as i have a 17" tft

I found the modeline generator and added the details to the xorg.conf as below.

Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

So now it's in 1280x1024 screen mode, but still at 75hz ?

I need it to be set at 60hz, what am i doing wrong, thanks

---

