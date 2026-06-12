---
title: "[SOLVED] LCD monitor won't get set to native resolution of 1366x768"
date: 2008-11-21
forum: Multimedia Software
---

### Post by anomalous_underdog on 2008-11-21
I'm using a ViewSonic VA1616w as a secondary monitor, and it keeps on getting set to 1024x768. I want it set to 1366x768

here's my xorg.conf
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" LeftOf "Screen1"
    Screen      1  "Screen1" 0 0

    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "pad"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "USB" "on"
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "USB" "on"
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "USB" "on"
EndSection

Section "InputDevice"
    Identifier     "pad"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "pad"
    Option         "USB" "on"
EndSection

Section "Monitor"
 #
    Identifier     "Monitor0"
    VendorName     "AOC"
    ModelName      "AOC SPECTRUM 7GlrA"
    HorizSync       30.0 - 85.0
    VertRefresh     50.0 - 130.0
    Gamma           1.715 2.347 1.996
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "ViewSonic"
    ModelName      "ViewSonic VA1616w SERIES"
    HorizSync       24.0 - 82.0
    VertRefresh     50.0 - 75.0
    Gamma           1.0
    Option         "IgnoreEDID"
    #DisplaySize     1600    900

EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:5:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:5:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT-1: 1280x1024 +0+0"
  SubSection "Display"
    Depth 24
  EndSubSection
EndSection

# 1366 x 768

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    #Option "ModeValidation" "NoEdidDFPMaxSizeCheck"
    Option "UseEdidFreqs" "FALSE"
    Option "UseEDIDDpi" "FALSE"
    Option "ModeValidation" "NoEdidModes"

    #Option "ModeValidation" "NoDFPNativeResolutionCheck"
    Option         "metamodes" "CRT-0: 1366x768_60 +0+0"
  SubSection "Display"
    Depth 24
	 Modes "1366x768"
  EndSubSection
EndSection


```

---

### Post by Arup on 2008-11-22
From what I see, your monitor is being identified as AOC instead of Viewsonic. I have a Viewsonic VA1716w and it runs its native resolution of 1440x900 from first boot with Intrepid x64 using build in Intel G31. Strangely in Windows XPx64, it needs special beta drivers from Intel to run at its native resolution.

---

### Post by anomalous_underdog on 2008-11-22
Like I said, the ViewSonic is a secondary monitor. The AOC is my primary monitor. The ViewSonic is labeled "Monitor1", while the AOC is labeled as "Monitor0".

---

### Post by anomalous_underdog on 2008-11-22
I followed Starcannon's advice in this [thread](http://ubuntuforums.org/showthread.php?t=964567) and used [http://xtiming.sourceforge.net/](http://xtiming.sourceforge.net/)

So for anyone else who uses a ViewSonic VA1616w, the one I got was this:

Modeline "1360x768@60" 84.50 1360 1392 1712 1744 768 783 791 807

Don't worry that it says 1360x768, it really gets set to 1366x768, as my monitor's built-in menu verifies.

---

