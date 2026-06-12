---
title: "opengl doesnt work on gutsy with i810"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by endzeit42 on 2008-04-13
recently installed gutsy (7.10) and something is really wrong about opengl.
i run toshiba notebook with intel 852GM graphic.
the xserver itself runs quite ok, only thing to mentoin is that the flash videos in firefox are juddering for some seconds until they run smooth. didnt test normal videoplayback yet. i just came to this opengl conclusion because my program for internet tv complains about opengl and it judders really heavy when switching to fullscreen. so i started searching for the cause.

on feisty  (7.04) everything worked fine except that i had to turn off compiz to watch videos, when it was enabled.

i recognized that xorg doesnt use the i810 driver anymore, but some new "intel". its the only one that works for me, xserver doesnt starts up when i choose "i810".
second thing i noticed was that the xorg.conf has not that much content like in feisty anymore. the sections "module" and "files" are completly missing among some other things, i will paste the feisty and gutsy config at the end of the thread for illustration.

i tried using the feisty setting or even add the missing ones to gutsy, but nothing was successful. i tried dpkg-reconfigure xserver-xorg with no luck either, and i ve tried installing xorg-xgl (wondered is wasnt installed yet) with the result that everything was much worser, now it was really slow, so i made it unhappened.

of course i searched a bit about this topic before posting this thread, but atm im kinda confused. from the informations i could get i understood that theres a new intel driver and the old one is broken in some way.

so my questions are mainly:
1. where are the modules loaded in new xorg?
2. is there a working driver for my chipset, and where can i get it
3. or do we have to wait for a new driver?

feisty xorg.conf (comments and input devices cutted):
```

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
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

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Devi$
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Devi$
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

gutsy xorg.conf (comments and input devices cutted):
```

Section "Files"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Devi$
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Standardbildschirm"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Devi$
        Monitor         "Standardbildschirm"
        DefaultDepth    24
        SubSection "Display"
                Modes           "4095x4095" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```

---

