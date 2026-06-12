---
title: "No sound in &quot;standalone&quot; X-Server"
date: 2010-11-25
forum: Multimedia Software
---

### Post by upskuhr on 2010-11-25
Hello,

usually I use a Xinerama setup with 3 monitors. But for playing nexuiz  (a free egoshooter) I switch to a single monitor. Therefore I have a  second xorg.conf called xorg.conf.1Monitor and start nexuiz with this  little script:
```
#!/bin/sh
export XORGCONFIG=xorg.conf.1Monitor
xinit /usr/games/nexuiz --  :2&
```The script works so far (it  used it with gentoo a couple of years). I execute it and nexuiz starts  on a single screen just like I want it. But without sound. I tried also  to stop gdm and start the script as the only X-Server, also no sound.

Do I need to start something additionally? Some soundserver or whatever? Or what might be the problem?

Here my  xorg.conf.1Monitor
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
upskuhr

---

### Post by upskuhr on 2010-11-29
*bump*

---

### Post by p4ndepravity on 2011-04-28
i also have the same problem. ubuntu server 10.10 + X + openbox + firefox - sound =\

i've installed alsamixer and toyed around with the devices therein to no avail.

I use onboard sound with nvidia 6xxx mobo

any insight would be great

aka buuump

---

