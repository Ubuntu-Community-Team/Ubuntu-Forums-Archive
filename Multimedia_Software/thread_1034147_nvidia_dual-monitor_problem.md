---
title: "nvidia dual-monitor problem"
date: 2009-01-08
forum: Multimedia Software
---

### Post by leeroberts21 on 2009-01-08
**Update:** After changing the resolution in 'System > Preferences > Screen Resolution' to 1680x1050, it stays at this resolution when I restart, AND the second monitor is now at 1280x1024 and taking up the full screen like it should. However, 'Screen Resolution' will not let me set my monitor to 60hz, which is what it should be, and what I keep changing it back to in nvidia-settings, and the 50hz is making my text look weird. So again, my problem with the second monitor seems to be fixed, however I think I need to disable the 'System > Preferences > Screen Resolution' somehow so that it does not default back to this, instead of my nvidia settings. How would I go about doing this, or fixing my problem another way?

-----------------------------------------

I have two monitors, both using DVI cables with VGA adapters so they can plug into my graphics card. My graphics card is an nVidia 8800 GT. I had everything running fine on Ubuntu 8.04, using the driver nvidia-glx-new. I upgraded to Ubuntu 8.10 today and started using the nvidia 180 driver and have had nothing but problems. I tried uninstalling everything and using the nvidia 177 drivers, but they had the same problems as well so now I'm trying to get the 180 drivers working again.

My main monitor is a 22" HP LCD which is supposed to have a resolution of 1680x1050@60hz. I have this one working correctly after a lot of tinkering.

My second monitor is a 19" Hyundai LCD which is supposed to have a resolution of 1280x1024@60hz. I have tried using the nvidia-settings tool to change it's resolution, but when I change it to the correct resolution, it only displays on about 1/4 of the monitor, with large black spaces on the right and bottom of the picture. When I switch to either TwinView, or enable Xinerama, the whole screen shows, however this is not how I want my screens to function. I want them to be seperate x servers so that I can have essentially two desktops. This is how I had it setup in Ubuntu 8.04 and it was working great. 

Also, I have tried manually editing xorg.conf and every time I change it to what I think should be the right settings, it seems to disable the nvidia driver and immediately put me into low-graphics mode. I can then reset xorg.conf and it puts me back into the default "nv" driver and I can re-enable the nvidia driver from there, but it is still having the same problem.

Any ideas? I'm still pretty new to Ubuntu so please explain things well enough that I can follow. :P

(P.S. I have tried installing the nvidia drivers from the hardware manager, from synaptic, and from the nvidia website. I had the most luck with the one from the nvidia website, that fixed most of my problems, except for the one I am talking about above.)

P.S.S - I'm not sure if it matters, but I am using kernel version 2.6.27-9-generic. ALSO, I just noticed that whenever I restart, my main monitor's resolution is getting reset to the resolution that is set in System > Preferences > Screen Resolution (1680x1050@**50**hz). The second monitor is still at the same resolution, but it still has the large black spaces.

---

### Post by leeroberts21 on 2009-01-08
Here is my xorg.conf:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
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
    ModelName      "CRT-0"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HIQ B70A"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-0: 1680x1050_60 +0+0; CRT-0: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1680x1050_60 +0+0; CRT-0: nvidia-auto-select +0+0; CRT-0: 1680x1050 +0+0"
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
    Option         "metamodes" "CRT-1: 1280x1024_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

