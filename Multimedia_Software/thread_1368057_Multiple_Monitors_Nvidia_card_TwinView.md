---
title: "Multiple Monitors: Nvidia card TwinView"
date: 2009-12-30
forum: Multimedia Software
---

### Post by lithium85 on 2009-12-30
Hello there,

I am using Ubuntu 9.10 (64bit) with an NVidia Graphics card (driver version 185.18.36) on a Laptop. In addition to the integrated Laptop DFP (1600x1050) I want to use another external screen (CRT, 1920x1080). I want them to be set up like this:

1) If the external CRT is connected:
Have one big ("virtual") Desktop (1920 x 1050+1080) with the CRT arranged above the DFP.

2) If the external CRT is not connected:
Have only the DFP running with a Desktop with Dimension of the DFP (1600x1050)

I managed to do 1) correctly using nvidias Twinview:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: 1680x1050 +0+1080, CRT: nvidia-auto-select +0+0; DFP: 1680x1050 @ 1680x1050"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```2) Basically does work as well, with one caveat:
Even if the CRT is not connected, the virtual desktop size is 1920x2130 pixels. So many windows/applications (as for example gnome notification events) get lost on the inaccessible upper part of the virtual desktop.

The reason for this is found in the nvidia driver documentation
([http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-g.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-g.html))

```
How are virtual screen dimensions determined in TwinView?

After all requested modes have been validated, and the offsets for each MetaMod$

Note that one side effect of this is that the virtual width and virtual height $

    "1600x1200,NULL; 1024x768+0+0, 1024x768+0+768"

the resulting virtual screen size will be 1600 x 1536.
```So even if my CRT is not connected the metamode using both screens is still 'validated' (whatever that means) by the nvidia driver. So what happens is this (Xorg.log)

```
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, DFP-0
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP:1680x1050+0+1080,CRT:nvidia-auto-select+0+0"
(II) NVIDIA(0):     "DFP:1680x1050@1680x1050"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 2130

```Any Ideas what I can do to set it up like I want? 
Can I force the nvidia driver to not validate the mode that is not working?
Can this be done using XRandR even with Nvidia graphic adapters?
I mean I could write some script that changes my xorg.conf on startup depending on whether the external screen is connected or not, but I dont really want to do this...

Hope anyone read through this thread and has an idea,

Cheers
bernhard

---

