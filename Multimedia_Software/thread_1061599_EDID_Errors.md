---
title: "EDID Errors"
date: 2009-02-06
forum: Multimedia Software
---

### Post by WaLshy11 on 2009-02-06
Hey all,

I am having trouble with my screen resolutions, it is stuck on 1024x768 but I need it to go to 1680x1050. I have search and fiddled around and I think it comes down to the EDID error and Ubuntu not recognizing my screen.

This is the error I am getting in xorg.log:

```
(WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-0
(II) NVIDIA(0): NVIDIA GPU GeForce 8800 Ultra (G80) at PCI:7:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 786432 kBytes
(--) NVIDIA(0): VideoBIOS: 60.80.18.00.13
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8800 Ultra at
(--) NVIDIA(0):     PCI:7:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
``` 


I have tried to go to the 'Acquire EDID', so I can add a line in my xorg.conf file ```
Option "CustomEDID" "DFP-0:/etc/X11/EDID.bin
```  in nvidia-settings but there is no such button.

This is my xorg.conf file:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "CMV221D"
    Modeline       "1680x1050" 149.00  1680 1760 1944 2280  1050 1050 1052 1089
EndSection

Section "Device"
    Identifier     "NVIDIA 8800GTX Ultra"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA 8800GTX Ultra"
    Monitor        "CMV221D"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "ExactModeTimingsDVI" "TRUE"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

```


Can anyone please help me. I have been trying to get this right for about 2 weeks now through multiple posting and searching, finally got it down to this (I think) but I am stuck.

---

### Post by WaLshy11 on 2009-02-07
Bump. 

Please help, still not working :(

---

### Post by WaLshy11 on 2009-02-08
bump

---

### Post by rwreed on 2010-12-29
I know this is an old and dead thread, but after upgrading to 10.04 I also had this same problem. My Xorg log showed an EDID error and I had no Generate EDID button on my nvidia-settings screen for DFP-0. I have a dual monitor configuration on an Nvidia Geforce 7500LE. The vga cord is plugged into the CRT-0 (a NEC Multisync LCD 1530v) which worked fine and was correctly detected by the nvidia-settings screen. The DVI cord is plugged into a DELL 1703fps which it did not detect correctly and was limited to a 640x480 resolution. 

What I found is that while the DFP-0 settings did not have an EDID generate button the CRT-0 screen did. Once I generated the EDID.bin file using that, and added the line above 
```
Option "CustomEDID" "DFP-0:/etc/X11/EDID.bin
```
 my DVI (DFP-0) monitor worked correctly.

---

