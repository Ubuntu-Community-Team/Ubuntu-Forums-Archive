---
title: "Playing a DVD on TV-out"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by Theeboon on 2007-04-09
I got my Nvidia card (GeForce2 MX440) to work with my TV. Whenever I switch to 800x600, my TV switches to 720x576.

> Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "TwinView" "True"
        Option          "TwinViewOrientation" "Clone"
        Option          "TVOutFormat" "COMPOSITE"
        Option          "TVStandard" "PAL-B"
        Option          "SecondMonitorHorizSync" "30-50"
        Option          "SecondMonitorVertRefresh" "60"
        Option          "MetaModes" "1280x1024,800x600;1024x768,800x600;800x600,720x576;640x480,640x480"
        Option          "ConnectedMonitor" "CRT,TV"
EndSection

This however isn't that great. When I play a DVD with Kaffeine and switch to fullscreen, I lose part of the image on the left and right side of the screen. When I put the TV output resolution to 800x600 I get small black bars on both sides of the screen.

Is there any way to eliminate the image loss/black bars?

---

