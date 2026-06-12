---
title: "Graphic &quot;noise&quot; using NVIDIA drivers when upgrading kernel"
date: 2011-03-18
forum: Multimedia Software
---

### Post by jfosterjr on 2011-03-18
I upgraded my Linux kernel to version 2.6.35-22-generic and subsequently experienced odd graphics issues such a random "noise" (pixels white) on an background (such as my wallpaper).  I do not see this issue with the graphics driver that is standard with the Ubuntu installation.  It only occurs with the use of the proprietary NVIDIA drivers.  I have since updated my Linux kernel to 2.6.35-27-generic and finally to 2.6.35-28-generic.  After each kernel upgrade I attempt to reinstall the NVIDIA drivers but the problem persists.  

Any suggestions would be greatly appreciated.  

Here is some information describing my system and the relevant components.

Machine
-----
```
Alienware m15x
```Ubuntu
-----
```
10.10 - Maverick Meerkat
```Linux Kernel
-----
```
2.6.35-28-generic
```Video Card
-----
```
NVIDIA GeForce 8700M GT
CUDA Cores: 32
VBIOS Version: 60.84.68.00.21
Memory: 512 MB
Memory Interface: 128 bit

NVIDIA Driver Version: 260.19.06 (and 173.14.2
```8)

X Screen
-----
```
Dimensions: 19200x1200 pixels
Resolution: 147x145 dpi
Depth: 24
```X Server
-----
```
Version Number: 11.0
Server Vendor String: The X.Org Foundation
Server Vendor Version: 1.9.0 
NV-CONTROL Version: 1.24
```/etc/X11/xorg.conf
-----
```
Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

---

### Post by lidex on 2011-03-19
Is this a manual install or nvidia-current from repos?

---

### Post by jfosterjr on 2011-03-19
This is nvidia-current from the repository.  Everything I installed has been through the repos.  Up until the 2.6.35-22-generic kernel upgrade the proprietary nvidia drivers worked fine.  Once the kernel was upgraded the display started the "noise" problem I mentioned in the first post.  Another problem that occurs now with the video is movie playback frequently pauses, then resumes after a few seconds.

---

### Post by lidex on 2011-03-19
Anything in xorg log?
```
cat /var/log/Xorg.0.log
```

---

### Post by jfosterjr on 2011-03-19
Here is a snippet of that log file you requested that mentions NVIDIA.  I have also included the entire log file as an attachment to this post.  Thank you for your time on this matter.

[    17.171] (II) LoadModule: "nvidia"
[    17.171] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    17.327] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.335]     compiled for 4.0.2, module version = 1.0.0
[    17.335]     Module class: X.Org Video Driver
[    17.427] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[    17.428] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    17.428] (++) using VT number 7

[    17.430] (II) Loading sub module "fb"
[    17.430] (II) LoadModule: "fb"
[    17.431] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.431] (II) Module fb: vendor="X.Org Foundation"
[    17.431]     compiled for 1.9.0, module version = 1.0.0
[    17.431]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.431] (II) Loading sub module "wfb"
[    17.431] (II) LoadModule: "wfb"
[    17.431] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.431] (II) Module wfb: vendor="X.Org Foundation"
[    17.431]     compiled for 1.9.0, module version = 1.0.0
[    17.431]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.431] (II) Loading sub module "ramdac"
[    17.431] (II) LoadModule: "ramdac"
[    17.431] (II) Module "ramdac" already built-in
[    17.455] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    17.455] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    17.455] (==) NVIDIA(0): RGB weight 888
[    17.455] (==) NVIDIA(0): Default visual is TrueColor
[    17.455] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.455] (**) NVIDIA(0): Option "NoLogo" "True"
[    17.456] (**) NVIDIA(0): Enabling RENDER acceleration
[    17.456] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    17.456] (II) NVIDIA(0):     enabled.
[    18.706] (II) NVIDIA(0): NVIDIA GPU GeForce 8700M GT (G84) at PCI:1:0:0 (GPU-0)
[    18.706] (--) NVIDIA(0): Memory: 524288 kBytes
[    18.706] (--) NVIDIA(0): VideoBIOS: 60.84.68.00.21
[    18.706] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    18.706] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    18.707] (--) NVIDIA(0): Connected display device(s) on GeForce 8700M GT at PCI:1:0:0
[    18.707] (--) NVIDIA(0):     LPL (DFP-0)
[    18.707] (--) NVIDIA(0): LPL (DFP-0): 330.0 MHz maximum pixel clock
[    18.707] (--) NVIDIA(0): LPL (DFP-0): Internal Dual Link LVDS
[    18.778] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    18.778] (==) NVIDIA(0): 
[    18.778] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    18.778] (==) NVIDIA(0):     will be used as the requested mode.
[    18.778] (==) NVIDIA(0): 
[    18.778] (II) NVIDIA(0): Validated modes:
[    18.778] (II) NVIDIA(0):     "nvidia-auto-select"
[    18.778] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    19.796] (--) NVIDIA(0): DPI set to (147, 145); computed from "UseEdidDpi" X config
[    19.796] (--) NVIDIA(0):     option
[    19.860] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    19.860] (--) Depth 24 pixmap format is 32 bpp
[    19.861] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    19.863] (II) NVIDIA(0): Initialized GPU GART.
[    19.872] (II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
[    19.873] (II) NVIDIA(0):     enough to receive ACPI hotkey events.
[    19.873] (WW) NVIDIA(0): ACPI: Error: Unable to find the brightness file path under
[    19.873] (WW) NVIDIA(0):     /proc/acpi/video. The NVIDIA X driver will not be able to
[    19.873] (WW) NVIDIA(0):     respond to ACPI brightness change hotkey events.
[    19.880] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    20.156] (II) Loading extension NV-GLX
[    20.258] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    20.300] (==) NVIDIA(0): Disabling shared memory pixmaps
[    20.300] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    20.300] (==) NVIDIA(0): Backing store disabled
[    20.300] (==) NVIDIA(0): Silken mouse enabled
[    20.302] (==) NVIDIA(0): DPMS enabled
[    20.302] (II) Loading extension NV-CONTROL
[    20.302] (II) Loading extension XINERAMA
[    20.302] (II) Loading sub module "dri2"
[    20.302] (II) LoadModule: "dri2"
[    20.302] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.302] (II) NVIDIA(0): [DRI2] Setup complete

---

### Post by jfosterjr on 2011-03-19
After some additional searching for things like "pixels", "snow", "noise", etc to describe the graphics issue I noticed a trend in some of the responses.  This trend led me to suspect that it was not a driver issue rather the graphics card itself might simply be going bad.  Having a dual boot machine (Ubuntu/Windows) I rebooted into Windows (which I have not touched for awhile now) and sure enough the pixel problem manifested itself under Windows as well.  So, graphics card is just going bad.  A bummer but at least this gives me an excuse to upgrade from the 8700M GT that I have now.

---

