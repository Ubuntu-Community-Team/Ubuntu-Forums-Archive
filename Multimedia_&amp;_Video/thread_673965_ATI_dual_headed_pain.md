---
title: "ATI dual headed pain"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by [XAP]Bob on 2008-01-21
I've been running dual monitors for several years now, initially within the evil empire, but for a few years now under various flavours of linux.

However I have a new (to me) machine with an ATI X850XT graphics card, and a pair of new monitors (one of my old ones went pop so it's brother is finding a nice new home).
The monitors are 22" 1680x1050 beasties, and very nice too (albeit I'm bit disapointed by the vertical viewing angle not being as advertised).

I have them wall mounted, side by side in portrait format with the tops together in the middle.

All very well and good - my setup at work has had a pair of 1280x1024's in portrait mode, driven by an nvidia card, for a while, so I think what I'm trying to do should be possible.


I'm struggling to get the monitors to do anything sensible even one at a time...


With a simple xorg.conf (Aiming for a single monitor 1680x1050 rotated):
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "ati0"
        Driver          "ati"
        BusID           "PCI:4:0:0"
        Screen          0
        Option "RandRRotation" "on"
        Option "RandR" "on"
        Option "DRI" "off"
EndSection

Section "Monitor"
        Identifier      "monitor0"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "screen0"
        Device          "ati0"
        Monitor         "monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
        Option         "Rotate" "left"
        Option "RandRRotation" "on"
        Option "RandR" "on"
EndSection

Section "ServerLayout"
        Identifier      "layout0"
        Screen          0       "screen0"       0       0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option "RandRRotation" "on"
        Option "RandR" "on"
EndSection

Section "ServerFlags"
    Option      "DefaultServerLayout" "layout0"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection

```

I end up with cloned, non rotated 1680x1050.

And the following excerpts from Xorg.0.log
```
(==) Using config file: "/etc/X11/xorg.conf"
(**) Option "defaultserverlayout" "layout0"
(**) ServerLayout "layout0"
(**) |-->Screen "screen0" (0)
(**) |   |-->Monitor "monitor0"
(**) |   |-->Device "ati0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) Option "RandR" "on"

```
```
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "RandRRotation" is not used
(WW) RADEON(0): Option "RandR" is not used
(WW) RADEON(0): Option "Rotate" is not used
(--) RandR disabled
```
```
(EE) AIGLX: Screen 0 is not DRI capable
```

Anyone got any ideas where I'm going so horribly wrong?

Cheers

---

