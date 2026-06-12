---
title: "Matrox P650 on Ubuntu 10.04 Lucid - Regression"
date: 2010-05-28
forum: Multimedia Software
---

### Post by scribe63 on 2010-05-28
I scrapped my 9.04 Ubuntu Studio install, for which i had to use a AV Linux RealTime Kernel, and installed UbuntuStudio 10.04.

Besides my basic issue with the new grub2, i am currently having a serious issues with the Matrox P650 (AGP) display card.

After the initial installation, for some reason, Nautilus, Synaptic and the GNOME desktop would become unresponsive, but the mouse and keyboard would continue to work.

To solve this, I decided and installed the driver for the display card from the matrox website, of which the latest is version 1.4.7.
The installed kernel is 2.6.31-10-rt #153-Ubuntu SMP PREEMPT RT 

The driver compiled without any error, but upon reboot, xserver-xorg (1.7.6)is unable to load the mtx_drv.so, glx, and v4l modules.
These are the errors it displays.
(II) LoadModule: "mtx"
(II) Loading /usr/lib/xorg/modules/drivers/mtx_drv.so
dlopen: /usr/lib/xorg/modules/drivers/mtx_drv.so: undefined symbol: resVgaShared
(EE) Failed to load /usr/lib/xorg/modules/drivers/mtx_drv.so

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
dlopen: /usr/lib/xorg/modules/extensions/libglx.so: undefined symbol: miInitVisualsProc
(EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so

v4l: failed to load module, (module requirement mismatch, 0)

I am uncertain as to whether this is a Matrox, Xorg, or Ubuntu/Ubuntu Studio 10.04 issue, and the only solution seems to be a downgrade of xorg and the kernel.

Any help or insight in how to solve this issue, so as to get back my dual monitor set up, will be kindly appreciated.

TIA

---

