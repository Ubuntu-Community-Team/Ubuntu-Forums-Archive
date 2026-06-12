---
title: "fglrx (everything extends to my other non-wrking screen)"
date: 2009-07-21
forum: Multimedia Software
---

### Post by UnsafeData on 2009-07-21
My video card is the **ATI HD4670**. I'm using Ubuntu Jaunty, and I'm running Openbox on it.

I want to get the fglrx drivers working, including dual screen with my two monitors. My CRT connected to DVI is on the left, and the VGA is on the right.

Before I installed the fglrx drivers, I had this in my xorg.conf:

```
SubSection "Display"
Depth 24
Modes "1024x768" "1024x768" #the resolutions of your monitors
Virtual 2048 768
EndSubSection
```

And this in my autostart.sh file:

```
xrandr --auto --output VGA-0 --mode 1024x768 --right-of DVI-0
```

In order to enable dual screens.


I don't really know what I'm doing. I installed fglrx from Restricted Drivers, then did:

```
    sudo aticonfig --initial=dual-head --screen-layout=right
```
and
```
    sudo aticonfig --dtop=horizontal --overlay-on=1
```

Now I can't really see the lower half of my screen apparently. I thought my panel was gone which is why I typed "tint2":
[img]http://img200.imageshack.us/img200/9004/2009072112481594731024x.png[/img]

When I maximize a window, the window seems to extrend to my other screen, which isn't working. The bottom also seems to extend down.
[img]http://www.acelayouts.com/uploads/images/2009-07-21/GXSzsvhQFa.png[/img]

By "my other screen isn't working", I mean, it's blank and when I move my cursor to it, my cursor turns into an 'x' and I can't move back to my other screen. 

Here's my xorg.
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "Default Screen" 0 0
    Screen         "aticonfig-Screen[0]-1" RightOf "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    Option        "" "DDX"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
    Option        "OverlayOnCRTC2" "0"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-1"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
    SubSection "Display"
        Virtual   2048 768
        Depth     24
        Modes    "1024x768" "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-1"
    Device     "aticonfig-Device[0]-1"
    Monitor    "aticonfig-Monitor[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

---

