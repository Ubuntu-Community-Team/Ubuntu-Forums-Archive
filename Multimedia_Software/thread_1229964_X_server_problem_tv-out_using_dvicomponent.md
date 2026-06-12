---
title: "X server problem: tv-out using dvi/component"
date: 2009-08-02
forum: Multimedia Software
---

### Post by Tjena on 2009-08-02
Hi, I just got a new computer and I'm using 64-bit Intrepid on it. I wanted to use the computer as a media center, so I figured I'd plug it into my HD television. 

The problem: My tv is Sony KLV-L32M1, so the only way to get HD resolutions is to use component cables for the picture. I bought a cheap DVI-component cable, but I can't get the screen showing. The screen only keeps flickering and sometimes shows a pinkish, fuzzy picture. 

I've been trying to configure the X server for quite a while now, but I honestly don't know if it's even possible to get it working. The graphics card is MSI GeForce n9400gt. Any help with this would be appreciated. Right now I think the reason it isn't working is that the graphics card is trying to send RGB over the cable, while the TV needs yPbPr as input (hence the flickering and stuff). 

Is there a way to force the graphics card to send yPbPr instead of RGB?

---

### Post by beckols on 2011-03-28
Did you ever figure this out?  I'm currently trying to do the same thing, and all I'm getting is flickering.

Video Card: GeForce 8400 GS

Xorg.conf:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

If anyone has any ideas, let me know.

---

