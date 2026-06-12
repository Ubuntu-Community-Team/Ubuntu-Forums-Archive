---
title: "Nvidia custom edid fix"
date: 2011-04-17
forum: Multimedia Software
---

### Post by martingrayson on 2011-04-17
Hi All,

I'm having some trouble with my graphics on my NVidia based Acer Aspire Revo following adding a surroundsound reciever to my HTPC. I'm using the latest Nvidia binaries, and all was working well prior to adding the reciever to my system.

When connecting the machine directly to a TV (Toshiba) via HDMI I'm able to play video fine, but when using HDMI via the reciever (i.e. PC->Reciever->TV) I get random black flashes.

I think this is because the drivers not able to detect information about the TV via EDID. But after capturing the EDID file and running it thru a command line tool, I'm in no better shape. I've also tried to disable NView but nothing seems to work.

Does any body have an idea whats going on?

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TSB TOSHIBA-TV"
    HorizSync       15.0 - 46.0
    VertRefresh     49.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
    Option         "CustomEDID" "DFP-0:/etc/X11/toshiba_exts.edid"
    Option         "DynamicTwinView" "False"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option "UseDisplayDevice" "DFP"
    Option         "metamodes" "1920x1080_50i +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

