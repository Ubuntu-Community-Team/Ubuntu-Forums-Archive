---
title: "Poor quality picture on LCD TV"
date: 2008-07-09
forum: Mythbuntu
---

### Post by meanmrmustard on 2008-07-09
I've got a remote frontend (8.04 version) that I've recently installed and viewing on a 42" LCD television.
The problem is, when viewing live or recorded TV there are lots of (almost) vertical lines across the entire screen.
This wasn't a problem with the Gutsy version and I'm not sure what I might do to resolve the issue.
Any ideas?

Mr. M.

---

### Post by Lindsay.Mathieson on 2008-07-10
Need some info:
[LIST]
[*]What's the LCD's Resolution
[*]What connector are you using (VGA, DVI, HDMI, Composite etc)
[*]What Make & Model is the Video Card
[*]Your xorg.conf
[/LIST]

---

### Post by meanmrmustard on 2008-07-10
> **Lindsay.Mathieson said:**
> Need some info:
[LIST]
[*]What's the LCD's Resolution  
[*]Whatconnector are you using (VGA, DVI, HDMI, Composite etc) 
[*]What Make & Model is the Video Card
[*]Your xorg.conf
[/LIST]

Res is 1024x768
Using S video
Nvidia GForce FX 5200

xorg:
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection

---

