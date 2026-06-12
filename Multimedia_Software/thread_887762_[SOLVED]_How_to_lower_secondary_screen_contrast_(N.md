---
title: "[SOLVED] How to lower secondary screen contrast (Nvidia)"
date: 2008-08-12
forum: Multimedia Software
---

### Post by Ux64 on 2008-08-12
I have two X Screens and I'm using Xinerama config.

But I'm unable to set contrast for secondary screen. I wonder how that can be done.

I think I have tried everything, but I still fail. And usually get error like:

```

ERROR: Invalid X Screen 1 specified on line 57 of configuration file
       '.nvidia-settings-rc' (there is only 1 X Screen on this
       Display).

```

What I should specify on that line? Old line started with 0 so I added contrast configuration with prefix 1.

Here is my Nvidia-Settings configuration screen:
[http://img139.imageshack.us/my.php?image=settingsoi2.png](http://img139.imageshack.us/my.php?image=settingsoi2.png)

TV-0 is the screen #1 and I should lower contrast by something like 10%.

I tried it using row:

```
1/RedContrast=-0.100000
1/GreenContrast=-0.100000
1/BlueContrast=-0.100000

```

Ubuntu Hardy Heron 64 bit. Nvidia 8500GT. I have now everything working, except that display adapter is using by default too much contrast.

---

### Post by Ux64 on 2008-08-13
xorg important parts:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 1600 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Generic CRT Display"
    ModelName      "Monitor 1600x1200"
    HorizSync       31.5 - 107.5
    VertRefresh     50.0 - 85.0
    Gamma           1
    ModeLine       "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    Option         "DPMS"
    Option         "OffTime" "5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "FUS P20-2"
    HorizSync       30.0 - 82.0
    VertRefresh     51.0 - 75.0
    Option         "DPMS"
    Option         "OffTime" "5"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 82.0
    VertRefresh     51.0 - 75.0
    Option         "DPMS"
    Option         "OffTime" "5"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8500 GT]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8500 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     3520 1200
        Depth       24
        Modes      "1600x1200@75"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "TV: 1920x1080 +1600+0, DFP: 1600x1200 +0+0"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TVStandard" "HD1080i"
    Option         "TVOutFormat" "COMPONENT"
    Option         "UseDisplayDevice" "TV"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 1920x1080 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: 1600x1200 +0+0"
EndSection

```

---

### Post by Ux64 on 2008-10-02
I disabled Xinerama now I got contrast issue solved. It wasn't simply possible to set OUTPUT contrast, which sucks. It would require using separate screen. But now I got range of new issues. 

A) First how I best use two different work spaces?

It seems to be bit funny arragement. It's not one work space, and it isn't either completely two different work spaces.

I would like to solve this issue. I would be nice to have two completely different work spaces. Allowing different users to be logged on. Using their own controls.

B) UI is just darn slow on screen 0, opening drop down menus or any new windows takes about 2 seconds. Which is SLOW! If I open that font selection drop down menu on this window, it'll take two seconds to open up. Or font size window or any other window. I wonder what is causing this issue. Too slow display adapter, I don't think so? Bad drivers or some bug in UI code? Maybe? Dunno. You tell me. But the problem is very clear.

C) Tearing issue hasn't been ever solved. It seems that VLC Xvideo and Nvidia controllers can't properly output synchronized video image. Unfortunately. 

D) 8500GT doesn't support non-interlaced full hd. In some cases this causes very bad interlace effects... But in most of cases it's not a problem.

Phew. Still some problems to be solved.

Btw. It was required to drasticly lower color levels on TV. New televisions just got too bright colors.

---

