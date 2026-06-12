---
title: "Can't get movie onto tv screen"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by littlespy on 2007-04-25
I set up my xorg.conf to use 2 screens one for my tv using svideo out and my main monitor.  The other screen shows up fine and I think my xorg.conf is setup correct.  However when I try to drag a movie onto the other screen(tv) it won't let me do it and it will stop the mouse cursor at the right of my monitor.  I'm sure there is an easy solution.  I tried to google around a bit but couldn't find what I was looking for.  My graphics card is geforce 8800 gts.

My xorg.conf

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0 "Screen[0]" 
    Screen 1 "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
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
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Monitor[0]"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor[1]"
    HorizSync           30-50
    VertRefresh         60 
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS]"
    Driver         "nvidia"
    screen 0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS][SVIDEO]"
    Driver         "nvidia"
        Screen 1 
        Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc 
        Option          "TVStandard" "NTSC" #or NTSC etc 
        Option          "ConnectedMonitor" "Monitor[1]" 
        BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "nVidia Corporation G80 [GeForce 8800 GTS]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen" 
        Device "nVidia Corporation G80 [GeForce 8800 GTS][SVIDEO]" 
        Identifier "Screen[1]" 
        Monitor "Monitor[1]" 
        DefaultDepth 24 
        SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
        EndSubSection    
EndSection

```

---

