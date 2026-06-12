---
title: "GeForce 6800 LE: no tv-out"
date: 2008-05-18
forum: Multimedia Software
---

### Post by un2982 on 2008-05-18
Hi,

i'm under Ubuntu Hardy with a Nvidia 6800 LE and i have some problems to use the TV-out.
I have two 19'TFT screens and split my desktop with the twinview feature (it's great :-)).

I had tryied a lot of configurations for my xorg.conf file, but i can't have any display on the tv (i know that i cannot use tree outputs neither the DVI in the same time than the tv-out, but i would like having one TFT output in the same time than a TV output).

Under Windows Xp and Vista i don't have any problem to do that, but i work with Linux and i'm borred having to reboot to Windows when i want to see a film on tv :-(

Here is my  xorg.conf file :
```

#
# Dual Screen Ok, but no TV-OUT signal
#
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "F419_TWIN" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "be"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor_F419"
    VendorName     "neovo"
    ModelName      "Arnos Instruments F-419"
    HorizSync       30.0 - 80.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "TwinView" "true"
    Option         "TwinViewOrientation" "CRT-0 LeftOf CRT-1"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "PAL-B"
    Option         "SecondMonitorHorizSync" "30-50"
    Option         "SecondMonitorVertRefresh" "60"
    Option         "MetaModes" "1280x1024,1280x1024;1280x1024@1280x800;1280x1024,800x600;1024x768,1024x768;800x600,800x600;640x480,640x480;512x384,512x384"
EndSection

Section "Device"
    Identifier     "Device_6800LE"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 LE"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "F419_TWIN"
    Device         "Device_6800LE"
    Monitor        "Monitor_F419"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1280x1024_60 +0+0, CRT-1: 1280x1024_60 +1280+0;CRT-0: 1280x1024_60 +0+0, CRT-1: 1024x768_60 +1280+0; CRT-0: 1024x768 +0+0, CRT-1: 800x600 +1024+0; CRT-0: 800x600 +0+0, CRT-1: 640x480 +800+0; CRT-0: 640x480 +0+0, CRT-1: 512x384 +640+0; CRT-0: 512x384 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

Does anyone have an idea?

---

### Post by un2982 on 2008-05-20
Neither of yours use an nVidia with this configuration?

---

