---
title: "Dual monitors, nvidia and wine."
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by hampton275 on 2007-12-01
Ok, it was a toss up whether this was a gaming or video question, so I went with video.

Firstly, other than this one app X works great.

I have an Nvidia GeForce 6800. After installing Diablo 2 under wine (which went without a problem), I attempt to run the game. I receive an "error 22" which I find out means I don't have a low enough video mode available in X(it needs 640x480 or 800x600). Fair enough. After checking around I realized something. Xorg adds the reolution for both monitors together. Very weird. 
Anyway, I managed to get the resolution to 800x600 but setting a metamode to shut off one monitor and drop the res on the other one to 800x600, which is what Diablo 2 supports, only I am still receiving the error???

Here is the output from xrandr:
$ xrandr 
Screen 0: minimum 800 x 600, current 3360 x 1050, maximum 3360 x 1050
default connected 3360x1050+0+0 0mm x 0mm
   3360x1050      50.0* 
   1600x600       51.0  
   800x600        52.0  

Relevant portion of my xorg.conf:
Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 64.0
    VertRefresh     0.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7800 GTX"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewOrientation" "LeftOf"
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1680+0; DFP-0: 800x600 +0+0, DFP-1: 800x600 +800+0; DFP-0: 800x600 +0+0, DFP-1: NULL"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

I would really appreciate any suggestions or ideas that might help me out with this. If there is any other data needed, just ask

TIA :)

---

