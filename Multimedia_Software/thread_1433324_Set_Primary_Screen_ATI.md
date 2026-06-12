---
title: "Set Primary Screen ATI"
date: 2010-03-18
forum: Multimedia Software
---

### Post by ahmet00000000 on 2010-03-18
Hi,

I'm using a Monitor and a LCD TV.
How can I set my Monitor as my primary screen? For example if I open a Youtube Video in Fullscreen mode it always plays on my Monitor, but I want it to play it on the LCD TV.

My xorg.conf

[HTML]Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   2560 1024
        Depth     24
    EndSubSection
EndSection
[/HTML]My HardInfo (Display)

[HTML]
Display:

Resolution                 1280x1024 pixels
Vendor                      The X.Org Foundation
Version                     1.6.4

Monitors:

Monitor 0                    1280x1024 pixel

Extensions
AMDXVOPL
ATI-GLX
ATIFGLEXTENSION
ATIFGLRXDRI
ATITVOUT
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-DRI
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
XVideo-MotionCompensation
glesx

OpenGL:

VendorATI Technologies Inc.
RendererATI Radeon HD 3300 Graphics
Version2.1.9016
Direct RenderingYes
[/HTML]

---

### Post by markbuntu on 2010-03-19
Put the lcd to the left in the monitor layout. Flash defaults to position 0,0 for full screen which is the upper left corner of the left display. People have been complaining about this for years but adobe is not interested in doing anything about it first claiming that it is a security feature and then dismissing it as trivial/not important and erasing all bug reports/complaints about it.

Somebody at adobe is just being a real jerk about this.

EDIT: There is this long running thread here.

[http://ubuntuforums.org/showthread.php?t=884161](http://ubuntuforums.org/showthread.php?t=884161)

---

