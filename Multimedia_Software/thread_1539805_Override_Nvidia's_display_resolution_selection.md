---
title: "Override Nvidia's display resolution selection"
date: 2010-07-27
forum: Multimedia Software
---

### Post by Despot on 2010-07-27
Recently I encountered a problem with a triple-monitor setup where the EDID was rejected by the nvidia driver (version 195.36.08), claiming that the EDID checksum was invalid. The maximum resolution that the driver would allow was 640x480. Searching through the X logs (/var/log/Xorg.0.log), I found the following message:

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

### Post by K.Mandla on 2010-07-28
Moved to Multimedia and Video.

---

### Post by nutznboltz on 2010-11-02
Things get worse with Maverick; you cannot even use the console without X then:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601376](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601376)

---

### Post by nutznboltz on 2010-11-03
Same solution with

01:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce 210] [10de:0a65] (rev a2)

Monitor: DS-275W

$ lsb_release -sd
Ubuntu 10.04.1 LTS

$ uname -srv
Linux 2.6.32-25-generic-pae #45-Ubuntu SMP Sat Oct 16 21:01:33 UTC 2010

$ dpkg -l | grep nvid
ii  nvidia-173-modaliases                173.14.27-0ubuntu1                              Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                 96.43.18-0ubuntu1                               Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                        0.2.23                                          Find obsolete NVIDIA drivers
ii  nvidia-current                       260.19.12-0ubuntu1~xup1~lucid                   NVIDIA binary Xorg driver, kernel module and
ii  nvidia-current-modaliases            260.19.12-0ubuntu1~xup1~lucid                   Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-settings                      260.19.12-0ubuntu1~lucid~xup                    Tool of configuring the NVIDIA graphics driv

```
$ cat xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.12  (buildmeister@builder101)  Fri Oct  8 13:54:10 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
#override
	Modeline "2560x1440_60.0"  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
#end override
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
#override
	Option "IgnoreEDIDChecksum" "DFP-1"
	Option "ExactModeTimingsDVI" "TRUE"
	Option "ModeValidation" "NoDFPNativeResolutionCheck"
#end override
    SubSection     "Display"
#override
	Modes "2560x1440"
	Modes "2560x1440_60.0"
#end override
        Depth       24
    EndSubSection
EndSection

```

---

