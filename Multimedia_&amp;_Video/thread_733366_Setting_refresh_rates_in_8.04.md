---
title: "Setting refresh rates in 8.04"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by feanor512 on 2008-03-23
I just did a fresh install of Ubuntu 8.04 Beta on a spare system. Unfortunately, it didn't detect the correct refresh rates for my monitor. My monitor is a Gateway VX900 and my graphics card is a Geforce 6800 GT. From Windows, I know that the monitor can handle 1600x1200x75hz, 1280x960x85hz, etc. According to [Gateway]("http://support.gateway.com/s/MONITOR/Z00833/z0083310.shtml") the specs for the monitor are Horizontal, 31 to 95 kHz; Vertical,  50 to 160 Hz.

I ran sudo dpkg-reconfigure xorg-xserver and it only asked me keyboard questions. The xorg.conf that it produced is at the end of my post. I then installed the proprietary nVidia driver through the GUI (If I do dpkg-reconfigure xorg-xserver first, it deactivates/uninstalls the proprietary nVidia driver.) Under Screen Resolution, I can only choose really low refresh rates (1600x1200x53hz, 1280x960x64hz, etc).

What do I need to add to xorg.conf to get the proper refresh rates? Thanks.
```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "vmmouse"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
    Load        "glx"
EndSection
```

---

### Post by mc4man on 2008-03-23
You may want to have this moved to the hardy thread in programming and development (use report button)  it would be interesting to see what you can and cannot add to xorg.conf in hardy. i think next week I'll remove hardy from my tester, install gutsy, configure properly and copy the conf to a flash drive. That way I'll have the correct monitor info to see what you can or cannot insert and what, if anything has an effect. (good or bad)
While there's alot of very good things about hardy user control has been slightly diminished in some area's

---

### Post by feanor512 on 2008-03-24
I installed nvidia-settings and it will allow me to choose the actual resolutions and refresh rates that my monitor can handle (regardless of xorg.conf).

This really needs to be fixed before 8.04 comes out of beta.

---

