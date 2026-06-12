---
title: "Problem with Samsung LE32A457 and ati"
date: 2009-02-08
forum: Multimedia Software
---

### Post by fonsocm on 2009-02-08
Hi.

I'm trying to configure my PC with Ubuntu to play videos in my tv: Samsung LE32A457.

My video card is ATI3600 and I am using the last proprietary drivers of ati.

My problem is: my tv is HD Ready but it only gives 24 playback using 1920x1080. However, when I select this resolution the desktop doesn't fill all the screen, the desktop is in the center of screen with black borders all around.

I use to configure xorg.conf aticonfig, the configuration is a dual head view, the tv is the second screen.

I tried the tips in the mythv modeline database web page without sucess.

Can some help me, please?

Thanks in advance.

My xorg.conf is:

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
 Modeline    "1920x1080" 74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-1"
        Driver      "fglrx"
        Option      "Centermode" "off"
        Option      "TVOverscan" "off"
        BusID       "PCI:1:0:0"
        Screen      1
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

Section "Screen"
        Identifier "aticonfig-Screen[0]-1"
        Device     "aticonfig-Device[0]-1"
        Monitor    "aticonfig-Monitor[0]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes     "1920x1080"
        EndSubSection
EndSection

---

