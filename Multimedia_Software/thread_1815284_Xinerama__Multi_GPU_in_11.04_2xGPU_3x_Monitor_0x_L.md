---
title: "Xinerama / Multi GPU in 11.04 2xGPU 3x Monitor 0x Luck (except Twinview) -"
date: 2011-07-31
forum: Multimedia Software
---

### Post by bemused0 on 2011-07-31
I know there are many multi-monitor posts out there. I've been reading them, for a couple of hours hours. (and, oh, the searching I have done)  

Setup: 2x 450GTS 1G SLI 
3Xmonitors

Has anyone had any luck on 11.04 in a xinerama setup with 2x Nvidia GPU's?

I've tried on the 270.x and 275.x drivers without luck.

I HAVE gotten Twinview + Separate X (for the 3rd monitor) working, but with problems.

I am unable to get xinerama working on 2, or 3 monitors.
Each time I get a black screen + background (or 2 black screens and a background).  Interaction is offset by 1 or 2 screens, depending -- eg I click on the left screen, menu displays on the right (left being black, right being 'on') etc.

-Setting Option "SLI" "On" 
causes the server to run on 1 monitor only (or not at all, depending on the xinerama setting)

-Setting multigpu "On" doesn't seem to help either.

```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    ModelName      "Ancor Communications Inc VE245"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection


Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    ModelName      "Ancor Communications Inc VE245"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    ModelName      "Ancor Communications Inc VE245"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 450"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 450"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 450"
    BusID          "PCI:4:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

Pretty simple X config, trying to keep it as basic as possible now.

If anyone has any ideas or if you've got something similar working, please reply.

Thanks!
-bem:popcorn:

---

### Post by bemused0 on 2011-07-31
Solved by disabling effects (compiz?) or by using kde, also re-arranged the layout.
Card 0 - Center Monitor
Card 1 - Left / Right monitors
(Why 2 and 1 from left to right wouldn't work, I have no idea)


Compiz and xinerama don't play, obviously and apparently I had completely forgotten this; it's been a while. That whole XgL thing died years ago right? 

Gibberish aside, the following xorg.conf worked out for Gnome ( Ubuntu Classic - No effects) and KDE

```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1920 0
    Screen      1  "Screen1" LeftOf "Screen0"
    Screen      2  "Screen2" 3840 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Ancor Communications Inc VE245"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Ancor Communications Inc VE245"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Ancor Communications Inc VE245"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 450"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 450"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 450"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-2: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

:) -- For the moment -


Now I need to figure out how to get 3 monitors working with compiz / xrandr (which I'm reading has replaced xinerama? oh I feel rusty)

This pretty much sums up the frustration:
[http://superuser.com/questions/55845/triple-3-monitors-under-linux](http://superuser.com/questions/55845/triple-3-monitors-under-linux)

---

