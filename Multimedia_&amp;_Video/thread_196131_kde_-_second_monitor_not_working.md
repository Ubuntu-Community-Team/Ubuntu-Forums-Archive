---
title: "kde - second monitor not working"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by dmonty on 2006-06-13
I have two monitors side-by-side so that I can drag applications between the two screens.

After upgrading to Dapper my second monitor stopped working in KDE. However the dual screens work fine in Gnome.

I tried switching between gdm and kdm but that made no difference.

However KDE works fine if I start kde from the command line without using kdm/gdm: 
```

xinit /usr/bin/ssh-agent /usr/bin/startkde --

```

I like kde with dual screens.  I do not want to have to always use command line to start kde.

I've tried changing xorg.conf's xinerama, dri, clone, horizontal etc etc but it does not make much difference.  It must be something in the kde and display manager.

```

Section "ServerLayout"
        Identifier     "DualHead"
        #Screen         "Primary Screen" 0 0
        Screen         "Primary Screen"
        Screen          "Secondary Screen" RightOf "Primary Screen"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        #Option         "Xinerama" "on"
        Option "Clone" "off"
EndSection

Section "Files"
                        # local font server
        # if the local font server has problems, we can fall back on these
#       FontPath        "/usr/lib/X11/fonts/cyrillic"
#       FontPath        "/usr/lib/X11/fonts/CID"
        FontPath     "unix/:7101"
        FontPath     "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/lib/X11/fonts/100dpi"
        FontPath     "/usr/lib/X11/fonts/75dpi"
        FontPath     "/usr/lib/X11/fonts/misc"
        FontPath     "/usr/lib/X11/fonts/Type1"
EndSection

Section "Module"
        Load  "bitmap"
        Load  "dbe"
        Load  "ddc"
        Load  "dri"
        Load  "evdev"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "record"
        Load  "type1"
        Load  "v4l"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "keyboard"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "Emulate3Buttons" "false"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
        Identifier   "Acer Primary"
        HorizSync    30.0 - 65.0
        VertRefresh  50.0 - 75.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "Acer Secondary"
        HorizSync    30.0 - 65.0
        VertRefresh  50.0 - 75.0
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Radeon Primary"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        BusID       "PCI:6:00:0"
EndSection

Section "Device"
        Identifier  "ATI Radeon Secondary"
        Driver      "fglrx"
        BusID       "PCI:6:00:1"
EndSection

Section "Screen"
        Identifier "Primary Screen"
        Device     "ATI Radeon Primary"
        Monitor    "Acer Primary"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Secondary Screen"
        Device     "ATI Radeon Secondary"
        Monitor    "Acer Secondary"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection


```

---

### Post by tronica on 2006-06-13
shouldn't this be uncommented

> #Screen         "Primary Screen" 0 0

for me this is uncommented. just a thought

---

### Post by alarson on 2006-06-18
I can confirm what dmonty said.  This is definitely a KDE thing, because prior to logging on, I can move the mouse between both monitors, and if I login "failsafe", both monitors work fine.  Its just when KDE is started by either kdm or gdm that the windows are restricted to the first monitor.  Also, interestingly enough, part of the mouse still does appear on the second monitor even after a KDE login, but only as much of the mouse pointer as shows when the mouse "point" is still in the first monitor.

Couple with a failed upgrade, then (after a clean install) a broken printer setup and KDE dapper is turning out to be less than stellar.

---

### Post by degel3030 on 2006-06-19
hi, i have this same problem but with ubuntu and 2 different monitors, when the login screen is there they both work, and when i log in they dont, im on my way out but ill shoot up my info when i get back tonight if needed

---

