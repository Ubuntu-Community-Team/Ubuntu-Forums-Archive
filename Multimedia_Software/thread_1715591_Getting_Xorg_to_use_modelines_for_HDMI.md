---
title: "Getting Xorg to use modelines for HDMI"
date: 2011-03-27
forum: Multimedia Software
---

### Post by kingmob on 2011-03-27
Hi, 

I'm having trouble with my sony bravia and the automatic setting of the display over HDMI. In the Xorg.0.log I get a bunch of "EDID contradicts itself" error messages and then finaly it will set a 1920x1080 resolution at 50Hz. In the nvidia gui I successfully see the 24Hz, 50Hz and 60Hz modes, but when I select them, my TV does not recognize them as such. Because of this, xbmc can not set the right refresh rates (I assume this is the cause) and I get tearing.

Some output:
Xrandr gives:
```

1920x1080      50.0*     51.0     52.0     53.0    54.0     55.0    159.0

```

At the same time, "nvidia-settings -nt -q RefreshRate" says
```

60.00 Hz

```

Nvidia-settings seems to be reporting correctly in this case. And whatever I set the output to, xrandr will for instance say it is 53Hz for the 60Hz mode and 159 for the 24Hz mode, Nvidia-settings will always say "60.00 Hz".

I managed to get all the correct modelines from windows vista however, but I don't know how to implement them. When I use the following, it is reported that 1920x1080@50 is not a valid mode. I changed the horisync and vertrefresh sections, since they were automatically set to "14 - 70" and "48 - 62" respectively, which would give errors I assume.
```

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DFP-1"
    HorizSync       14.0 - 135
    VertRefresh     48.0 - 152
    Option         "DPMS"
    Option         "ExactModeTimingsDVI" "True"
    Option         "UseEDIDDpi" "False"
    Option         "UseEDIDFreqs" "False"
    Modeline    "1920x1080@50" 400.000 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 210"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "IgnoreEDID"
    SubSection     "Display"
        Depth       24
        Modes       "1920x1080@50"
    EndSubSection
EndSection

```

Anyone any ideas?

---

### Post by BicyclerBoy on 2011-04-01
I don't think xrandr works well with nvidia driver..

Your modeline is way off..try this

# 1920x1080 49.93 Hz (CVT 2.07M9) hsync: 55.62 kHz; pclk: 141.50 MHz
Modeline "1920x1080_50.00"  141.50  1920 2032 2232 2544  1080 1083 1088 1114 -hsync +vsync

# reduced vertical blanking timings
# 1920x1080 59.93 Hz (CVT 2.07M9-R) hsync: 66.59 kHz; pclk: 138.50 MHz
Modeline "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync

You may need to dial back the vertical & horizontal freq ranges to sensible values so the driver does not just ignore them.

Option "UseEDID"  "FALSE"

I would try turning off overscan & all the motion flow nonsense in the TV..
Real pity you do not have a GT220 or better..for feature set C 2x de-interlacing & scaling..

---

### Post by kingmob on 2011-04-06
> **BicyclerBoy said:**
> I don't think xrandr works well with nvidia driver..

Your modeline is way off..try this

# 1920x1080 49.93 Hz (CVT 2.07M9) hsync: 55.62 kHz; pclk: 141.50 MHz
Modeline "1920x1080_50.00"  141.50  1920 2032 2232 2544  1080 1083 1088 1114 -hsync +vsync

# reduced vertical blanking timings
# 1920x1080 59.93 Hz (CVT 2.07M9-R) hsync: 66.59 kHz; pclk: 138.50 MHz
Modeline "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync

You may need to dial back the vertical & horizontal freq ranges to sensible values so the driver does not just ignore them.

Option "UseEDID"  "FALSE"

I would try turning off overscan & all the motion flow nonsense in the TV..
Real pity you do not have a GT220 or better..for feature set C 2x de-interlacing & scaling..

Thanks for your reply. I've been away from Ubuntu for a long time, so I'm a bit rusty and completely unknown with using the digital outputs. I will try this out tonight :)

---

