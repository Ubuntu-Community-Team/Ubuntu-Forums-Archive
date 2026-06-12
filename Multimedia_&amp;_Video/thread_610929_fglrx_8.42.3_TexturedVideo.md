---
title: "fglrx 8.42.3 TexturedVideo"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by dixon on 2007-11-12
Hi. 
Is TexturedVideo working for anybody? I discovered this feature just week ago. I didn't need it really before, but to be able to use the new feature in skype(webcam support) I need multiple xv ports. When I enable the texturedvideo option in xorg.conf the videos are ok in original size, but when I resize the video or switch to fullscreen the video is blocky(also the subtitles) and there's also some tearing visible.

I'm using Mobility R9700 with fglrx drivers(8.42.3).
Here's my xorg.conf
```

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
    Driver    "fglrx"
    Option    "VideoOverlay" "on"
    Option    "OpenGLOverlay" "off"
    Option     "TexturedVideo" "on"
    Option    "XaaNoOffscreenPixmaps" "on"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Všeobecný monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
    Monitor        "Všeobecný monitor"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Option          "AIGLX"         "true"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```Any help would be really appreciated :) THX

---

### Post by Yellow Pasque on 2007-11-13
Hi. Try adding more resolutions to the line where you have 1024x768 (800x600, 640x480, and bigger resolutions if your monitor supports them). I don't know if it's related to your problem, but it won't hurt anything so long as your monitor supports it.

---

