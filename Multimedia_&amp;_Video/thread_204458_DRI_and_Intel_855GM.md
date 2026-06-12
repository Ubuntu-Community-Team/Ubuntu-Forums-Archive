---
title: "DRI and Intel 855GM"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by Zeroedout on 2006-06-27
Hello, I recently threw Dapper on a Dell Latitude D400 which has an intel 855GM card. After I installed dapper, i ran glxinfo and direct rendering was working, so I thought, kick ***, i'm gonna throw on XGL and compiz (to impress the ladies!). Unfortunatly, after adding Quinstrom's repos and doing a dist-upgrade, dri didn't work. So I googled it and on one of the gentoo wiki's it said kernel 2.6.17 was needed, and I compiled and installed (built intelfb module into the kernel). Now DRI does not work. The following is the relevent info:

**glxinfo**```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample........

client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address,.............

GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_ad...............


OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture...................

```

**dmesg |grep intel ```
**
[17179571.320000] intelfb: intelfb_init
[17179571.320000] intelfb: Framebuffer driver for Intel(R) 830M/845G/852GM/855GM/865G/915G/915GM chipsets
[17179571.320000] intelfb: Version 0.9.2
[17179571.320000] intelfb: intelfb_setup
[17179571.320000] intelfb: no options
[17179571.320000] intelfb: intelfb_pci_register
[17179571.320000] intelfb: fb aperture: 0xf0000000/0x8000000, MMIO region: 0xfaf80000/0x80000
[17179571.320000] intelfb: 00:02.0: Intel(R) 855GM, aperture size 128MB, stolen memory 892kB
[17179571.324000] intelfb: fb: 0xf3011000(+ 0x3011)/0x400000 (0xfbe11000)
[17179571.324000] intelfb: MMIO: 0xfaf80000/0x80000 (0xff280000)
[17179571.324000] intelfb: ring buffer: 0xf3001000/0x10000 (0xfbe01000)
[17179571.324000] intelfb: HW cursor: 0x0/0x0 (0x0) (offset 0x0) (phys 0x0)
[17179571.324000] intelfb: options: vram = 4, accel = 1, hwcursor = 0, fixed = 0, noinit = 0
[17179571.324000] intelfb: options: mode = ""
[17179571.324000] intelfb: Non-CRT device is enabled ( LVDS port ).  Disabling mode switching.
[17179571.324000] intelfb: Video mode must be programmed at boot time.
[17179571.324000] intelfb: cleanup
[17179587.788000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179588.872000] intel8x0_measure_ac97_clock: measured 55453 usecs
[17179588.872000] intel8x0: clocking to 48000


```
Attached is Xorg.0.log

---

