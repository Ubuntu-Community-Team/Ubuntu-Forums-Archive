---
title: "How Do I Install My Video Card Drivers?"
date: 2011-09-01
forum: Multimedia Software
---

### Post by KingRazor on 2011-09-01
I'm running ubuntu 11.04 64-bit.

I have an NVIDIA GeForce GTS 250 video card.

I went under "additional drivers" and actived the NVIDIA accelerated graphics driver, but it says it's "not currently in use".

I also tried downloading the driver from NVIDIA's website, but instead of installing, it opens in a text document and I get the message: "Could not open the file home/razor/Downloads/NV...A-Linux-x86_64-280.13.run.

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again."

Please help.

---

### Post by papibe on 2011-09-01
> **dabbi2000 said:**
> "but not currently in use"
That seems to be a bug.

In order to make sure you are running the Nvidia driver:

Backup your X config file first:
```
# sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then run the Nvidia X Server Setings:
```
$ gksudo nvidia-settings
```
Select X Server Display Configuration (left). In the right press 'Save to X Configuration File'. Restart your machine.

Tell us how it goes,
Regards.

---

### Post by KingRazor on 2011-09-01
Upon trying to do that, I received this error:

Failed to parse existing X config file '/etc/X11/xorg.conf'!

---

### Post by papibe on 2011-09-01
Interesting. It be may corrupted. Delete it (actually rename it), so you can take out of the equation:
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.error
```
Hope it helps,
Regards.

---

### Post by KingRazor on 2011-09-01
Alright, I've followed the instructions in your first post, but nothing has changed.

---

### Post by papibe on 2011-09-01
Well, if you are referring to the message on Additional Drivers, that will remain until the bug is fixed (the bug is related to displaying correctly what is being used).

To make 100% sure you are using the nvidia driver, post the result of this command:
```
$ grep -i nvidia /var/log/Xorg.0.log
```
It should look something similar like this:
```
[    15.054] (II) Module glx: vendor="NVIDIA Corporation"
[    15.054] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    15.055] (II) LoadModule: "nvidia"
[    15.055] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    15.055] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.055] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011
[    15.055] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    15.071] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    15.071] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    15.071] (==) NVIDIA(0): RGB weight 888
[    15.071] (==) NVIDIA(0): Default visual is TrueColor
[    15.071] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.071] (**) NVIDIA(0): Option "NoLogo" "True"
[    15.071] (**) NVIDIA(0): Option "TwinView" "0"
[    15.071] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[    16.184] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    16.184] (II) NVIDIA(GPU-0):     Vision stereo.
[    16.186] (II) NVIDIA(0): NVIDIA GPU GeForce 310M (GT218) at PCI:1:0:0 (GPU-0)
[    16.186] (--) NVIDIA(0): Memory: 524288 kBytes
[    16.186] (--) NVIDIA(0): VideoBIOS: 70.18.5f.00.12
[    16.186] (II) NVIDIA(0): Detected PCI Express Link width: 8X
[    16.186] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    16.186] (--) NVIDIA(0): Connected display device(s) on GeForce 310M at PCI:1:0:0
[    16.186] (--) NVIDIA(0):     Seiko/Epson (DFP-0)
[    16.186] (--) NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[    16.186] (--) NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[    16.234] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    16.234] (II) NVIDIA(0): Validated modes:
[    16.234] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    16.234] (II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
[    17.304] (--) NVIDIA(0): DPI set to (99, 97); computed from "UseEdidDpi" X config
[    17.304] (--) NVIDIA(0):     option
[    17.304] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    17.344] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[    17.663] (==) NVIDIA(0): Disabling shared memory pixmaps
[    17.663] (==) NVIDIA(0): Backing store disabled
[    17.663] (==) NVIDIA(0): Silken mouse enabled
[    17.663] (**) NVIDIA(0): DPMS enabled
[    17.664] (II) NVIDIA(0): [DRI2] Setup complete
pablo@vanhalen:~$ grep -i nvidia /var/log/Xorg.0.log | more
[    15.054] (II) Module glx: vendor="NVIDIA Corporation"
[    15.054] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    15.055] (II) LoadModule: "nvidia"
[    15.055] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    15.055] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.055] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2
011
[    15.055] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    15.071] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    15.071] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    15.071] (==) NVIDIA(0): RGB weight 888
[    15.071] (==) NVIDIA(0): Default visual is TrueColor
[    15.071] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.071] (**) NVIDIA(0): Option "NoLogo" "True"
[    15.071] (**) NVIDIA(0): Option "TwinView" "0"
[    15.071] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[    16.184] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support 
NVIDIA 3D
[    16.184] (II) NVIDIA(GPU-0):     Vision stereo.
[    16.186] (II) NVIDIA(0): NVIDIA GPU GeForce 310M (GT218) at PCI:1:0:0 (GPU-0
)
[    16.186] (--) NVIDIA(0): Memory: 524288 kBytes
[    16.186] (--) NVIDIA(0): VideoBIOS: 70.18.5f.00.12
[    16.186] (II) NVIDIA(0): Detected PCI Express Link width: 8X
[    16.186] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    16.186] (--) NVIDIA(0): Connected display device(s) on GeForce 310M at PCI:
1:0:0
[    16.186] (--) NVIDIA(0):     Seiko/Epson (DFP-0)
[    16.186] (--) NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[    16.186] (--) NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[    16.234] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    16.234] (II) NVIDIA(0): Validated modes:
[    16.234] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    16.234] (II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
[    17.304] (--) NVIDIA(0): DPI set to (99, 97); computed from "UseEdidDpi" X c
onfig
[    17.304] (--) NVIDIA(0):     option
[    17.304] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory 
access.
[    17.344] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[    17.663] (==) NVIDIA(0): Disabling shared memory pixmaps
[    17.663] (==) NVIDIA(0): Backing store disabled
[    17.663] (==) NVIDIA(0): Silken mouse enabled
[    17.663] (**) NVIDIA(0): DPMS enabled
[    17.664] (II) NVIDIA(0): [DRI2] Setup complete
```
Regards.

