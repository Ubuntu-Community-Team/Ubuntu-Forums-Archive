---
title: "No support for 1650x1050 Quadro4 980 XL"
date: 2008-07-30
forum: Multimedia Software
---

### Post by pormogo on 2008-07-30
So I can't seem to get my box to recognize my monitors recommended resolution. When I check the /var/log/Xorg.0.log file I see the following. 

```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU Quadro4 980 XGL at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.28.20.19.15
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro4 980 XGL at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): External Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
**(WW) NVIDIA(0): No valid modes for "1680x1050"; removing.**
(WW) NVIDIA(0):
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0):
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
(WW) NVIDIA(0):     UBB.
```

So I went ahead and found a modeline for a 1680*1050 monitor, but that didn't seem to change anything (I appended my monitor and screen settings as shown below).

[i]Section "Monitor"
        Identifier      "Configured Monitor"
        ModeLine     "1680x1050@60"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals"     "True"
        SubSection "Display"
                Viewport                0 0
                Depth                   24
                Modes                   "1680x1050"
        EndSubSection
EndSection[/i]

But once X starts it still defaults back to 1600x1200, does my quadro not support this monitors resolution? I am using Nvidias binary driver. Any help is most appreciated.

Oddly enough xrandr seems to think my monitor can't display that resolution (although that doesn't stop my monitor from complaining about it anytime I turn it on).

```
darthbator@adamantium:~$ xrandr
Screen 0: minimum 320 x 240, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200      50.0*
   1600x1024      51.0
   1440x900       52.0
   1400x1050      53.0     54.0     55.0
   1280x1024      56.0     57.0
   1280x960       58.0
   1280x800       59.0
   1280x768       60.0
   1152x864       61.0
   1024x768       62.0     63.0     64.0
   960x600        65.0
   840x525        66.0
   832x624        67.0
   800x600        68.0     69.0     70.0     71.0     72.0     73.0
   800x512        74.0
   720x450        75.0
   640x512        76.0     77.0
   640x480        78.0     79.0     80.0     81.0
   640x400        82.0
   640x384        83.0
   576x432        84.0
   512x384        85.0     86.0     87.0
   416x312        88.0
   400x300        89.0     90.0     91.0     92.0
   320x240        93.0     94.0     95.0
```

---

