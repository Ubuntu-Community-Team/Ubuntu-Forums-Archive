---
title: "Signal Loss on 8800GT"
date: 2008-04-08
forum: Multimedia &amp; Video
---

### Post by AngryBacon on 2008-04-08
I'm trying to get nVidia drivers working on my 8800GT but any time I try to use the driver I lose signal to my monitor.


lspci -n | grep 0300 retuns 05:00.0 0300: 10de:0611 (rev a2)

Video card model is 05:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)

Using 171.06 drivers on Hardy.

xorg.conf
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "dvorak"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "vmmouse"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "RenderAccel"           "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Option          "AddARGBGLXVisuals"     "True"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
```

I'll try to get a log file later.

---

### Post by AngryBacon on 2008-04-08
X doesn't seem to generate a log file when using the nvidia driver. Xorg.0.log and Xorg.0.log.old are identical, and startx >> filename yields nothing.

---

