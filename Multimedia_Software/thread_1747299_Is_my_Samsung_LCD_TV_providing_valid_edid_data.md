---
title: "Is my Samsung LCD TV providing valid edid data?"
date: 2011-05-02
forum: Multimedia Software
---

### Post by fsallstrom on 2011-05-02
Hello
I have been struggeling to get HDMI output work with to my Samsung LCD TV (Samsung LE40F) without success. I am running Ubuntu 11.4 on an eeebox with Nvidia Ion 2 video chipset. I have installed the proprietary Nvidia drivers and everything seems to work fine, except HDMI. I can connect the TV through VGA and get full 1080 resolution but when connecting through HDMI I get nothing. The LCD TV never picks up the signal.

I have managed to get the nvidia Xserver control panel detect the LCD TV (connected through HDMI while at the same time connecting my LG screen through VGA) but nothing gets picked up by the TV regardless of the different settings Ive tried (and Ive tried every setting you can think of)

I now starting to suspect my Samsung TV does not provide correct edid information but how can I verify this? 

Here is a printout from the xorg logfile, does it look like the edid from the Samsung LCD TV is valid?

```
fredrik@Burken:~$ less /var/log/Xorg.0.log | grep NVIDIA
[    19.245] (II) Module glx: vendor="NVIDIA Corporation"
[    19.275] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    19.672] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.704] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    19.898] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    20.137] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    20.137] (==) NVIDIA(0): RGB weight 888
[    20.137] (==) NVIDIA(0): Default visual is TrueColor
[    20.137] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.137] (**) NVIDIA(0): Option "TwinView" "0"
[    20.138] (**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0; CRT: 1280x1024_75 +0+0"
[    20.138] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
[    21.339] (II) NVIDIA(GPU-0): Display (LG Electronics L1980Q (CRT-0)) does not support
[    21.339] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[    21.373] (II) NVIDIA(GPU-0): Display (SAMSUNG LCD (DFP-0)) does not support NVIDIA 3D
[    21.373] (II) NVIDIA(GPU-0):     Vision stereo.
[    21.381] (II) NVIDIA(0): NVIDIA GPU ION (GT21:cool: at PCI:2:0:0 (GPU-0)
[    21.381] (--) NVIDIA(0): Memory: 524288 kBytes
[    21.381] (--) NVIDIA(0): VideoBIOS: 70.18.5a.00.11
[    21.381] (II) NVIDIA(0): Detected PCI Express Link width: 1X
[    21.381] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    21.381] (--) NVIDIA(0): Connected display device(s) on ION at PCI:2:0:0
[    21.381] (--) NVIDIA(0):     LG Electronics L1980Q (CRT-0)
[    21.381] (--) NVIDIA(0):     SAMSUNG LCD (DFP-0)
[    21.381] (--) NVIDIA(0): LG Electronics L1980Q (CRT-0): 400.0 MHz maximum pixel clock
[    21.382] (--) NVIDIA(0): SAMSUNG LCD (DFP-0): 165.0 MHz maximum pixel clock
[    21.382] (--) NVIDIA(0): SAMSUNG LCD (DFP-0): Internal Single Link TMDS
[    21.383] (II) NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
[    21.412] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    21.412] (II) NVIDIA(0): Validated modes:
[    21.412] (II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0"
[    21.412] (II) NVIDIA(0):     "CRT:1280x1024_75+0+0"
[    21.413] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[    21.443] (--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
[    21.443] (--) NVIDIA(0):     option
[    21.443] (**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
[    21.443] (==) NVIDIA(1): RGB weight 888
[    21.443] (==) NVIDIA(1): Default visual is TrueColor
[    21.443] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[    21.444] (**) NVIDIA(1): Option "TwinView" "0"
[    21.444] (**) NVIDIA(1): Option "MetaModes" "DFP: nvidia-auto-select +0+0"
[    21.444] (II) NVIDIA(1): NVIDIA GPU ION (GT21:cool: at PCI:2:0:0 (GPU-0)
[    21.444] (--) NVIDIA(1): Memory: 524288 kBytes
[    21.444] (--) NVIDIA(1): VideoBIOS: 70.18.5a.00.11
[    21.444] (II) NVIDIA(1): Detected PCI Express Link width: 1X
[    21.444] (--) NVIDIA(1): Interlaced video modes are supported on this GPU
[    21.444] (--) NVIDIA(1): Connected display device(s) on ION at PCI:2:0:0
[    21.444] (--) NVIDIA(1):     LG Electronics L1980Q (CRT-0)
[    21.444] (--) NVIDIA(1):     SAMSUNG LCD (DFP-0)
[    21.444] (--) NVIDIA(1): LG Electronics L1980Q (CRT-0): 400.0 MHz maximum pixel clock
[    21.444] (--) NVIDIA(1): SAMSUNG LCD (DFP-0): 165.0 MHz maximum pixel clock
[    21.444] (--) NVIDIA(1): SAMSUNG LCD (DFP-0): Internal Single Link TMDS
[    21.446] (II) NVIDIA(1): Display Device found referenced in MetaMode: DFP-0
[    21.587] (II) NVIDIA(1): Assigned Display Device: DFP-0
[    21.587] (II) NVIDIA(1): Validated modes:
[    21.587] (II) NVIDIA(1):     "DFP:nvidia-auto-select+0+0"
[    21.587] (II) NVIDIA(1): Virtual screen size determined to be 1920 x 1080
[    21.603] (--) NVIDIA(1): DPI set to (304, 304); computed from "UseEdidDpi" X config
[    21.603] (--) NVIDIA(1):     option
[    21.603] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    21.612] (II) NVIDIA(0): Setting mode "CRT:nvidia-auto-select+0+0"
[    21.768] (==) NVIDIA(0): Disabling shared memory pixmaps
[    21.768] (==) NVIDIA(0): Backing store disabled
[    21.768] (==) NVIDIA(0): Silken mouse enabled
[    21.769] (**) NVIDIA(0): DPMS enabled
[    21.771] (II) NVIDIA(0): [DRI2] Setup complete
[    21.779] (II) NVIDIA(1): Setting mode "DFP:nvidia-auto-select+0+0"
[    22.069] (==) NVIDIA(1): Disabling shared memory pixmaps
[    22.069] (==) NVIDIA(1): Backing store disabled
[    22.069] (==) NVIDIA(1): Silken mouse enabled
[    22.069] (==) NVIDIA(1): DPMS enabled
[    22.072] (II) NVIDIA(1): [DRI2] Setup complete    
```Thanks!

/Fredrik

---

