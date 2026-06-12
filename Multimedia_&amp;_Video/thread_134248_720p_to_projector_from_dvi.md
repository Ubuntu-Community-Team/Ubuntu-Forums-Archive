---
title: "720p to projector from dvi"
date: 2006-02-21
forum: Multimedia &amp; Video
---

### Post by Viktor on 2006-02-21
Hi!
I have an Nvidia FX 5200 card and currntly I use an LCD on the VGA-output. I have been trying to hook up my video projector, hitachi tx200, to my dvi output. The problem is that I only get out 640x480. But the resolution on the projector is 1280x720.
Is there anyone that knows ssomething about this or have done something similar with greater success than me?
I post a copy of my xorg.conf so you can see what I've done so far.

What should I do to get 1280x720 to the projector ?

Section "ServerLayout"
    Identifier     "Standard Layout"
    Screen 0       "Screen0"  LeftOf "Screen1"
    Screen 1	   "Screen1" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    Option  	   "Xinerama" "off"
    Option         "Clone" "off"
EndSection

Section "Files"

        # paths to defoma fonts
    
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
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
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       31.5 - 80.0
    VertRefresh     59.9 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
Identifier "Projector"
#HorizSync       28.00 - 33.00
#VertRefresh     43.00 - 72.00
Modeline "1280x720@50" 59.42 1280 1312 1536 1568 720 735 741 757 +hsync +vsync
Modeline "1280x720@60" 73.78 1280 1312 1592 1624 720 735 742 757 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
     Screen 1
     Option "NoDDC" "1"
     Option "IgnoreEDID" "1" #"yes"
     Option "UseEdidFreqs" "0" #"false"
     Option "TVStandard" "HD720p"
     BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
     Screen 0
     #Option "NoDDC" "1"
     #Option "IgnoreEDID" "yes"
     #Option "UseEdidFreqs" "false"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
Identifier "Screen1"
Device "Videocard1"
Monitor "Projector"
#Option "TVStandard" "HD720p"
Option "ConnectedMonitor" "DFP"
Option "ExactModeTimingsDVI" "True"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x720@60"
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
Modes "1280x720@60"
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 15
Modes "1280x720@60"
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 8
Modes "1280x720@60"
EndSubSection
EndSection

#Section "DRI"
#Group 0
#Mode 0666
#EndSection

---