---

### Post by KingRazor on 2011-09-01
I typed that in, but nothing happened. It just went to the next line.

---

### Post by papibe on 2011-09-01
My mistake, this is the good one (also fixed above).
```
$ grep -i nvidia /var/log/Xorg.0.log
```

---

### Post by KingRazor on 2011-09-01
Alright, here are the results:

```
[    11.188] (II) Module glx: vendor="NVIDIA Corporation"
[    11.188] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[    11.189] (II) LoadModule: "nvidia"
[    11.189] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    11.189] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.189] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[    11.189] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    11.199] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    11.199] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    11.199] (==) NVIDIA(0): RGB weight 888
[    11.199] (==) NVIDIA(0): Default visual is TrueColor
[    11.199] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    11.199] (**) NVIDIA(0): Option "TwinView" "0"
[    11.199] (**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0"
[    12.040] (II) NVIDIA(GPU-0): Display (IBM L171 (CRT-1)) does not support NVIDIA 3D Vision
[    12.040] (II) NVIDIA(GPU-0):     stereo.
[    12.090] (II) NVIDIA(GPU-0): Display (IBM L170p (DFP-0)) does not support NVIDIA 3D Vision
[    12.090] (II) NVIDIA(GPU-0):     stereo.
[    12.092] (II) NVIDIA(0): NVIDIA GPU GeForce GTS 250 (G92) at PCI:1:0:0 (GPU-0)
[    12.092] (--) NVIDIA(0): Memory: 524288 kBytes
[    12.092] (--) NVIDIA(0): VideoBIOS: 62.92.7e.00.00
[    12.092] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    12.092] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    12.092] (--) NVIDIA(0): Connected display device(s) on GeForce GTS 250 at PCI:1:0:0
[    12.092] (--) NVIDIA(0):     IBM L171 (CRT-1)
[    12.092] (--) NVIDIA(0):     IBM L170p (DFP-0)
[    12.092] (--) NVIDIA(0): IBM L171 (CRT-1): 400.0 MHz maximum pixel clock
[    12.092] (--) NVIDIA(0): IBM L170p (DFP-0): 330.0 MHz maximum pixel clock
[    12.092] (--) NVIDIA(0): IBM L170p (DFP-0): Internal Dual Link TMDS
[    12.097] (II) NVIDIA(0): Display Device found referenced in MetaMode: CRT-1
[    12.104] (II) NVIDIA(0): Assigned Display Device: CRT-1
[    12.104] (II) NVIDIA(0): Validated modes:
[    12.105] (II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0"
[    12.105] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[    12.127] (--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
[    12.127] (--) NVIDIA(0):     option
[    12.127] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    12.136] (II) NVIDIA(0): Setting mode "CRT:nvidia-auto-select+0+0"
[    12.223] (==) NVIDIA(0): Disabling shared memory pixmaps
[    12.223] (==) NVIDIA(0): Backing store disabled
[    12.223] (==) NVIDIA(0): Silken mouse enabled
[    12.224] (**) NVIDIA(0): DPMS enabled
[    12.224] (II) NVIDIA(0): [DRI2] Setup complete

```

---

### Post by papibe on 2011-09-01
:D You are using the Nvidia driver!

---

### Post by KingRazor on 2011-09-01
Yep, I finally got my second monitor working.

I no longer hate ubuntu!

---

