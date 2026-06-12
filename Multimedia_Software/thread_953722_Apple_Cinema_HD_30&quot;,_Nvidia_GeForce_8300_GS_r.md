---
title: "Apple Cinema HD 30&quot;, Nvidia GeForce 8300 GS rev 161 increase screen resolution"
date: 2008-10-20
forum: Multimedia Software
---

### Post by joshjdevl on 2008-10-20
Ubuntu 8.04
Apple Cinema HD 30"
nVidia Corporation GeForce 8300 GS rev 161
nVidia Driver version 177.80

I see the following in my log
"(WW) NVIDIA(0): No valid modes for "2560x1600_60"; removing."


I'm unable to increase my screen resolution past 1280x800. There is no higher option available in the change resolution. I would like to use the resolution 2560x1600 as this is the recommended and max resolution I can use for this monitor.

my xorg.conf

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    HorizSync      49.000-98.000
    VertRefresh    60.000
    Option         "DPMS"
        Modeline "2560x1600_60.00"  348.16  2560 2752 3032 3504  1600 1601 1604 1656  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
        Option          "UseEdidFreqs"
        Option          "ExactModeTimingsDVI"
        Option          "NoLogo"
        Option          "NoBandWidthTest"
        Option          "AllowGLXWithComposite"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "2560x1600_60"
    EndSubSection
EndSection






My log
(II) NVIDIA(0): NVIDIA GPU GeForce 8300 GS (G86) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.49.00.19
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8300 GS at PCI:1:0:0:
(--) NVIDIA(0):     Apple Cinema HD (DFP-0)
(--) NVIDIA(0): Apple Cinema HD (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): Apple Cinema HD (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "2560x1600_60"; removing.
(WW) NVIDIA(0):
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0):
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (50, 50); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

---

### Post by joshjdevl on 2008-10-22
geforce 8300 is only single link dvi.

I upgraded to an 8600 (dual link dvi) and reinstalled drivers and it works now.

---

