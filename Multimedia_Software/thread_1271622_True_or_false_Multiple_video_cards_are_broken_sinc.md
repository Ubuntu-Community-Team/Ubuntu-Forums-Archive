---
title: "True or false: Multiple video cards are broken since Hardy"
date: 2009-09-21
forum: Multimedia Software
---

### Post by ThomasJ02 on 2009-09-21
This bug ([https://bugs.freedesktop.org/show_bug.cgi?id=20816](https://bugs.freedesktop.org/show_bug.cgi?id=20816)) seems to imply that Ubuntu and X haven't worked for people with multiple video cards since, say, last year. 

Does anyone have a fully working multicard X with windows that can span all of their screens, or is this one of those situations where it's better to run Windows (Vista supports this out of the box)

---

### Post by markbuntu on 2009-09-22
While RandR1.2 does not support multiple video cards, it is still possible to use xinerama with the latest nvidia and ati drivers for multiple cards/screens. 

I have two video cards and three monitors and have them set up so all three act as a single screen. I can move windows between them, stretch windows across all three etc.

This is not a ubuntu problem, it is a problem with x and its move to randr before multiple cards was worked out but as I said, the nvidia and ati proprietary drivers are able to do this with xinerama. I do not know if this is possible with other drivers.

---

### Post by ThomasJ02 on 2009-09-23
Thanks for your reply - I actually went out and bought a pair of cheap nVidia cards and it works now!

xorg.conf:

```

Section "Monitor"
        Identifier      "Monitor0"
EndSection

Section "Monitor"
        Identifier      "Monitor1"
EndSection

Section "Monitor"
        Identifier      "Monitor2"
EndSection



Section "Screen"
        Identifier      "Screen0"
        Device "Device0"
        Monitor "Monitor0"
        DefaultDepth    24
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device "Device1"
        Monitor "Monitor1"
        DefaultDepth    24
EndSection

Section "Screen"
        Identifier      "Screen2"
        Device "Device2"
        Monitor "Monitor2"
        DefaultDepth    24
EndSection


Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Device0"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        BusID "PCI:1:0:0"
        Screen 0
EndSection

Section "Device"
        Identifier      "Device1"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        BusID "PCI:1:0:0"
        Screen 1
EndSection

Section "Device"
        Identifier      "Device2"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        BusID "PCI:5:0:0"
EndSection


Section "ServerLayout"
        Identifier "Layout0"
        Screen  0 "Screen0" 0 0
        Screen  1 "Screen1" LeftOf "Screen0"
        Screen  2 "Screen2" RightOf "Screen0"
EndSection

Section "ServerFlags"
        Option "Xinerama" "1"
EndSection

```

I also needed to use [https://launchpad.net/~m0sia/+archive/ppa](https://launchpad.net/~m0sia/+archive/ppa) to prevent the ghost cursor issue some other people and I have been having with Xinerama.

---

