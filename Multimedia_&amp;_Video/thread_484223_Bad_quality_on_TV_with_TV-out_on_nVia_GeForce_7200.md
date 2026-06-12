---
title: "Bad quality on TV with TV-out on nVia GeForce 7200 GS"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by westis on 2007-06-25
Hi,

I've managed to get a picture out through my nVidia GeForce 7200 GS PCI-express card to a TV. But the quality on the TV is really bad... Also it doesn't display the full width, as if the 1.067 pixel ratio is changed to square pixels when playing mpeg-2 files.

I installed the nVidia driver though Envy.

I connect through S-video with a converter to RCA.  An mpeg-2-card through s-video out on the same computer, but in Windows, works perfectly. 

Here's the relevant (?) part of xorg.conf:

```
Section "Monitor"
    Identifier     "Monitor[0]"
    HorizSync       31.5 - 82.0
    VertRefresh     50.0 - 90.0
EndSection

Section "Device"
    Identifier "Device[0]"
    Driver "nvidia"
    Option "TwinView"
    Option "SecondMonitorHorizSync"   	"30-50"
    Option "SecondMonitorVertRefresh" 	"60"
    Option "TwinViewOrientation"      	"Clone"
    Option "MetaModes" "1280x1024,1280,1024; 1024x768,1024x768; 800x600,800x600"
    #Option "MetaModes" "800x600,800x600"
    #Option "MetaModes" "800x600,720x576"
    Option "TVOutFormat" "SVIDEO"
    #Option "TVOutFormat" "COMPOSITE"
    Option "TVStandard" "PAL-B"
    Option "ConnectedMonitor" "CRT,TV"
    BusID  "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Viewport    0 0
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

I'm using Ubuntu Feisy and tried this with Totem (gstreamer) and VLC, with same result.

Would be really grateful for assistance!

Thanks,
Daniel

---

