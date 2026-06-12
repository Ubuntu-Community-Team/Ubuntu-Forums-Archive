---
title: "Nvidia TV-Out problem"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by dlkb1240 on 2007-03-03
Ok. I have followed all the beginners guides for a couple of days now and I still cant get my tv to dual display. Heres what I have in my Xorg.conf:
```
Section "ServerLayout"
   Identifier      "Basic Layout"
    Screen 0        "Screen0"
    Screen 1        "Screen1" RightOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
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
    Load           "i2c"
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
    Option         "XkbOptions" "lv3:ralt_switch"
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

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "Monitor" #CRT
        HorizSync       30-70
        VertRefresh     50-140
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier "Television" #TV
        HorizSync 30-50
        VertRefresh 60
EndSection

Section "Device"
        Identifier      "Device0"
        Driver          "nvidia"
        Screen 0
        Option  "RenderAccel"   "true"
        BusID   "PCI:01:00:0"
EndSection

Section "Device"
        Identifier      "Device1"
        Driver "nvidia"
        Screen 1
        Option        "TVOutFormat" "SVIDEO" #or SVIDEO etc 
   	Option        "TVStandard" "NTSC-M" #or NTSC etc 
   	Option        "ConnectedMonitor" "Television" 
        BusID   "PCI:01:00:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor"
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
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "Television"
        DefaultDepth    24 
        SubSection "Display"
                Depth 24
                Modes "1024x768_60"
        EndSubSection
EndSection

```

And heres the Xorg.log(the part that counts):
```
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.05.51
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     Philips 107S (CRT-0)
(--) NVIDIA(0): Philips 107S (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "Television"
(**) NVIDIA(1): Option "TVStandard" "NTSC-M"
(**) NVIDIA(1): Option "TVOutFormat" "SVIDEO"
(**) NVIDIA(1): Option "UseDisplayDevice" "Device1"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing SVIDEO output
(**) NVIDIA(1): TV Standard string: "NTSC-M"
(WW) NVIDIA(1): Invalid UseDisplayDevice string token: "Device1"; discarding
(WW) NVIDIA(1):     token.
(II) NVIDIA(1): NVIDIA GPU GeForce 6200 at PCI:1:0:0
(--) NVIDIA(1): VideoRAM: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.44.a2.05.51
(II) NVIDIA(1): Detected AGP rate: 8X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(1):     Philips 107S (CRT-0)
(--) NVIDIA(1): Philips 107S (CRT-0): 400.0 MHz maximum pixel clock
(EE) NVIDIA(1): Unable to find available Display Devices for screen 1.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(--) Depth 24 pixmap format is 32 bpp
```

Am I missing anything here? Thanks.

---

### Post by klyick on 2008-01-05
bump.

I have this same problem.

---

### Post by Plasma_NZ on 2008-03-13
He can u explain a in a little more detail wat your trying to achive ?? twinview ?? seperate xsessions ? clone mode..??

is it 2 screens ? like both crt or lcd ??   crt and a tv ?

also what video card.. which driver release..

---

