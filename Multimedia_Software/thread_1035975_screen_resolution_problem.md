---
title: "screen resolution problem"
date: 2009-01-10
forum: Multimedia Software
---

### Post by Myth123 on 2009-01-10
Hi,
I have installed icewm on the top of X11 and ubuntu server edition 8.04.
My problem is screen resolution is low (800x600) and I wanted to enhance it to 1024x768.
My xorg.conf file is as follows :

```
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
        Driver          "openchrome"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24

        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection


```

My chipset is ASUS VIA K8M800.

---

