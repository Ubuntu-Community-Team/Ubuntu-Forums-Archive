---
title: "Nvidia Flickering"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by MemoryDump on 2007-08-24
I noticed since installing Feisty and the latest Nvidia  drivers using a HowTo posted on these forums that my screen seems to flicker.

Here's my Hardware:

- Nvidia GeForce 7800 GS (AGP)
- Samsung 22" Widescreen LCD Monitor (226BW)
- Logitech MX700 wireless mouse
- Microsoft Intellimouse (backup mouse)
- Microsoft Natural® Ergonomic Keyboard 4000

Here is my Xorg.conf
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"

        Option          "AIGLX"         "true"
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

Section "ServerFlags"
    Option         "Xinerama" "0"
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
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Name"  "Logitech USB Receiver"
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
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GS"

#       Option  "AddARGBGLXVisuals" "True"
#       Option "AllowGLXWithComposite" "True"
#       Option "DisableGLXRootClipping" "True"
#       Option "DamageEvents" "True"
#       Option "UseEvents" "False"
#       Option "TripleBuffer" "True"
#       Option "BackingStore" "True" 
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050_60 +0+0"
    Option         "AddARGBGLXVisuals" "True"

    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

I had inserted some other variables I had found on another post, however I didn't see it making much of a difference (if any at all) so I just commented them out.

I do have compiz=fusion running, but I was noticing this "flickering" before even loading it.

Am I missing something? As far as I can see I have everything setup as best as it can be for my card/monitor I have. I didn't have this flickering happening when I was running XP/SP2.

thanks
-MD :D

---

### Post by tseliot on 2007-08-24
try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

