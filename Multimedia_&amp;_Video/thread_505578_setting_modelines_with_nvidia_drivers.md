---
title: "setting modelines with nvidia drivers"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by Natakou on 2007-07-20
I installed ubuntu 7.04 and am currently using the nvidia drivers and am having trouble setting modelines. the nvidiaglx and the default driver don't work, xwindows crashes whenever i try to use them. xvidtune doesn't work either, error states current modeline is not supported on anything i choose, so i was trying to set modelines by narrowing in xvidtune showing the output and lots of trial and error.

> Section "Monitor"
    Identifier     "Samsung"
    Option         "DPMS"
#    Option        "IgnoreEDID"
    ModeLine       "1920x1080"   148.35   1920 2008 2056 2224   1080 1084 1089 1125 +hsync +vsync
#    ModeLine       "1768x992_60"  145.42  1768 1872 2064 2360  992 993 996 102$
EndSection

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7300 GS]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7300 GS]"
    Monitor        "Samsung"
    DefaultDepth    24
#    Option        "UseEdidFreqs" "true"
#    Option        "ModeValidation" "NoMaxPCIkCheck, AllowNon60HzDFPModes, NoVe$
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080"
    EndSubSection
EndSection



Are there any programs that can facilitate the install of modelines or fixing overscan that im not using?

---

