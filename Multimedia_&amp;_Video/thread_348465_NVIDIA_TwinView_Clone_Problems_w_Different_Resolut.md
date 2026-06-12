---
title: "NVIDIA TwinView Clone Problems w/ Different Resolutions"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by ShiftyPowers on 2007-01-28
Hey all, 

Been searching for an answer to my problem around the entire Net and finally exhausted my sources.  I currently am trying to set up a dual head CLONE config using Nvidia TwinView for my HTPC setup.  I can get the system to output clone mode to both screens but the resolution on the second monitor (the projector) is not 1280x720 as it should be.  The first monitor (the LCD TV) is fine.

Here is what I have in the system
Adapter: Nvidia FX 6200
Display 1: Samsung 40" LCD TV connected via VGA cable (resolution 1360x768)
Display 2: Panasonic Projector connected via DVI cable (resolution 1280x720)
OS: Ubuntu Edgy
Driver: latest Nvidia binary driver 9xxx

So here's a copy of what I currently have in my xorg.conf:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "AX100U"
    HorizSync       28.0 - 49.0
    VertRefresh     24.0 - 61.0
    ModeLine       "1280x720" 76.1 1280 1406 1542 1664 720 721 724 746 -hsync +vsync
#    Option         "VendorName" "ATI Proprietary Driver"
#    Option         "ModelName" "Generic Autodetecting Monitor"
    Option         "DPMS" "true"
EndSection

Section "Device"
    Identifier     "NVIDIA 6200"
    Driver         "nvidia"
    Option         "UseEvents" "True"
    Option "NoLogo" "1"
    Option "NoPowerConnectorCheck" 
    Option "TwinView" "True"
    Option "TwinViewOrientation" "Clone"
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1360x768,1280x720"
#    Option "ConnectedMonitor" "CRT,DFP"
#    Option "UseDisplayDevice" "CRT-0,DFP-0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA 6200"
    Monitor        "AX100U"
    DefaultDepth   24
    Option         "VideoOverlay" "on"
    Option         "OpenGLOverlay" "off"
    Option         "IgnoreEDID" "on"
    Option         "UseEvents" "True"
    SubSection     "Display"
        Viewport   0 0
        Depth       24
        Modes      "1360x768" "1280x720" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Section "ServerLayout"
Identifier "TwinView Configuration"
Screen 0 "Default Screen" 0 0
InputDevice "Configured Mouse"
InputDevice "Generic Keyboard"
Option "Xinerama" "Off"
EndSection

```

This is getting very frustrating.  I can't get TwinView to display different resolutions to each of the screens.  Any ideas?

---

### Post by ShiftyPowers on 2007-01-29
ok, did some checking, i suspect that cloning actually does not allow for different resolutions on the same card given that you are using the same framebuffer.   Is that true?

---

