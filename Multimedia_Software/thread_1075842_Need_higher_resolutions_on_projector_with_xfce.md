---
title: "Need higher resolutions on projector with xfce"
date: 2009-02-20
forum: Multimedia Software
---

### Post by Neeperand on 2009-02-20
I am using Mythbuntu 8.10 (XFCE as the window manager).  I have an Infocus 4805 Projector that it's hooked up to using the DVI cable. The native resolution of the projector is 854x480 and xfce automatically configured this resolution.  This is fine for most of the things I do (mythtv, hulu, etc). However, when doing maintenance most windows require more than 600 pixels to display and I can't see the bottom of the window to click "OK", "Accept", etc.

What I want is one of the following:
1. I know the projector is capable of accepting higher resolutions and downsizing them (I've done this with Windows), so I'd like to tell xfce that it's OK to use a higher resolution.
2. Or, be able to tell the VNC viewer to display in a higher resolution.

My xorg.conf is the just the default created when I installed mythbuntu:
> Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Thanks.

---

