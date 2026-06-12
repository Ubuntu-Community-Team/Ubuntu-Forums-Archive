---
title: "Matrox M9148 Quad-head Problems"
date: 2013-06-30
forum: Multimedia Software
---

### Post by jabeavers on 2013-06-30
I started a thread on this topic on askubuntu ([http://askubuntu.com/questions/314167/cant-get-matrox-quad-head-working](http://askubuntu.com/questions/314167/cant-get-matrox-quad-head-working)), but no answer. I will, therefore, ask here. This is what the other post says:

I have xubuntu 13.04 newly installed. I'm trying to get my Matrox M9148 gpu to work. I'm loosely following the instructions here: [ftp://ftp.matrox.com/pub/mga/archive/linux/2013/1.4.1/README.txt](ftp://ftp.matrox.com/pub/mga/archive/linux/2013/1.4.1/README.txt)  I had to create and edit an xorg.conf file, and now the card outputs to all monitors, but no program windows display, even though they are there and I can interact with them. It's like their alpha is set to 0. Even the login screen window is gone, only the background image is present, and the desktop icons if I login. Also, the mouse will travel to the other monitor, but changes to an X, and the cursor is duplicated on screen 0 as an X.


Here's xorg.conf:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen3"
    Screen      3  "Screen3" Below "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option      "Protocol" "auto"
    Option      "Device" "/dev/input/mice"
    Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor3"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"               # [<bool>]
        #Option     "SWcursor"              # [<bool>]
        #Option     "Independent"           # [<bool>]
        #Option     "UseKernelModule"       # [<bool>]
        #Option     "mon0_forcedvi"         # [<bool>]
        #Option     "mon1_forcedvi"         # [<bool>]
        #Option     "mon2_forcedvi"         # [<bool>]
        #Option     "mon3_forcedvi"         # [<bool>]
        #Option     "ICDOP1"                # [<bool>]
        #Option     "ICDOP2"                # [<bool>]
    Identifier  "Card0"
    Driver      "m9x"
    BusID       "PCI:1:0:0"
        Screen      0
        Option      "Independent"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"              # [<bool>]
        #Option     "kmsdev"                # <str>
        #Option     "ShadowFB"              # [<bool>]
    Identifier  "Card1"
    Driver      "m9x"
    BusID       "PCI:1:0:0"
        Screen      1
        Option      "Independent"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"              # [<bool>]
        #Option     "Rotate"                # <str>
        #Option     "fbdev"                 # <str>
        #Option     "debug"                 # [<bool>]
    Identifier  "Card2"
    Driver      "m9x"
    BusID       "PCI:1:0:0"
        Screen      2
        Option      "Independent"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"              # [<bool>]
        #Option     "DefaultRefresh"        # [<bool>]
        #Option     "ModeSetClearScreen"    # [<bool>]
    Identifier  "Card3"
    Driver      "m9x"
    BusID       "PCI:1:0:0"
        Screen      3
        Option      "Independent"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
EndSection

Section "Screen"
    Identifier "Screen3"
    Device     "Card3"
    Monitor    "Monitor3"
EndSection
```

---

### Post by jabeavers on 2013-07-08
Well, I got it working, but not like I wanted. I use xrandr in ~/.xprofile to setup the screens when I login, which is fine, but I don't understand why it won't work in xorg.conf.

Here's my .xprofile:

    ```
xrandr --output mon0 --pos 528x0
    xrandr --output mon1 --right-of mon0
    xrandr --output mon2 --below mon1
    xrandr --output mon3 --left-of mon2 

And here's what I ended up with in xorg.conf:

        Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
    EndSection
    
    Section "Module"
        Load  "glx"
    EndSection
    
    Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
    EndSection
    
    Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option        "Protocol" "auto"
        Option        "Device" "/dev/input/mice"
        Option        "ZAxisMapping" "4 5 6 7"
    EndSection
    
    Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
    EndSection
    
    Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
    #    Option "RightOf" "Monitor0"
    EndSection
    
    Section "Monitor"
        Identifier   "Monitor2"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
    #    Option    "Below" "Monitor1"
    EndSection
    
    Section "Monitor"
        Identifier   "Monitor3"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
    #    Option "Below" Monitor0"
    EndSection
    
    Section "Device"
            ### Available Driver options are:-
            ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
            ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
            ### <percent>: "<f>%"
            ### [arg]: arg optional
            #Option     "NoAccel"                # [<bool>]
            #Option     "SWcursor"               # [<bool>]
            #Option     "Independent"            # [<bool>]
            #Option     "UseKernelModule"        # [<bool>]
            #Option     "mon0_forcedvi"          # [<bool>]
            #Option     "mon1_forcedvi"          # [<bool>]
            #Option     "mon2_forcedvi"          # [<bool>]
            #Option     "mon3_forcedvi"          # [<bool>]
            #Option     "ICDOP1"                 # [<bool>]
            #Option     "ICDOP2"                 # [<bool>]
        Identifier  "Card0"
        Driver      "m9x"
        BusID       "PCI:1:0:0"
    #    Option        "Independent"
    EndSection
    
    Section "Device"
            ### Available Driver options are:-
            ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
            ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
            ### <percent>: "<f>%"
            ### [arg]: arg optional
            #Option     "SWcursor"               # [<bool>]
            #Option     "kmsdev"                 # <str>
            #Option     "ShadowFB"               # [<bool>]
        Identifier  "Card1"
    #    Driver      "modesetting"
        Driver      "m9x"
        BusID       "PCI:1:0:0"
    #    Option "Independent"
    EndSection
    
    Section "Device"
            ### Available Driver options are:-
            ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
            ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
            ### <percent>: "<f>%"
            ### [arg]: arg optional
            #Option     "ShadowFB"               # [<bool>]
            #Option     "Rotate"                 # <str>
            #Option     "fbdev"                  # <str>
            #Option     "debug"                  # [<bool>]
        Identifier  "Card2"
    #    Driver      "fbdev"
        Driver "m9x"
        BusID       "PCI:1:0:0"
    #    Option "Independent"
    EndSection
    
    Section "Device"
            ### Available Driver options are:-
            ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
            ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
            ### <percent>: "<f>%"
            ### [arg]: arg optional
            #Option     "ShadowFB"               # [<bool>]
            #Option     "DefaultRefresh"         # [<bool>]
            #Option     "ModeSetClearScreen"     # [<bool>]
        Identifier  "Card3"
        Driver      "m9x"
        BusID       "PCI:1:0:0"
    #    Option        "Independent"
    EndSection
    
    Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 24
        SubSection "Display"
            Viewport   0 0
            Depth     1
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     4
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     8
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     15
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     16
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     24
            Modes    "1680x1050" "1600x1200" "1400x900" "1280x800" "1280x768" "1152x864" "1024x768"
        EndSubSection
    EndSection
    
    Section "Screen"
        Identifier "Screen1"
        Device     "Card1"
        Monitor    "Monitor1"
        DefaultDepth 24
        SubSection "Display"
            Viewport   0 0
            Depth     1
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     4
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     8
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     15
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     16
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     24
            Modes    "1680x1050" "1600x1200" "1400x900" "1280x800" "1280x768" "1152x864" "1024x768"
        EndSubSection
    EndSection
    
    Section "Screen"
        Identifier "Screen2"
        Device     "Card2"
        Monitor    "Monitor2"
        DefaultDepth 24
        SubSection "Display"
            Viewport   0 0
            Depth     1
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     4
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     8
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     15
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     16
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     24
            Modes    "1680x1050" "1600x1200" "1400x900" "1280x800" "1280x768" "1152x864" "1024x768"
        EndSubSection
    EndSection
    
    Section "Screen"
        Identifier "Screen3"
        Device     "Card3"
        Monitor    "Monitor3"
        DefaultDepth 24
        SubSection "Display"
            Viewport   0 0
            Depth     1
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     4
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     8
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     15
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     16
        EndSubSection
        SubSection "Display"
            Viewport   0 0
            Depth     24
            Modes    "1680x1050" "1600x1200" "1400x900" "1280x800" "1280x768" "1152x864" "1024x768"
        EndSubSection
    EndSection
    
    Section "ServerLayout"
        Identifier     "QuadScreen"
        Screen      0  "Screen0" 528 0
        Screen      1  "Screen1" 1681 0
        Screen      2  "Screen2" 1681 865
        Screen      3  "Screen3" 0 865
        Option        "Xinerama"   "true"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
    EndSection
```

I wish I could get X to work by itself without needing the xrandr stuff, but on the login screen, it looks like all all of the screens are there but just stacked up on top of each other and are mirrored/duplicated on all of the monitors.

No big deal right now because it's working, but if anyone has any clues, I'd love to hear them....

---

