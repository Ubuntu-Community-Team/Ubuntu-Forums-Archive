---
title: "Nvidia video card stopped working with Nvidia driver"
date: 2010-06-24
forum: Multimedia Software
---

### Post by sujitvp on 2010-06-24
Hello,

I had created this thread in the General section, before realizing it was better suited here. The link to the original post is [Nvidia video card stopped working with Nvidia driver]("http://ubuntuforums.org/showthread.php?p=9503055").

I have a dual-boot desktop installed with Lucid Lynx on one partition. I am using nVidia 9600 GT video card (PCI-E) and had the Lucid Lynx working with it and configured for TwinView.

Then I bought and installed a Hauppage PVR 1600 card (PCI). Ever since after installing this card, my nVidia card has stopped working with the nVidia driver. Although, I am still able to get display out in the "low graphics mode" from the video card.

To ensure that I had not accidentally misaligned or mis-installed the card, I booted into the Windows partition and was able to configure both the Hauppage and the nVidia cards using their own drivers.

I googled the errors reported in kern.log and Xorg.0.log, found several references to it but no solutions.

I have tried uninstalling and then re-installing the nVidia driver. 

Next I am going to try re-installing linux (I had a similar problem once before, and upgrading from Intrepid to Lucid to resolve it). 

However, before I try re-installing linux, I would like to know if there is a more elegant solution that addresses the core issue. Even if the solution is to re-install, I would like to understand the core issue itself.


_Additional data on the issue:_

**From the kern.log**
```

Jun 11 21:25:22 Home kernel: [   27.005174] nvidia: module license 'NVIDIA' taints kernel.
.
.
Jun 11 21:25:23 Home kernel: [   27.997642] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 11 21:25:23 Home kernel: [   27.997653] nvidia 0000:01:00.0: setting latency timer to 64
.
.
Jun 11 21:25:23 Home kernel: [   27.998381] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 11 21:41:46 PST 2010
.
.
Jun 11 21:25:24 Home kernel: [   29.650899] NVRM: failed to map registers!!
Jun 11 21:25:24 Home kernel: [   29.650903] NVRM: RmInitAdapter failed! (0x10:0x32:1359)
Jun 11 21:25:24 Home kernel: [   29.650908] NVRM: rm_init_adapter(0) failed
.

```

**From the Xorg.log**
```

.
.
(--) PCI: (0:0:2:0) 8086:2772:1019:2624 Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xf3f80000/524288, 0xc0000000/268435456, 0xf3f40000/262144, I/O @ 0x0000cc00/8
(--) PCI:*(0:1:0:0) 10de:0622:1462:1270 nVidia Corporation G94 [GeForce 9600 GT] rev 161, Mem @ 0xf7000000/16777216, 0xd0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
(--) PCI: (0:2:2:0) 14f1:5b7a:0070:7444 Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder rev 0, Mem @ 0xf8000000/67108864
.
.
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.15  Thu Mar 11 22:01:49 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Jun 11 22:56:51 NVIDIA(0): Enabling RENDER acceleration
(II) Jun 11 22:56:51 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jun 11 22:56:51 NVIDIA(0):     enabled.
(EE) Jun 11 22:56:51 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) Jun 11 22:56:51 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) Jun 11 22:56:51 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) Jun 11 22:56:51 NVIDIA(0):     README for additional information.
(EE) Jun 11 22:56:51 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
.

```

---

