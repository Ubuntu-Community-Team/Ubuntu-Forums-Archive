---
title: "Multiple X-Screens with Radeon Driver"
date: 2014-05-19
forum: Multimedia Software
---

### Post by ryan-maloney on 2014-05-19
Hi,

Due to the constraints of a program (Psychophysics toolbox), I need to handle multiple monitors with separate X-Screens, but after a lot of hassle, I've had very little success. The primary monitor is DVI-0, while the secondary monitor uses HDMI.

I'm running an Intel i5-4430 CPU, ignoring the integrated graphics.

Running lspci I get this.
```

$ lspci -v | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770/8760 / R7 250X] (prog-if 00 [VGA controller])

```

Running
```
 $ xrandrScreen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected (normal left inverted right x axis y axis)
   1280x720       60.0 +   50.0     59.9  
   1920x1080      50.0  
   1920x1080i     60.1     50.0     60.0  
   1280x1024      75.0  
   1440x900       75.0     59.9  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        75.0     72.8     60.0     59.9  
   720x400        70.1  
DVI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      59.9*+
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0  



```

and here's my xorg.conf

```

Section "ServerLayout"
        Identifier    "X.org Configured"
        Option          "Xinerama" "off"
        Option          "Clone"    "off"
        Screen          0 "Screen0" 0 0
        Screen          1 "Screen1" RightOf "Screen0"
EndSection


Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection


Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "Lilliput"
        ModelName    "Monitor Model"

EndSection


Section "Device"
    Identifier  "Card0"
        Driver      "radeon"
        BusID       "PCI:1:0:0"
        Screen 0
EndSection


Section "Device"
    Identifier  "Card1"
    Option      "ZaphodHeads"       "HDMI-0"
    BusID       "PCI:1:0:0"
    Screen 1
EndSection


Section "Screen"
        Identifier     "Screen0"
        Device        "Card0"
        Monitor        "Monitor0"
        #Option     "Primary" "true"
EndSection


Section "Screen"
        Identifier     "Screen1"
        Device         "Card1"
        Monitor     "Monitor1"
EndSection


```

I've gotten multiple xScreens, however, doing so causes the graphics to go wonky (artifacts all over the place rendering most programs unusable). I have no problems if I delete xorg.conf from /etc/.

Any next steps to get this working (or more info I should provide?)

Thanks!

---

