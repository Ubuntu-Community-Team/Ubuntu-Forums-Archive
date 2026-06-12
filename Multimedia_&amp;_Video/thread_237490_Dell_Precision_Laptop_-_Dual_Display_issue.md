---
title: "Dell Precision Laptop - Dual Display issue"
date: 2006-08-16
forum: Multimedia &amp; Video
---

### Post by casperlingus on 2006-08-16
I have a Dell Precision M90 with an NVIDIA Quadro FX 2500 video card and I'm attempting to dual display with a Dell UltraSharp 2407WFP (yes, I know it's ridiculous).  

This works no problem in Windows.  Ubuntu, however, does not like the DVI output of the video card.  It works fine using the analog cable, but not DVI.  In fact, as far as I can tell, Ubuntu detects the DVI connection, and Windows proves that it works, but nothing shows up when I try to actually use it. 

Here's the seemingly-relevant parts of /var/log/Xorg.0.log:

```
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RandRRotation" "on"
**(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-1"**
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU Quadro FX 2500M at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.16.16
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro FX 2500M at PCI:1:0:0:
[B](--) NVIDIA(0):     Dell 2407WFP (CRT-0)
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0):     Dell 2407WFP (DFP-1)[/B]
(--) NVIDIA(0): Dell 2407WFP (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(--) NVIDIA(0): Dell 2407WFP (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): Dell 2407WFP (DFP-1): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1200"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(0): DPI set to (93, 92); computed from "UseEdidDpi" X config option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "UseDisplayDevice" "DFP-0"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU Quadro FX 2500M at PCI:1:0:0
(--) NVIDIA(1): VideoRAM: 524288 kBytes
(--) NVIDIA(1): VideoBIOS: 05.71.22.16.16
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on Quadro FX 2500M at PCI:1:0:0:
(--) NVIDIA(1):     Dell 2407WFP (CRT-0)
(--) NVIDIA(1):     Seiko (DFP-0)
(--) NVIDIA(1):     Dell 2407WFP (DFP-1)
(--) NVIDIA(1): Dell 2407WFP (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): Seiko (DFP-0): Internal Dual Link LVDS
(--) NVIDIA(1): Dell 2407WFP (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(1): Dell 2407WFP (DFP-1): Internal Single Link TMDS
(II) NVIDIA(1): Assigned Display Device: DFP-0
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "1920x1200"
(II) NVIDIA(1): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(1): DPI set to (131, 132); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8

...

(II) NVIDIA(0): Setting mode "1920x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "1920x1200"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources

```

And here's the relevant parts of my xorg.conf

```

Section "ServerLayout"
    Identifier     "Non-Default Layout"
    Screen         0 "Screen0" 0 0
    Screen         1 "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
    Option         "Xinerama" "On"
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


... ...


Section "Monitor"
    Identifier     "Monitor Dell"
    HorizSync       46.0 - 81.0
    VertRefresh     43.0 - 76.0
    #Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor Laptop"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    BoardName      "NVIDIA Quadro FX 2500"
    BusID          "PCI:1:0:0"
    Screen         0
**    Option         "UseDisplayDevice" "DFP-1"**
    #Option         "UseDisplayDevice" "CRT-0"
    Option         "RandRRotation" "on"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    BoardName      "NVIDIA Quadro FX 2500"
    BusID          "PCI:1:0:0"
    Screen         1
    Option         "UseDisplayDevice" "DFP-0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor Dell"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor Laptop"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection
```

Can this problem be explained?  I seems like Ubuntu just doesn't know how to actually send signals to the monitor, even though it knows it's there.

Casper...

---

### Post by casperlingus on 2006-08-16
Bump.

I've tried just about everything.  I've various combinations of monitors, and connections.  Using a docking station and not using it.  I would believe it's not possible except I've seen Windows do it without a hitch.

There must be an explanation for this.  There must be a solution too.  

Casper...

---

### Post by casperlingus on 2008-04-17
I don't know if it's relevant anymore (bug fixed in newer nvidia drivers?), but I found the solution to this problem.

Xorg.0.log was reporting the second monitor to be connected to DFP-1, and would automatically send second-monitor-stuff to DFP-1.  I tried explicitly selecting DFP-1, and it still didn't work.  Turns out the monitor was actually DFP-2, misreported by Xorg, and the option "UseDisplayDevice" "DFP-2" fixed all my problems.

Okay, well not all of them :)  but it got me to the next step.

-Casper

---

