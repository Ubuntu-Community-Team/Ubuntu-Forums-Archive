---
title: "no correct video output with ga-73pvm-s2h"
date: 2009-12-21
forum: Multimedia Software
---

### Post by sonfrau on 2009-12-21
Hi!

I have installed Kubuntu 9.10

I have got connected a Monitor on the VGA output and my Panasonic TV on my HDMI output.

When I start Kubuntu I just see video on my Monitor, no video on TV.

If I disconnect the VGA output I have video on my TV.

How can I configure my xorg.conf to fix this behaviour?

This is a truncated output of /var/log/Xorg.0.log:

(--) NVIDIA(0): Interlaced video modes are supported on this GPU                                                                               
(--) NVIDIA(0): Connected display device(s) on GeForce 7100 / nForce 630i at                                                                   
(--) NVIDIA(0):     PCI:0:16:0:                                                                                                                
(--) NVIDIA(0):     LG L196WTQ (CRT-0)                                                                                                         
(--) NVIDIA(0):     PANASONIC-TV (DFP-0)                                                                                                       
(--) NVIDIA(0): LG L196WTQ (CRT-0): 350.0 MHz maximum pixel clock                                                                              
(--) NVIDIA(0): PANASONIC-TV (DFP-0): 165.0 MHz maximum pixel clock                                                                            
(--) NVIDIA(0): PANASONIC-TV (DFP-0): Internal Single Link TMDS                                                                                
(II) NVIDIA(0): Assigned Display Device: CRT-0                                                                                                 
(==) NVIDIA(0):                                                                                                                                
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"                                                                 
(==) NVIDIA(0):     will be used as the requested mode.                                                                                        
(==) NVIDIA(0):                                                                                                                                
(II) NVIDIA(0): Validated modes:                                                                                                               
(II) NVIDIA(0):     "nvidia-auto-select"                                                                                                       
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900

and my xorg.conf:

/etc/X11/xorg.conf

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
EndSection

Thanks a lot.

---

