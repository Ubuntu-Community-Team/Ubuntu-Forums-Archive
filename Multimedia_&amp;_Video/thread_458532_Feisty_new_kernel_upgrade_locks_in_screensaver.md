---
title: "Feisty: new kernel upgrade locks in screensaver"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by madscientist on 2007-05-29
Hi all; ever since the latest kernel/restricted drivers upgrade yesterday I've had my system lock up whenever using GL screensavers such as Lattice, etc.  Before that, I had no problems.  Now it will lock up almost immediately after starting the screensaver.  Sometimes it will even start to lock up when looking at the little screensaver chooser window.

What happens is that the CPU goes to 100%, all being used by the X server.  No amount of mouse movement or key pressing will turn off the screensaver.  The first time it had been frozen for a few hours at least, and the screen was blank (but the monitor was not in sleep mode, which it usually would be after that amount of time).  I can't use C-A-F1 to get a console.  I tried logging in remotely and SSH never responded.  I had to hard-reset (power cycle).

The next time it happened I found it shortly after it locked up.  The screensaver image was on the screen still, but it was completely frozen.  Again, no C-A-F1, etc.  This time I WAS able to log in remotely, and I saw that the X server was using 100% (basically) of the CPU.  I couldn't kill it with "kill PID".  I used "kill -9 PID" and that worked BUT the entire system froze hard again, just as before: the screen was blank, my existing SSH connection was non-responsive, no new connection could be made, C-A-F1 didn't work.  Again I had to power-cycle the system.

Help!  Of course I've turned off fancy screensavers, but my kids are always turning them back on again (they love those things).

Here are some packages/versions from my system:

```
ii  linux-headers-2.6.20-16           2.6.20-16.28
ii  linux-headers-2.6.20-16-generic   2.6.20-16.28
ii  linux-headers-generic             2.6.20.16.28.1
ii  linux-image-2.6.20-16-generic     2.6.20-16.28
ii  linux-image-generic               2.6.20.16.28.1
ii  linux-restricted-modules-generic  2.6.20.16.28.1
ii  nvidia-kernel-common              20051028+1ubuntu7
ii  nvidia-glx                        1.0.9631+2.6.20.5-16.28
ii  xserver-xorg-video-nv             2.0.0-0ubuntu3
```

My Xorg.0.log says:

```
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5500]"
    ...
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5500] rev 161, Mem @ 0xde000000/24, 0xc0000000/28, BIOS @ 0xdfee0000/17
    ...
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9631
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9631
        Module class: X.Org Video Driver
    ...
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
    ...
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
(--) NVIDIA(0):     ViewSonic (CRT-0)
(--) NVIDIA(0): ViewSonic (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0):     "640x400"
(II) NVIDIA(0):     "640x350"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (101, 108); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
    ...
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL

```

---

### Post by n8bounds on 2007-05-29
there's a bug with 2.6.20-16, almost everyone is having problems, try the next most recent kernel in your grub list..

---

