---
title: "Visible 4272 x 1536 Desktop, 7 Monitors, 3 outputs, 1 video card"
date: 2011-01-28
forum: Multimedia Software
---

### Post by adapeater on 2011-01-28
I currently have this working, but it may not after an update, so I'm looking for a better solution.

My goal is to have a rectangular desktop, even though the native resolutions of my monitors are not the same. I'm ok with "wasting pixels," ie. not using a portion of one of my monitors, but can't find the "proper" way specify this.

 I stumbled upon a quirk that achieved what I want when I was trying to reproduce an error to paste in this post. This sequence of commands:
```
xrandr --fb 4272x1536 --output DFP1 --scale 1x.8 --mode 1920x1200 --pos 0x0
xrandr --output CRT1 --pos 1200x0
xrandr --output CRT2 --pos 1200x768
xrandr --fb 4272x1536 --output DFP1 --scale 1x1 --mode 1920x1200 --pos 0x0
```result in a band of unused pixels at the bottom of one of my monitors (the one that is "too tall"). I'd like a better solution though, as I'm concerned this result is more of a quirk than an intended behavior.

 Using the 1x.8 scaling gave me a rectangular desktop, but it looked **really bad**. Adding that final line gives me what I want; even though xrandr complains:
```
xrandr: specified screen 4272x1536 not large enough for output DFP1 (1200x1920+0+0)
```First I tried a couple of other possibilities, such as I creating a modeline with 1920x1200 timings, but only using 1536 pixels. However this error occurs: "xrandr: Configure crtc 0 failed"

Let's see if I can draw a picture to help illustrate:
```

+-----+ +----+ +----+ +----+
|     | |CRT | |CRT | |CRT |
| HP  | +----+ +----+ +----+
|ZR24w| +----+ +----+ +----+
|     | |LCD | |LCD | |LCD |
+-----+ +----+ +----+ +----+
```The HP ZR24w is on the left, rotated to portrait rather than widescreen (1200x1920). CRT1 and CRT2 are each connected to a TripleHead2Go Digital Edition, each of which is connected to three monitors running at 1024x768. Three old CRTs are sitting above three old LCDs.

By default the HP uses all 1920 pixels, whereas 2 x 768 is only 1536. So I end up with an invisible portion of the desktop "below" the LCDs. I have accidentally stretched windows down in to this area. 

For testing purposes I've "lost" a window by moving it to this invisible area. I was able to get it back using shortcut keys and moving it up to the visible area, but it'd rather not loose the window in the first place.

my xorg.conf:
```
Section "ServerLayout"
    Identifier     "Basic fglrx"
    Screen      0  "Screen1" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Disable" "false"
    Option        "PreferredMode" "1440x900"
    Option        "Rotate" "left"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "3072x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "900 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "3072x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "900 768"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Device0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "Device1"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    Option        "Monitor-CRT1" "0-CRT1"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Device1"
    DefaultDepth     24
    SubSection "Display"
        Virtual   4272 1920
        Depth     8
    EndSubSection
    SubSection "Display"
        Virtual   4272 1920
        Depth     16
    EndSubSection
    SubSection "Display"
        Virtual   4272 1920
        Depth     32
    EndSubSection
    SubSection "Display"
        Virtual   4272 1920
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Device0"
    DefaultDepth     24
    SubSection "Display"
        Virtual   4272 1920
        Depth     8
    EndSubSection
    SubSection "Display"
        Virtual   4272 1920
        Depth     16
    EndSubSection
    SubSection "Display"
        Virtual   4272 1920
        Depth     32
    EndSubSection
    SubSection "Display"
        Virtual   4272 1920
        Depth     24
    EndSubSection
EndSection


```

---

