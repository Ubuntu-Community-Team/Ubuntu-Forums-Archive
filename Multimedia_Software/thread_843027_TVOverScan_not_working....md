---
title: "TVOverScan not working..."
date: 2008-06-27
forum: Multimedia Software
---

### Post by allene222 on 2008-06-27
My prototype worked with 'Option "TVOverScan"   "0.5"'  in the Device section of xorg.conf.  My new hardware is unaffected by any value of TVOverScan, even 1.0.  (TV CRT with SVIDEO input)

I probably have a little different driver configuration than most in that I have nvidia drivers disabled in the hardware driver section but they are being loaded by xorg.conf.  I don't really understand this, I just know that they are loaded by xorg and that the computer will not boot if I enable them in the nvidia control window.  I think there is a conflict between the nvidia driver and the air2pc cards.

TVOverScan should work.  I have seen it work, just not with this hardware.  I don't know what to do.  This is the last problem in the system that I know of.  Everything else is working.  I need to get the picture screen filled by the output.

My distribution is MythBuntu 8.04.  Video card is Ausu 6200.  MB is Asus M3A and CPU is AMD 5400+

I don't know what to do to get the picture larger.

Allen


Here is some of my xorg.conf:

    Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
    EndSection

    ---snip some stuff-----

    Section "Monitor"
        # HorizSync source: edid, VertRefresh source: edid
        Identifier     "Monitor0"
        VendorName     "Unknown"
        ModelName      "Panasonic AX-100"
        HorizSync       28.0 - 49.0
        VertRefresh     24.0 - 61.0
        Option         "DPMS"
    EndSection

    Section "Monitor"
        # HorizSync source: xconfig, VertRefresh source: xconfig
        Identifier     "Monitor1"
        VendorName     "Unknown"
        ModelName      "TV-0"
        HorizSync       28.0 - 49.0
        VertRefresh     24.0 - 61.0
        Option         "DPMS"
        Option         "TVOverScan"   "1.0"
    EndSection

    Section "Device"
        Identifier     "Videocard0"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce 6200 LE"
        BusID          "PCI:1:0:0"
        Option         "UseDisplayDevice" "DFP"
        Screen          0
    EndSection

    Section "Device"
        Identifier     "Videocard1"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce 6200 LE"
        BusID          "PCI:1:0:0"
        Option         "UseDisplayDevice" "TV-0"
        Screen          1
    EndSection

    Section "Screen"
        Identifier     "Screen0"
        Device         "Videocard0"
        Monitor        "Monitor0"
        DefaultDepth    24
        Option         "TwinView" "0"
        Option         "metamodes" "DFP: 1280x720_60 +0+0"
        SubSection     "Display"
            Depth       24
        EndSubSection
    EndSection

    Section "Screen"
        Identifier     "Screen1"
        Device         "Videocard1"
        Monitor        "Monitor1"
        DefaultDepth    24
        Option         "TwinView" "0"
        Option         "metamodes" "TV: nvidia-auto-select +0+0"
        SubSection     "Display"
            Depth       24
        EndSubSection
    EndSection

Here is some of the x log:

    (II) NVIDIA(0): Validated modes:
    (II) NVIDIA(0):     "nvidia-auto-select"
    (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
    (++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
    (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
    (**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
    (==) NVIDIA(1): RGB weight 888
    (==) NVIDIA(1): Default visual is TrueColor
    (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
    (**) NVIDIA(1): Option "TwinView" "0"
    (**) NVIDIA(1): Option "MetaModes" "TV: nvidia-auto-select +0+0"
    (**) NVIDIA(1): Option "TVOverScan" "1.0"
    (**) NVIDIA(1): Option "UseDisplayDevice" "TV-0"
    (**) NVIDIA(1): Enabling RENDER acceleration
    (II) NVIDIA(1): NVIDIA GPU GeForce 6200 LE (NV44) at PCI:1:0:0 (GPU-0)
    (--) NVIDIA(1): Memory: 524288 kBytes
    (--) NVIDIA(1): VideoBIOS: 05.44.02.67.01
    (II) NVIDIA(1): Detected PCI Express Link width: 16X
    (--) NVIDIA(1): Interlaced video modes are supported on this GPU
    (--) NVIDIA(1): Connected display device(s) on GeForce 6200 LE at PCI:1:0:0:
    (--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
    (--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
    (--) NVIDIA(1): TV encoder: NVIDIA
    (II) NVIDIA(1): Assigned Display Device: TV-0
    (II) NVIDIA(1): Validated modes:
    (II) NVIDIA(1):     "TV:nvidia-auto-select+0+0"
    (II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
    (++) NVIDIA(1): DPI set to (100, 100); computed from -dpi X commandline option
    (==) NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
    (--) Depth 24 pixmap format is 32 bpp

---

### Post by allene222 on 2008-06-28
I am told that TVOverScan no longer works, that it is "depreciated"

This does what I want when entered on a terminal:
"nvidia-settings -a TVOverScan[TV-0]=12"

I want to put this in a file so it runs automatically when X starts.  None of the instructions on the man page work.

What file can I put this command in on mythbuntu 8.04 so it will run at startup of X?

Allen

---

