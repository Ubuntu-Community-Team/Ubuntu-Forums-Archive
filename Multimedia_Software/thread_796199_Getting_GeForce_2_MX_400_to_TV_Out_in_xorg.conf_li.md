---
title: "Getting GeForce 2 MX 400 to TV Out in xorg.conf like it does via nvtv?"
date: 2008-05-16
forum: Multimedia Software
---

### Post by Mark Kidd on 2008-05-16
Thanks in large part to many forum posts that helped me along the way, I have been able to setup Hardy to work pretty well with my GeForce 2 MX 400. I used EnvyNG to install nvidia's '96' drivers and got my xorg.conf straightened out so that I'm able to set my monitor and my attached television (CRT television connected via SVIDIO) as separate X screens.

The trouble is, I am having trouble figuring out how to get the television to display across its full width. This is possible with nvtv, but since AFAIK nvtv doesn't work with a dual X screen setup I don't know how to go about getting that result with the tools at hand.

I have a suspicion that a custom modeline is the route to success, but my searches have not yielded any ideas (that don't crash X at any rate). I'd really appreciate anyone that can start me on the right direction. I've had the best luck with 800x600 on the television, if that matters.

Here's my xorg.conf:
```

Section "ServerLayout"
    Identifier     "Simple Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 828FI"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 120.0
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    BoardName      "GeForce2 MX/MX 400"
    Option         "ConnectedMonitor" "Monitor0"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    BoardName      "GeForce2 MX/MX 400"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "NSTC-M"
    Option         "ConnectedMonitor" "Monitor1"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "N
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSectionVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSectionVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

And here's the output from nvtv when it's working its magic on my TV out:
```

*** Resolution 800 x 600  Overscan 11.900 x 05.350*** CRT Registers
  Clock       : 0,
  HDisplay    : 800,
  HSyncStart  : 792,
  HSyncEnd    : 816,
  HTotal      : 840,
  HBlankStart : 800,
  HBlankEnd   : 840,
  VDisplay    : 600,
  VSyncStart  : 630,
  VSyncEnd    : 632,
  VTotal      : 690,
  VBlankStart : 600,
  VBlankEnd   : 690,
  Latency     : 0,
```

---

### Post by Teloid on 2008-05-16
I can't understand, did you use modeline or not for tv output? If no, use command gtf <width> <height> <greq> like that:
```
gtf 1600 1200 120
```
if you already tried modelines, and it coused X crash, take a look to log file /etc/xorg/Xorg.0.log (zero means log of last Xorg start).

---

### Post by Mark Kidd on 2008-05-16
I'd be glad to give that a try. What frequency should I use for a CRT TV - 50hz?

---

### Post by Mark Kidd on 2008-05-17
Or should it be 60hz? Any suggestions?

---

### Post by Redsandro on 2008-08-16
Hey Mark, did you finally get a good picture on your television?
What did you do?

---

