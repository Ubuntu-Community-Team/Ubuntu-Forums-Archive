---
title: "Fullscreen issue prevents me to use OpenOffice, Kaffeine, KPDF, etc in fullscreenmode"
date: 2009-05-30
forum: Multimedia Software
---

### Post by insane2600tt on 2009-05-30
Dear all, first of all thank you for opening a new world to me: LINUX!

I'm writing because I'm quite a newbie with this fantastic operating system and I want to migrate from windows to linux for ever; also for my work in the company.

I'm using right now a DualScreen configuration to project a second X screen during presentations: it works like a charm with **VLC** using the 1280x1024 size of the projector but uses only part of the screen when I use KAFFEINE or KPDF or OPENOFFICE in thei fullscreen mode.

Basically I have 2 screens, setted up in "Separate X" mode, working with NVidia drivers: the screen of my laptop that is **1280x800** and the projector screen that is **1280x1024**. In synthesys the problem is that regardless if I use the first or the second one, when I maximize something but vlc, it uses the size of the smallest screen.

**VLC fullscreen experience, OK** _[http://img171.imageshack.us/my.php?image=vlcfullscreen.png](http://img171.imageshack.us/my.php?image=vlcfullscreen.png)_
**Kaffeine,OpenOffice,Firefox,ecc BAD fullscreens **_[http://img140.imageshack.us/my.php?image=kaffeinefullscreen.png](http://img140.imageshack.us/my.php?image=kaffeinefullscreen.png)_

here is my xorg.conf: _[http://pastebin.com/f604546ce](http://pastebin.com/f604546ce)_
here my lspci: _[http://pastebin.com/m3182a31d](http://pastebin.com/m3182a31d)_
and here my kernel version, os, nvidia drivers version, kde version, xorg version: _[http://pastebin.com/m20b2e41](http://pastebin.com/m20b2e41)_

I tried to solve it by my self, but now is one week I fight with it and I'm out of ideas and I'm not so experienced with linux, hence I ask for your help, because I really don't want to come back to windows.

Thanks to everybody,
Marco

---

### Post by insane2600tt on 2009-05-30
I solved moving towards TwinView... yes, i don't have the facilities of 2 X servers, but still... is the only way I found to let everything work.

Here is my xorg.conf; hope that helps someone in the future :-)
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load           "glx"
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
    Option         "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AcerView"
    HorizSync       31.0 - 79.0
    VertRefresh     56.0 - 85.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "AcerView"
    HorizSync       31.0 - 79.0
    VertRefresh     56.0 - 85.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6200"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6200"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x1024 +1280+0, DFP: 1280x800 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x1024 +0+0"
EndSection

```

---

