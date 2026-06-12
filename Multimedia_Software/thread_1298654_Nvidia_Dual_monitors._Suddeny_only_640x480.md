---
title: "Nvidia Dual monitors. Suddeny only 640x480"
date: 2009-10-23
forum: Multimedia Software
---

### Post by falkaholic on 2009-10-23
Hi,

I am running a 9800GT in TwinView in 9.04. Using two identical Acer LCDs. I think a recent update might have done something to my set up. 

nvidia-settings shows one monitor and "DFP-0" that only has VGA a maximum.

I've tried nvidia-xconfig, reinstalling the 180 driver, reboots/shutdowns, etc. Monitors work fine in Windows, so its not a hardware thing.

My xorg.log has this interesting passage:

```

(**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +1440+0, DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-1"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-0
(II) NVIDIA(0): NVIDIA GPU GeForce 9800 GT (G92) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 1048576 kBytes
(--) NVIDIA(0): VideoBIOS: 62.92.52.00.b1
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9800 GT at PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0):     Acer AL1916W (DFP-1)
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(--) NVIDIA(0): Acer AL1916W (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Acer AL1916W (DFP-1): Internal Dual Link TMDS
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
(II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):    
(II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1440+0,DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 2080 x 900
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp

```

Any clues on how to fix this?

---

