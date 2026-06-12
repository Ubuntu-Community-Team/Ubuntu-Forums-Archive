---
title: "nvidia: initialize screen if not connected"
date: 2012-01-26
forum: Multimedia Software
---

### Post by barbex on 2012-01-26
Hello!

I have a PC that I use as a media center in the living room. It has one small Monitor connected via VGA and the TV as a second screen connected via DVI -> HDMI.

It all works fine if the TV is turned on when the PC boots but I usually have the TV turned off. In that case the nvidia driver doesn't initialize the TV as a second display and I would have to turn it on and then restart X to get it working. (Annoying and not family friendly)

I hunted around in the nvidia driver options but I can't get it to work!

Here is my xorg.conf:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "GVC"
    HorizSync       31.0 - 53.0
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: unknown, VertRefresh source: unknown
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Toshiba TFT-TV"
    HorizSync       15.0 - 46.0
    VertRefresh     49.0 - 61.0
    ModeLine       "1920x1080" 74.25 1920 2008 2052 2200 1080 1084 1094 1124 +hsync +vsync interlace
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 800x600_60 +0+0"
    Option         "DPI"  "81 x 81"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "UseEDID" "false"
    Option         "ConnectedMonitor" "DFP"
    Option         "ExactModeTimingsDVI" "TRUE"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    Option         "DPI"  "110 x 110"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

And here is what the log says after booting:

```

 24.884] (II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:2:0:0 (GPU-0)
[    24.884] (--) NVIDIA(0): Memory: 262144 kBytes
[    24.885] (--) NVIDIA(0): VideoBIOS: 05.44.a2.03.00
[    24.885] (II) NVIDIA(0): Detected AGP rate: 8X
[    24.885] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    24.885] (--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:2:0:0
[    24.885] (--) NVIDIA(0):     GVC (CRT-0)
[    24.885] (--) NVIDIA(0): GVC (CRT-0): 400.0 MHz maximum pixel clock
[    24.885] (II) NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
[    24.885] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    24.885] (II) NVIDIA(0): Validated modes:
[    24.885] (II) NVIDIA(0):     "CRT:800x600_60+0+0"
[    24.885] (II) NVIDIA(0): Virtual screen size determined to be 800 x 600
[    24.887] (**) NVIDIA(0): DPI set to (81, 81); computed from "DPI" X config option
[    24.887] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    24.887] (**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
[    24.887] (==) NVIDIA(1): RGB weight 888
[    24.887] (==) NVIDIA(1): Default visual is TrueColor
[    24.887] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[    24.887] (**) NVIDIA(1): Option "UseEDID" "false"
[    24.887] (**) NVIDIA(1): Option "ConnectedMonitor" "DFP"
[    24.887] (**) NVIDIA(1): Option "TwinView" "0"
[    24.887] (**) NVIDIA(1): Option "MetaModes" "DFP: 1920x1080_60 +0+0"
[    24.887] (**) NVIDIA(1): Option "ExactModeTimingsDVI" "TRUE"
[    24.887] (**) NVIDIA(1): Option "DPI" "110 x 110"
[    24.887] (**) NVIDIA(1): Enabling RENDER acceleration
[    24.888] (II) NVIDIA(1): NVIDIA GPU GeForce 6200 (NV44) at PCI:2:0:0 (GPU-0)
[    24.892] (--) NVIDIA(1): Memory: 262144 kBytes
[    24.892] (--) NVIDIA(1): VideoBIOS: 05.44.a2.03.00
[    24.892] (II) NVIDIA(1): Detected AGP rate: 8X
[    24.892] (--) NVIDIA(1): Interlaced video modes are supported on this GPU
[    24.892] (--) NVIDIA(1): Connected display device(s) on GeForce 6200 at PCI:2:0:0
[    24.892] (--) NVIDIA(1):     GVC (CRT-0)
[    24.892] (--) NVIDIA(1): GVC (CRT-0): 400.0 MHz maximum pixel clock
[    24.892] (EE) NVIDIA(1): Unable to find available Display Devices for screen 1.
[    24.892] (EE) NVIDIA(1): No display devices found for this X screen.
[    24.892] (II) UnloadModule: "nvidia"
[    24.892] (II) UnloadModule: "wfb"
[    24.892] (II) UnloadModule: "fb"
[    24.892] (--) Depth 24 pixmap format is 32 bpp
[    24.893] (II) NVIDIA(0): Initialized AGP GART.
[    24.903] (II) NVIDIA(0): Setting mode "CRT:800x600_60+0+0"
[    25.005] (II) Loading extension NV-GLX
[    25.229] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    25.236] (==) NVIDIA(0): Disabling shared memory pixmaps
[    25.236] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    25.236] (==) NVIDIA(0): Backing store disabled
[    25.236] (==) NVIDIA(0): Silken mouse enabled
[    25.237] (**) NVIDIA(0): DPMS enabled
[    25.237] (II) Loading extension NV-CONTROL
[    25.237] (II) Loading extension XINERAMA
[    25.237] (II) Loading sub module "dri2"
[    25.237] (II) LoadModule: "dri2"
[    25.238] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.238] (II) NVIDIA(0): [DRI2] Setup complete
[    25.238] (==) RandR enabled

```

From what I read in the nvidia readme Option "ConnectedMonitor" "DFP" is supposed to do exactly what I want but it doesn't work.

Anything else I can try?

---

