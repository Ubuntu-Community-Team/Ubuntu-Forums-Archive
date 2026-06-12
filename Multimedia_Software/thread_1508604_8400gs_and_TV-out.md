---
title: "8400gs and TV-out"
date: 2010-06-13
forum: Multimedia Software
---

### Post by Mastus on 2010-06-13
Hi,

I have a Leadtek(?) 8400GS GPU and I'm having troubles getting the TV-out to work.

I'm using Ubuntu 10.04 and 195.36.24 nVidia drivers from the repos.

xorg.conf as follows:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 0 0
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

    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic E95"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 180.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:6:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:6:0:0"
    Screen          0
EndSection

Section "Screen"

# Removed Option "metamodes" "TV: 800x600 +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "ConnectedMonitor" "CRT-1, TV-0"
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1280x960 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

There's no video output, and the Xorg.0.log always spits out these errors:

```

(II) Jun 13 12:54:31 NVIDIA(1): Display Device found referenced in MetaMode: TV-0
(II) Jun 13 12:54:31 NVIDIA(1): Assigned Display Device: TV-0
(EE) Jun 13 12:54:31 NVIDIA(1): The requested configuration of display devices (TV-0) in
(EE) Jun 13 12:54:31 NVIDIA(1):     MetaMode "TV:nvidia-auto-select+0+0" is not supported on
(EE) Jun 13 12:54:31 NVIDIA(1):     this GPU; none is recommended, instead.
(WW) Jun 13 12:54:31 NVIDIA(1): 
(WW) Jun 13 12:54:31 NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) Jun 13 12:54:31 NVIDIA(1):     "nvidia-auto-select".
(WW) Jun 13 12:54:31 NVIDIA(1): 
(EE) Jun 13 12:54:31 NVIDIA(1): The requested configuration of display devices (TV-0) in
(EE) Jun 13 12:54:31 NVIDIA(1):     MetaMode "nvidia-auto-select" is not supported on this
(EE) Jun 13 12:54:31 NVIDIA(1):     GPU; none is recommended, instead.
(EE) Jun 13 12:54:31 NVIDIA(1): Unable to use default mode "nvidia-auto-select".

```

The nvidia-settings utility also gives errors of not finding the metamodes...

Please help.

---

### Post by Mastus on 2010-06-14
Pffft....

I have installed the latest beta drivers (256.29) from the x-swat ppa.

The Xorg.0.log says this
```

(--) Jun 14 15:28:26 NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:6:0:0:
(--) Jun 14 15:28:26 NVIDIA(0):     ViewSonic E95 (CRT-1)
(--) Jun 14 15:28:26 NVIDIA(0):     NVIDIA TV Encoder (TV-0)

```

So I presume that the TV is detected? The ConnectedDisplays option doesn't change anything.

I have modified my xorg.conf as follows

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    ModelName      "ViewSonic E95"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 180.0
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:6:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:6:0:0"
    Screen          1
    Option	   "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "TV-0"
    Option	   "ModeValidation" "TV-0: NoMaxPClkCheck, NoMaxSizeCheck, NoHorizSyncCheck, NoVertRefreshCheck, NoWidthAlignmentCheck, NoVirtualSizeCheck, NoVesaModes, NoEdidModes, NoExtendedGpuCapabilitiesCheck, NoTotalSizeCheck"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x960 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes       "800x600"
    EndSubSection
EndSection

```

And guess what? No TV-output and the same old story on logs...

```

(II) Jun 14 15:28:26 NVIDIA(1): Mode Validation Overrides for NVIDIA TV Encoder (TV-0):
(II) Jun 14 15:28:26 NVIDIA(1):     NoMaxPClkCheck
(II) Jun 14 15:28:26 NVIDIA(1):     NoMaxSizeCheck
(II) Jun 14 15:28:26 NVIDIA(1):     NoHorizSyncCheck
(II) Jun 14 15:28:26 NVIDIA(1):     NoVertRefreshCheck
(II) Jun 14 15:28:26 NVIDIA(1):     NoVesaModes
(II) Jun 14 15:28:26 NVIDIA(1):     NoEdidModes
(II) Jun 14 15:28:26 NVIDIA(1):     NoWidthAlignmentCheck
(II) Jun 14 15:28:26 NVIDIA(1):     NoVirtualSizeCheck
(II) Jun 14 15:28:26 NVIDIA(1):     NoExtendedGpuCapabilitiesCheck
(II) Jun 14 15:28:26 NVIDIA(1):     NoTotalSizeCheck
(II) Jun 14 15:28:26 NVIDIA(1): Assigned Display Device: TV-0
(EE) Jun 14 15:28:26 NVIDIA(1): The requested configuration of display devices (TV-0) in
(EE) Jun 14 15:28:26 NVIDIA(1):     MetaMode "800x600" is not supported on this GPU; none is
(EE) Jun 14 15:28:26 NVIDIA(1):     recommended, instead.
(WW) Jun 14 15:28:26 NVIDIA(1): 
(WW) Jun 14 15:28:26 NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) Jun 14 15:28:26 NVIDIA(1):     "nvidia-auto-select".
(WW) Jun 14 15:28:26 NVIDIA(1): 
(EE) Jun 14 15:28:26 NVIDIA(1): The requested configuration of display devices (TV-0) in
(EE) Jun 14 15:28:26 NVIDIA(1):     MetaMode "nvidia-auto-select" is not supported on this
(EE) Jun 14 15:28:26 NVIDIA(1):     GPU; none is recommended, instead.
(EE) Jun 14 15:28:26 NVIDIA(1): Unable to use default mode "nvidia-auto-select".

```

Am I missing an option to override the mode validations? Or is this a driver bug - as in it doesn't respect the overrides? I know that the TV-out is rarely used nowadays, so does anyone have working configuration with an nVidia card and 10.04 Ubuntu? Had an FX5200 and Ubuntu 9.10 on my old computer and it worked like a charm (after a bit of fiddle, but not much)

I messed around with the drivers and such - and I managed to got the nvidia kernel error and then the TV came alive! No output on the monitor though... So I think that the GPU is not defective. 

Please help. 

 ](*,)

---

