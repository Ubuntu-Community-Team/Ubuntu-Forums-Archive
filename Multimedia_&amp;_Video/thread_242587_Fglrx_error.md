---
title: "Fglrx error"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by varean on 2006-08-23
Hey everyone,I reinstalled Ubuntu recently and I followed the ati-drivers howto guide on the wiki to get 3d acceleration working with my Radeon X1600 Pro PCIe card working, but I get this error when I try to start X:
```
  (WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found
  (EE) fglrx(0): ===[R200PreInitDAL]=== DALEnableInstance failed
  (EE) fglrx(0): PreInitDAL failed
  (EE) fglrx(0): R200PreInit failed
  (EE) Screen(s) found, but none have a usable configuration.
```

There is also an error before that says ```
/some/directory/containing/the/fglrx_module/fglrx.ko
Directory does not exist
```

And then it says that it cant load the module.  I tried module-assistant build fglrx again but it still doesnt find the module for some reason. As far as I know, I think it cant find the module, but I dont really know how to fix it.

---

### Post by varean on 2006-08-25
Well, this is good news, the system detects my video card correctly, but I get an error when starting X, aside from the one posted above.  Here is my /var/log/Xorg.0.log:
```
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x00009000 - 0x000090ff (0x100) IX[B]
        [1] -1  0       0x00009400 - 0x000094ff (0x100) IX[B]
        [2] -1  0       0x00009800 - 0x000098ff (0x100) IX[B]
        [3] -1  0       0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 3 I/O range:
        [0] -1  0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [1] -1  0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [2] -1  0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [3] -1  0       0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
        [0] -1  0       0xfd900000 - 0xfd9fffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
        [0] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 4 I/O range:
        [0] -1  0       0x0000c000 - 0x0000c0ff (0x100) IX[B]
        [1] -1  0       0x0000c400 - 0x0000c4ff (0x100) IX[B]
        [2] -1  0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [3] -1  0       0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
        [0] -1  0       0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
        [0] -1  0       0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(3:0:0) ATI Technologies Inc unknown chipset (0x71c2) rev 0, Mem @ 0xd0000000/28, 0xfd9f0000/16, I/O @ 0xbc00/8
(--) PCI: (3:0:1) ATI Technologies Inc unknown chipset (0x71e2) rev 0, Mem @ 0xfd9e0000/16
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
        [0] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
        [1] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
        [2] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
        [3] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
        [4] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
        [5] -1  0       0xfd9f0000 - 0xfd9fffff (0x10000) MX[B](B)
        [6] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [7] -1  0       0x0000c800 - 0x0000c807 (0x8) IX[B]
        [8] -1  0       0x0000cc00 - 0x0000cc1f (0x20) IX[B]
        [9] -1  0       0x0000d400 - 0x0000d407 (0x8) IX[B]
        [10] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [11] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[B]
        [12] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [13] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [14] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [15] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [16] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [17] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[B]
        [18] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[B]
        [19] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [20] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
        [0] -1  0       0xfd9e0000 - 0xfd9effff (0x10000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
        [1] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
        [2] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
        [3] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
        [4] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
        [5] -1  0       0xfd9f0000 - 0xfd9fffff (0x10000) MX[B](B)
        [6] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [7] -1  0       0x0000c800 - 0x0000c807 (0x8) IX[B]
        [8] -1  0       0x0000cc00 - 0x0000cc1f (0x20) IX[B]
        [9] -1  0       0x0000d400 - 0x0000d407 (0x8) IX[B]
        [10] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [11] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[B]
        [12] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [13] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [14] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [15] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [16] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [17] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[B]
        [18] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[B]
        [19] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [20] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
        [0] -1  0       0xfd9e0000 - 0xfd9effff (0x10000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
        [5] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
        [6] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
        [7] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
        [8] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
        [9] -1  0       0xfd9f0000 - 0xfd9fffff (0x10000) MX[B](B)
        [10] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [11] -1 0       0xfd9e0000 - 0xfd9effff (0x10000) MX[B](B)
        [12] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [13] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [14] -1 0       0x0000c800 - 0x0000c807 (0x8) IX[B]
        [15] -1 0       0x0000cc00 - 0x0000cc1f (0x20) IX[B]
        [16] -1 0       0x0000d400 - 0x0000d407 (0x8) IX[B]
        [17] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [18] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[B]
        [19] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [20] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [21] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [22] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [23] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [24] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[B]
        [25] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[B]
        [26] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [27] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.0.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 6.8.99.8, module version = 8.28.8
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) ATI Radeon/FireGL: The following chipsets are supported:
        RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
        MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
        RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
        RADEON 9250/9200 Series (RV280 5961),
        RADEON 9250/9200 Series (RV280 5962),
        RADEON 9250/9200 Series (RV280 5964), FireMV 2200 PCI (RV280 5965),
        MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
        FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
        RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
        RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
        RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
        MOBILITY RADEON 9600/9700 (M10/M11 4E50),
        MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
        RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
        FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
        RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
        FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
        RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
        FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
        RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
        RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
        MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300/X550 (RV370 5B60),
        RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
        FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
        MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
        MOBILITY RADEON X600 SE (M24 5462), MOBILITY FireGL V3100 (M22 5464),
        RADEON X600/X550 Series (RV380 3E50), FireGL V3200 (RV380 3E54),
        MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
        MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
        RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
        RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
        FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
        RADEON X800 SE (R420 4A4F),
        RADEON X800 XT Platinum Edition (R420 4A50),
        RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
        RADEON X800 GTO (R423 5549),
        RADEON X800 XT Platinum Edition (R423 554A),
        RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
        FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
        MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
        MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
        RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
        RADEON X850 XT Platinum Edition (R480 5D4D),
        RADEON X800 GTO (R480 5D4F), FireGL V7200 (R480 5D50),
        RADEON X850 XT (R480 5D52), RADEON X850 (R481 4B48),
        RADEON X850 XT (R481 4B49), RADEON X850 SE (R481 4B4A),
        RADEON X850 PRO (R481 4B4B),
        RADEON X850 XT Platinum Edition (R481 4B4C),
        MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
        FireGL V5000 (RV410 5E48), RADEON X700 XT (RV410 5E4A),
        RADEON X700 PRO (RV410 5E4B), RADEON X700 SE (RV410 5E4C),
        RADEON X700 (RV410 5E4D), RADEON X700/X550 Series (RV410 5E4F),
        MOBILITY RADEON X700 (M26 5652), MOBILITY RADEON X700 (M26 5653),
        MOBILITY RADEON X700 XL (M26-XC 564F),
        RADEON 9000/9100 IGP Series (RS300 5834),
        RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
        MOBILITY RADEON 9000 IGP (RL300MB 7835),
        MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
        RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
        RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
        RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
        RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
        RADEON X1800 (R520 7100), MOBILITY RADEON X1800 XT (M58 7101),
        MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
        FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
        MOBILITY FireGL V7100 (M58 7106), RADEON X1800 Series (R520 7108),
        RADEON X1800 Series (R520 7109), RADEON X1800 Series (R520 710A),
        RADEON X1800 Series (R520 710B), RADEON X1800 Series (R520 710C),
        FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
        MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
        RADEON X1600 Series (RV515 7140), RADEON X1300 Series (RV515 7142),
        MOBILITY FireGL (M54 GL 7144), MOBILITY RADEON X1400 (M54 7145),
        RADEON X1300 Series (RV515 7146), MOBILITY RADEON X1300 (M52 7149),
        MOBILITY RADEON X1300 (M52 714A), RADEON X1300 Series (RV515 714D),
        RADEON X1300 Series (RV515 714E), FireGL V3300 (RV515 7152),
        RADEON X1300 Series (RV515 715E), RADEON X1300 (RV516 7180),
        RADEON X1600 Series (RV516 7181), RADEON X1300 (RV516 7183),
        MOBILITY RADEON X1450 (M64P 7186), RADEON X1300 (RV516 7187),
        MOBILITY RADEON X1350 (M62P 718B),
        MOBILITY RADEON X1350 (M62CSP 718C),
        MOBILITY RADEON X1450 (M64CSP 718D),
        MOBILITY RADEON X1350 (M62S 7196), RADEON X1900 (R580 7240),
        RADEON X1900 (R580 7243), RADEON X1900 (R580 7244),
        RADEON X1900 (R580 7245), RADEON X1900 (R580 7246),
        RADEON X1900 (R580 7247), RADEON X1900 (R580 7248),
        RADEON X1900 (R580 7249), RADEON X1900 (R580 724A),
        RADEON X1900 (R580 724B), RADEON X1900 (R580 724C),
        RADEON X1900 (R580 724D), FireStream 2U (R580 724E),
        FireStream 2U (R580 724F), RADEON X1600 Series (RV530 71C0),
        RADEON X1600 Series (RV530 71C2), MOBILITY FireGL V5200 (M56 71C4),
        MOBILITY RADEON X1600 (M56 71C5),
        RADEON X1600 Series (RV530 LE 71C6),
        RADEON X1600 Series (RV530 VE 71CE), FireGL V3400 (RV530 71D2),
        MOBILITY RADEON X1700 (M66-XT 71D6), FireGL V5200 (RV530 71DA),
        RADEON X1600 Series (RV530 SE 71DE), RADEON X1600 XT (RV535 XT 71C1),
        MOBILITY FireGL V5250 (M66GL 71D4),
        MOBILITY RADEON X1700 (M66-P 71D5), RADEON Xpress 1200 (RS600 7941),
        RADEON Xpress 1200 (RS600 7942)
(II) Primary Device is: PCI 03:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.28.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.28g1 
(II) ATI Proprietary Linux Driver Build Date: Aug 17 2006 09:26:25
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.28.1.1.2.3-driver-lnx-x86-x86_64-287161
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found
(--) Chipset RADEON X1600 Series (RV530 71C2) found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
        [5] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
        [6] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
        [7] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
        [8] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
        [9] -1  0       0xfd9f0000 - 0xfd9fffff (0x10000) MX[B](B)
        [10] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [11] -1 0       0xfd9e0000 - 0xfd9effff (0x10000) MX[B](B)
        [12] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [13] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [14] -1 0       0x0000c800 - 0x0000c807 (0x8) IX[B]
        [15] -1 0       0x0000cc00 - 0x0000cc1f (0x20) IX[B]
        [16] -1 0       0x0000d400 - 0x0000d407 (0x8) IX[B]
        [17] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [18] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[B]
        [19] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [20] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [21] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [22] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [23] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [24] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[B]
        [25] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[B]
        [26] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [27] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81db970
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
        [5] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
        [6] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
        [7] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
        [8] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
        [9] -1  0       0xfd9f0000 - 0xfd9fffff (0x10000) MX[B](B)
        [10] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [11] -1 0       0xfd9e0000 - 0xfd9effff (0x10000) MX[B](B)
        [12] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [13] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [14] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [15] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [16] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [17] -1 0       0x0000c800 - 0x0000c807 (0x8) IX[B]
        [18] -1 0       0x0000cc00 - 0x0000cc1f (0x20) IX[B]
        [19] -1 0       0x0000d400 - 0x0000d407 (0x8) IX[B]
        [20] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [21] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[B]
        [22] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[B]
        [23] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [24] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [25] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [26] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [27] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[B]
        [28] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[B]
        [29] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [30] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
        [31] 0  0       0xfd9003b0 - 0xfd9003bb (0xc) IS[B]
        [32] 0  0       0xfd9003c0 - 0xfd9003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): PCI bus 3 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON X1600 Series (RV530 71C2)" (Chipset = 0x71c2)
(--) fglrx(0): (PciSubVendor = 0x17ee, PciSubDevice = 0x71c0)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfd9f0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: RV530
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 6.8.99.8, module version = 8.28.8
        ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR1
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(EE) fglrx(0): === [R200PreInitDAL] === DALEnableInstance failed
(EE) fglrx(0): PreInitDAL failed
(EE) fglrx(0): R200PreInit failed
(II) fglrx(0): === [R200PreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "fglrxdrm"
(II) Unloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) UnloadModule: "drm"
(II) UnloadModule: "vbe"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

---

### Post by varean on 2006-08-25
Well, I ran over the installation again and I took a look at the error again.  For some reason(which is my issue), the system can't find the fglrx module, the directory its in, doesn't exist.  It detects my card, its series, and loads the proper modules, except for the fglrx module.  It tries to enable the fglrx instance but fails, thats why i get the "R200 PreINIT enable failed" error.  I am booting into the latest kernel version, but it still cant find the module, any ideas?

---

