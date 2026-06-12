---
title: "Twinview"
date: 2014-04-17
forum: Multimedia Software
---

### Post by meanmrmustard on 2014-04-17
I've recently changed video cards to a Nvidia GeForce GT 620.
Previously I was using a GT 610 and twinview was enabled.
After rebooting, twinview is no longer an option - the only choice is xscreen.

I was and am using the proprietary driver and have tried three different versions, 
all with the same result.

Searches on twinview are mostly for older versions of Ubuntu and nothing I've found has been the least bit enlightening.
Are there other config files that control twinview?
What could have gone wrong?

Here's my xorg.conf
Maybe there's something missing?

```

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

---

### Post by Laurent_Dinclaux on 2014-04-23
Have you tried using nvidia-settings ?

---

