---
title: "Overriding Nvidia's display resolution selection"
date: 2010-07-27
forum: Multimedia Software
---

### Post by Despot on 2010-07-27
Recently I encountered a problem with a triple-monitor setup in Ubuntu Lucid (10.04) where the EDID was rejected by the nvidia driver (version 195.36.08), claiming that the EDID checksum was invalid. The maximum resolution that the driver would allow was 640x480. Searching through the X logs (/var/log/Xorg.0.log), I found the following message:

```
(WW) Jul 26 21:37:57 NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid: the
(WW) Jul 26 21:37:57 NVIDIA(GPU-0):     checksum for EDID version 1 extension is invalid.

```

The monitor in question is from HannsG, product ID is "HG281D" The open-source nouveau driver detected the monitor correctly, and I tested various video card/cable combinations, to no avail. I believe this is a bug in the nvidia driver.

To work around this problem, I had to override the nvidia driver's routines for selecting and validating display resolutions. I used the nvidia-settings utility to generate an xorg.conf with the desired three-screen configuration and the 640x480 resolution on the middle screen, then added some extra options to /etc/X11/xorg.conf.

Here is my current xorg.conf file. All monitors operate at maximum resolution with this configuration. Override options have an extra indent and bracketed by override/end override comments.

The modeline came from the X log files generated while running X using the nouveau driver ("cat /var/log/Xorg.0.log" | grep Modeline"). I used the Modeline for the highest resolution that my monitor supported: 1920x1200.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "LeftScreen" 0 0
    Screen      1  "MiddleScreen" RightOf "LeftScreen"
    Screen      2  "RightScreen" RightOf "MiddleScreen"
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
    Identifier     "LeftMonitor"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "RightMonitor"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "MiddleMonitor"
    VendorName     "HannsG"
    ModelName      "HG281D"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
#override
	Modeline "1920x1200_60.00" 154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync
#end override
EndSection

Section "Device"
    Identifier     "LeftDevice"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "MiddleDevice"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "RightDevice"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:5:0:0"
EndSection

Section "Screen"
    Identifier     "LeftScreen"
    Device         "LeftDevice"
    Monitor        "LeftMonitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "MiddleScreen"
    Device         "MiddleDevice"
    Monitor        "MiddleMonitor"
    DefaultDepth    24
#override
	Option "IgnoreEDIDChecksum" "DFP-1"
	Option "ExactModeTimingsDVI" "TRUE"
	Option "ModeValidation" "NoDFPNativeResolutionCheck"
#end override
    SubSection     "Display"
#override
	Modes "1920x1200"
#end override
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "RightScreen"
    Device         "RightDevice"
    Monitor        "RightMonitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Adding a
```
Option "ModeDebug" "TRUE"
```
line to the the MiddleScreen section produced a lot of helpful information about how the driver was validating modes.

Detailed descriptions of the options used here can be found at [http://us.download.nvidia.com/XFree86/Linux-x86/195.36.08/README/xconfigoptions.html](http://us.download.nvidia.com/XFree86/Linux-x86/195.36.08/README/xconfigoptions.html)

---

