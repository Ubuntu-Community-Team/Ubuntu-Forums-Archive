---
title: "New Card, new problems."
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by varean on 2006-08-28
Hi everyone, I am running Ubuntu 6.06 with my Radeon X1600 Pro PCI Express card and I get this error after installing the drivers:
```

   /some/directory/containing/the/fglrx_module/fglrx.ko
   Directory does not exist 
  (WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found
  (EE) fglrx(0): ===[R200PreInitDAL]=== DALEnableInstance failed
  (EE) fglrx(0): PreInitDAL failed
  (EE) fglrx(0): R200PreInit failed
  (EE) Screen(s) found, but none have a usable configuration
```

Xorg.0.log:
```
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x00009000 - 0x000090ff (0x100) IX[b]
        [1] -1  0       0x00009400 - 0x000094ff (0x100) IX[b]
        [2] -1  0       0x00009800 - 0x000098ff (0x100) IX[b]
        [3] -1  0       0x00009c00 - 0x00009cff (0x100) IX[b]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xfdd00000 - 0xfddfffff (0x100000) MX[b]
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0xfdc00000 - 0xfdcfffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 3 I/O range:
        [0] -1  0       0x0000b000 - 0x0000b0ff (0x100) IX[b]
        [1] -1  0       0x0000b400 - 0x0000b4ff (0x100) IX[b]
        [2] -1  0       0x0000b800 - 0x0000b8ff (0x100) IX[b]
        [3] -1  0       0x0000bc00 - 0x0000bcff (0x100) IX[b]
(II) Bus 3 non-prefetchable memory range:
        [0] -1  0       0xfd900000 - 0xfd9fffff (0x100000) MX[b]
(II) Bus 3 prefetchable memory range:
        [0] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 4 I/O range:
        [0] -1  0       0x0000c000 - 0x0000c0ff (0x100) IX[b]
        [1] -1  0       0x0000c400 - 0x0000c4ff (0x100) IX[b]
        [2] -1  0       0x0000c800 - 0x0000c8ff (0x100) IX[b]
        [3] -1  0       0x0000cc00 - 0x0000ccff (0x100) IX[b]
(II) Bus 4 non-prefetchable memory range:
        [0] -1  0       0xfdb00000 - 0xfdbfffff (0x100000) MX[b]
(II) Bus 4 prefetchable memory range:
        [0] -1  0       0xfda00000 - 0xfdafffff (0x100000) MX[b]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[b]
(--) PCI:*(3:0:0) ATI Technologies Inc unknown chipset (0x71c2) rev 0, Mem @ 0xd0000000/28, 0xfd9f0000/16, I/O @ 0xbc00/8
(--) PCI: (3:0:1) ATI Technologies Inc unknown chipset (0x71e2) rev 0, Mem @ 0xfd9e0000/16
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[b]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[b]
(II) Active PCI resource ranges:
        [0] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
        [1] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[b]
        [2] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
        [3] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[b]
        [4] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
        [5] -1  0       0xfd9f0000 - 0xfd9fffff (0x10000) MX[b](B)
        [6] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [7] -1  0       0x0000c800 - 0x0000c807 (0x8) IX[b]
        [8] -1  0       0x0000cc00 - 0x0000cc1f (0x20) IX[b]
        [9] -1  0       0x0000d400 - 0x0000d407 (0x8) IX[b]
        [10] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[b]
        [11] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[b]
        [12] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[b]
        [13] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[b]
        [14] -1 0       0x00000970 - 0x00000977 (0x8) IX[b]
        [15] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[b]
        [16] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[b]
        [17] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[b]
        [18] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[b]
        [19] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[b]
        [20] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[b](B)
(II) Inactive PCI resource ranges:
        [0] -1  0       0xfd9e0000 - 0xfd9effff (0x10000) MX[b](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
        [1] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[b]
        [2] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
        [3] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[b]
        [4] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
        [5] -1  0       0xfd9f0000 - 0xfd9fffff (0x10000) MX[b](B)
        [6] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [7] -1  0       0x0000c800 - 0x0000c807 (0x8) IX[b]
        [8] -1  0       0x0000cc00 - 0x0000cc1f (0x20) IX[b]
        [9] -1  0       0x0000d400 - 0x0000d407 (0x8) IX[b]
        [10] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[b]
        [11] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[b]
        [12] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[b]
        [13] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[b]
        [14] -1 0       0x00000970 - 0x00000977 (0x8) IX[b]
        [15] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[b]
        [16] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[b]
        [17] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[b]
        [18] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[b]
        [19] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[b]
        [20] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[b](B)
(II) Inactive PCI resource ranges after removing overlaps:
        [0] -1  0       0xfd9e0000 - 0xfd9effff (0x10000) MX[b](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
        [5] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[b]
        [6] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
        [7] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[b]
        [8] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
        [9] -1  0       0xfd9f0000 - 0xfd9fffff (0x10000) MX[b](B)
        [10] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [11] -1 0       0xfd9e0000 - 0xfd9effff (0x10000) MX[b](B)
        [12] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [13] -1 0       0x00000000 - 0x000000ff (0x100) IX[b]
        [14] -1 0       0x0000c800 - 0x0000c807 (0x8) IX[b]
        [15] -1 0       0x0000cc00 - 0x0000cc1f (0x20) IX[b]
        [16] -1 0       0x0000d400 - 0x0000d407 (0x8) IX[b]
        [17] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[b]
        [18] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[b]
        [19] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[b]
        [20] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[b]
        [21] -1 0       0x00000970 - 0x00000977 (0x8) IX[b]
        [22] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[b]
        [23] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[b]
        [24] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[b]
        [25] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[b]
        [26] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[b]
        [27] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[b](B)
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
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
        [5] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[b]
        [6] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
        [7] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[b]
        [8] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
        [9] -1  0       0xfd9f0000 - 0xfd9fffff (0x10000) MX[b](B)
        [10] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [11] -1 0       0xfd9e0000 - 0xfd9effff (0x10000) MX[b](B)
        [12] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [13] -1 0       0x00000000 - 0x000000ff (0x100) IX[b]
        [14] -1 0       0x0000c800 - 0x0000c807 (0x8) IX[b]
        [15] -1 0       0x0000cc00 - 0x0000cc1f (0x20) IX[b]
        [16] -1 0       0x0000d400 - 0x0000d407 (0x8) IX[b]
        [17] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[b]
        [18] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[b]
        [19] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[b]
        [20] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[b]
        [21] -1 0       0x00000970 - 0x00000977 (0x8) IX[b]
        [22] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[b]
        [23] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[b]
        [24] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[b]
        [25] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[b]
        [26] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[b]
        [27] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[b](B)
(II) fglrx(0): pEnt->device->identifier=0x81db970
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xfe02b000 - 0xfe02bfff (0x1000) MX[b]
        [5] -1  0       0xfe02c000 - 0xfe02cfff (0x1000) MX[b]
        [6] -1  0       0xfe02d000 - 0xfe02dfff (0x1000) MX[b]
        [7] -1  0       0xfe02e000 - 0xfe02e0ff (0x100) MX[b]
        [8] -1  0       0xfe02f000 - 0xfe02ffff (0x1000) MX[b]
        [9] -1  0       0xfd9f0000 - 0xfd9fffff (0x10000) MX[b](B)
        [10] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [11] -1 0       0xfd9e0000 - 0xfd9effff (0x10000) MX[b](B)
        [12] 0  0       0x000a0000 - 0x000affff (0x10000) MS[b]
        [13] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[b]
        [14] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[b]
        [15] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [16] -1 0       0x00000000 - 0x000000ff (0x100) IX[b]
        [17] -1 0       0x0000c800 - 0x0000c807 (0x8) IX[b]
        [18] -1 0       0x0000cc00 - 0x0000cc1f (0x20) IX[b]
        [19] -1 0       0x0000d400 - 0x0000d407 (0x8) IX[b]
        [20] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[b]
        [21] -1 0       0x0000dc00 - 0x0000dcff (0x100) IX[b]
        [22] -1 0       0x0000e000 - 0x0000e00f (0x10) IX[b]
        [23] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[b]
        [24] -1 0       0x00000970 - 0x00000977 (0x8) IX[b]
        [25] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[b]
        [26] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[b]
        [27] -1 0       0x0000f400 - 0x0000f40f (0x10) IX[b]
        [28] -1 0       0x00001c40 - 0x00001c7f (0x40) IX[b]
        [29] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[b]
        [30] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[b](B)
        [31] 0  0       0xfd9003b0 - 0xfd9003bb (0xc) IS[b]
        [32] 0  0       0xfd9003c0 - 0xfd9003df (0x20) IS[b]
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

FYI, I followed the ATI-Drivers howto from the unofficial ATI wiki generating packages for Ubuntu/dapper from Ati-drivers 8.28

---

### Post by varean on 2006-09-02
No one has any ideas?

Here is my dmesg.
```
f 00000000 00000410 00000001 00000000 00000001
[17179569.820000] mtrr: v2.0 (20020519)
[17179569.820000] CPU: AMD Athlon(tm) 64 Processor 3500+ stepping 01
[17179569.820000] Enabling fast FPU save and restore... done.
[17179569.820000] Enabling unmasked SIMD FPU exception support... done.
[17179569.820000] Checking 'hlt' instruction... OK.
[17179569.836000] checking if image is initramfs... it is
[17179570.276000] Freeing initrd memory: 6617k freed
[17179570.288000] ACPI: Looking for DSDT ... not found!
[17179570.292000] ENABLING IO-APIC IRQs
[17179570.292000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179570.440000] NET: Registered protocol family 16
[17179570.440000] EISA bus registered
[17179570.440000] ACPI: bus type pci registered
[17179570.440000] PCI: PCI BIOS revision 3.00 entry at 0xfa7c0, last bus=4
[17179570.440000] PCI: Using MMCONFIG
[17179570.440000] ACPI: Subsystem revision 20051216
[17179570.448000] ACPI: Interpreter enabled
[17179570.448000] ACPI: Using IOAPIC for interrupt routing
[17179570.448000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.448000] PCI: Probing PCI hardware (bus 00)
[17179570.452000] Boot video device is 0000:03:00.0
[17179570.452000] PCI: Transparent bridge - 0000:00:10.0
[17179570.452000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.548000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179570.552000] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)
[17179570.552000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.552000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.552000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.552000] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 *10 11 14 15)
[17179570.552000] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.552000] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.552000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.552000] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[17179570.552000] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.552000] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[17179570.552000] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 *11 14 15)
[17179570.556000] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.556000] ACPI: PCI Interrupt Link [LPMU] (IRQs *5 7 9 10 11 14 15)
[17179570.556000] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.556000] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[17179570.556000] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[17179570.556000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.556000] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[17179570.556000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[17179570.556000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[17179570.556000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[17179570.556000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[17179570.556000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[17179570.556000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[17179570.560000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[17179570.560000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[17179570.560000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[17179570.560000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[17179570.560000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[17179570.560000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[17179570.560000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[17179570.560000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[17179570.560000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[17179570.560000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[17179570.560000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[17179570.560000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[17179570.564000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[17179570.564000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[17179570.564000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.564000] pnp: PnP ACPI init
[17179570.568000] pnp: PnP ACPI: found 13 devices
[17179570.568000] PnPBIOS: Disabled by ACPI PNP
[17179570.568000] PCI: Using ACPI for IRQ routing
[17179570.568000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.668000] pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
[17179570.668000] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
[17179570.668000] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
[17179570.668000] pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
[17179570.668000] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
[17179570.668000] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
[17179570.668000] pnp: 00:00: ioport range 0x2000-0x207f has been reserved
[17179570.668000] pnp: 00:00: ioport range 0x2080-0x20ff has been reserved
[17179570.668000] PCI: Bridge: 0000:00:02.0
[17179570.668000]   IO window: a000-afff
[17179570.668000]   MEM window: fd800000-fd8fffff
[17179570.668000]   PREFETCH window: fde00000-fdefffff
[17179570.668000] PCI: Bridge: 0000:00:03.0
[17179570.668000]   IO window: 9000-9fff
[17179570.668000]   MEM window: fdd00000-fddfffff
[17179570.668000]   PREFETCH window: fdc00000-fdcfffff
[17179570.668000] PCI: Bridge: 0000:00:04.0
[17179570.668000]   IO window: b000-bfff
[17179570.668000]   MEM window: fd900000-fd9fffff
[17179570.668000]   PREFETCH window: d0000000-dfffffff
[17179570.668000] PCI: Bridge: 0000:00:10.0
[17179570.668000]   IO window: c000-cfff
[17179570.668000]   MEM window: fdb00000-fdbfffff
[17179570.668000]   PREFETCH window: fda00000-fdafffff
[17179570.668000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179570.668000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[17179570.668000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179570.668000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[17179570.668000] audit: initializing netlink socket (disabled)
[17179570.668000] audit(1156685917.668:1): initialized
[17179570.668000] VFS: Disk quotas dquot_6.5.1
[17179570.668000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.668000] Initializing Cryptographic API
[17179570.668000] io scheduler noop registered
[17179570.668000] io scheduler anticipatory registered
[17179570.668000] io scheduler deadline registered
[17179570.668000] io scheduler cfq registered
[17179578.668000] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[17179578.668000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179578.668000] pcie_portdrv_probe->Dev[02fc:10de] has invalid IRQ. Check vendor BIOS
[17179578.668000] assign_interrupt_mode Found MSI capability
[17179578.668000] Allocate Port Service[pcie00]
[17179578.668000] Allocate Port Service[pcie03]
[17179578.668000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[17179578.668000] pcie_portdrv_probe->Dev[02fd:10de] has invalid IRQ. Check vendor BIOS
[17179578.668000] assign_interrupt_mode Found MSI capability
[17179578.668000] Allocate Port Service[pcie00]
[17179578.668000] Allocate Port Service[pcie03]
[17179578.668000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179578.668000] pcie_portdrv_probe->Dev[02fb:10de] has invalid IRQ. Check vendor BIOS
[17179578.668000] assign_interrupt_mode Found MSI capability
[17179578.668000] Allocate Port Service[pcie00]
[17179578.668000] Allocate Port Service[pcie03]
[17179578.668000] isapnp: Scanning for PnP cards...
[17179579.020000] isapnp: No Plug & Play device found
[17179579.032000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179579.584000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179579.588000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179579.588000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179579.588000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179579.588000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179579.588000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179579.588000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179579.588000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179579.588000] mice: PS/2 mouse device common for all mice
[17179579.600000] EISA: Probing bus 0 at eisa.0
[17179579.600000] Cannot allocate resource for EISA slot 1
[17179579.600000] Cannot allocate resource for EISA slot 2
[17179579.600000] EISA: Detected 0 cards.
[17179579.600000] NET: Registered protocol family 2
[17179579.648000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179579.660000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179579.660000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179579.660000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179579.660000] TCP: Hash tables configured (established 16384 bind 16384)
[17179579.660000] TCP reno registered
[17179579.660000] TCP bic registered
[17179579.660000] NET: Registered protocol family 1
[17179579.660000] NET: Registered protocol family 8
[17179579.660000] NET: Registered protocol family 20
[17179579.660000] Using IPI Shortcut mode
[17179579.660000] ACPI wakeup devices: 
[17179579.660000] SLPB HUB0 XVRA XVRB XVRC USB0 USB2 AZAD MMAC MMCI UAR1 
[17179579.660000] ACPI: (supports S0 S3 S4 S5)
[17179579.660000] Freeing unused kernel memory: 288k freed
[17179579.692000] vga16fb: initializing
[17179579.692000] vga16fb: mapped to 0xc00a0000
[17179579.796000] Console: switching to colour frame buffer device 80x25
[17179579.796000] fb0: VGA16 VGA frame buffer device
[17179580.896000] Capability LSM initialized
[17179580.916000] ACPI: Fan [FAN] (on)
[17179580.920000] ACPI: Thermal Zone [THRM] (41 C)
[17179581.252000] SCSI subsystem initialized
[17179581.252000] ACPI: bus type scsi registered
[17179581.252000] libata version 1.20 loaded.
[17179581.256000] sata_nv 0000:00:0e.0: version 0.8
[17179581.256000] **** SET: Misaligned resource pointer: dfa3bd02 Type 07 Len 0
[17179581.256000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[17179581.256000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 209
[17179581.256000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179581.256000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xE000 irq 209
[17179581.256000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xE008 irq 209
[17179581.624000] ata1: dev 0 cfg 00:427a 49:2f00 82:746b 83:7f61 84:4023 85:7469 86:3e41 87:4023 88:407f 93:0000
[17179581.624000] ata1: dev 0 ATA-7, max UDMA/133, 312581808 sectors: LBA48
[17179581.624000] sata_get_dev_handle: SATA dev addr=0xe0000, handle=0xdfedafe0
[17179581.632000] ata1: dev 0 configured for UDMA/133
[17179581.636000] sata_get_dev_handle: SATA dev addr=0xe0000, handle=0xdfedafe0
[17179581.644000] scsi0 : sata_nv
[17179581.848000] ata2: no device found (phy stat 00000000)
[17179581.848000] scsi1 : sata_nv
[17179581.848000]   Vendor: ATA       Model: WDC WD1600JS-19N  Rev: 10.0
[17179581.848000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179581.848000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[17179581.848000] NFORCE-MCP51: chipset revision 161
[17179581.848000] NFORCE-MCP51: not 100% native mode: will probe irqs later
[17179581.848000] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[17179581.848000]     ide0: BM-DMA at 0xf400-0xf407, BIOS settings: hda:DMA, hdb:DMA
[17179581.848000]     ide1: BM-DMA at 0xf408-0xf40f, BIOS settings: hdc:DMA, hdd:DMA
[17179581.848000] Probing IDE interface ide0...
[17179581.860000] Driver 'sd' needs updating - please use bus_type methods
[17179581.860000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17179581.860000] SCSI device sda: drive cache: write back
[17179581.864000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17179581.864000] SCSI device sda: drive cache: write back
[17179581.864000]  sda: sda1 sda2 < sda5 >
[17179581.912000] sd 0:0:0:0: Attached scsi disk sda
[17179582.416000] Probing IDE interface ide1...
[17179582.704000] hdc: WDC WD1200JB-00GVA0, ATA DISK drive
[17179583.152000] hdd: DVDRW IDE 16X, ATAPI CD/DVD-ROM drive
[17179583.208000] ide1 at 0x170-0x177,0x376 on irq 15
[17179583.232000] hdc: max request size: 1024KiB
[17179583.240000] hdc: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(33)
[17179583.240000] hdc: cache flushes supported
[17179583.240000]  hdc: hdc1
[17179583.264000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179583.264000] Uniform CD-ROM driver Revision: 3.20
[17179583.516000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179583.516000] **** SET: Misaligned resource pointer: dfa3b302 Type 07 Len 0
[17179583.516000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[17179583.516000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 217
[17179583.516000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[17179583.516000] forcedeth: using HIGHDMA
[17179583.564000] usbcore: registered new driver usbfs
[17179583.564000] usbcore: registered new driver hub
[17179583.564000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179583.564000] **** SET: Misaligned resource pointer: dfbb1dc2 Type 07 Len 0
[17179583.564000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[17179583.564000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 225
[17179583.564000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179583.564000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[17179583.584000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[17179583.584000] ohci_hcd 0000:00:0b.0: irq 225, io mem 0xfe02f000
[17179583.640000] hub 1-0:1.0: USB hub found
[17179583.640000] hub 1-0:1.0: 8 ports detected
[17179583.744000] **** SET: Misaligned resource pointer: dfbb1ac2 Type 07 Len 0
[17179583.744000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179583.744000] ACPI: PCI Interrupt 0000:00:0b.1[b] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 233
[17179583.744000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[17179583.744000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[17179583.744000] ehci_hcd 0000:00:0b.1: debug port 1
[17179583.744000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[17179583.744000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[17179583.744000] ehci_hcd 0000:00:0b.1: irq 233, io mem 0xfe02e000
[17179583.744000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179583.744000] hub 2-0:1.0: USB hub found
[17179583.744000] hub 2-0:1.0: 8 ports detected
[17179584.036000] eth0: forcedeth.c: subsystem: 01565:2501 bound to 0000:00:14.0
[17179584.060000] Probing IDE interface ide0...
[17179584.088000] ohci_hcd 0000:00:0b.0: wakeup
[17179584.472000] usb 1-3: new full speed USB device using ohci_hcd and address 2
[17179584.688000] Attempting manual resume
[17179584.712000] EXT3-fs: mounted filesystem with ordered data mode.
[17179584.724000] kjournald starting.  Commit interval 5 seconds
[17179594.204000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179595.324000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179595.328000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179595.612000] drivers/usb/net/atmel/at76_usbdfu.c: USB Device Firmware Upgrade (DFU) handler v0.12beta23-fw_dwl loading
[17179595.612000] drivers/usb/net/atmel/at76c503.c: Generic Atmel at76c503/at76c505 routines v0.12beta23-fw_dwl
[17179595.612000] drivers/usb/net/atmel/at76c503-fw_skel.c: Atmel at76c503 (RFMD) Wireless LAN Driver v0.12beta23-fw_dwl loading
[17179595.612000] drivers/usb/net/atmel/at76c503-fw_skel.c: downloading firmware atmel_at76c503-rfmd.bin
[17179595.632000] input: PC Speaker as /class/input/input1
[17179595.716000] parport: PnPBIOS parport detected.
[17179595.716000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179595.724000] parport0: Printer, HEWLETT-PACKARD DESKJET 840C
[17179595.740000] Real Time Clock Driver v1.12
[17179595.756000] Floppy drive(s): fd0 is 1.44M
[17179595.780000] FDC 0 is a post-1991 82077
[17179595.852000] **** SET: Misaligned resource pointer: dc25a7c2 Type 07 Len 0
[17179595.852000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23
[17179595.852000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [APCJ] -> GSI 23 (level, low) -> IRQ 209
[17179595.852000] PCI: Setting latency timer of device 0000:00:10.2 to 64
[17179595.908000] logips2pp: Detected unknown logitech mouse model 109
[17179596.048000] drivers/usb/net/atmel/at76c503-fw_skel.c: got it.
[17179596.056000] drivers/usb/net/atmel/at76c503.c: $Id: at76c503.c,v 1.74 2005/03/08 01:33:14 jal2 Exp $ compiled Aug  3 2006 03:05:22
[17179596.056000] drivers/usb/net/atmel/at76c503.c: firmware version 0.90.1 #44 (fcs_len 4)
[17179596.060000] drivers/usb/net/atmel/at76c503.c: device's MAC 00:06:25:27:85:80, regulatory domain FCC (U.S) (id 16)
[17179596.060000] drivers/usb/net/atmel/at76c503.c: registered wlan0
[17179596.060000] usbcore: registered new driver at76c503-rfmd
[17179596.172000] intel8x0_measure_ac97_clock: measured 54803 usecs
[17179596.172000] intel8x0: clocking to 46974
[17179596.372000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[17179596.760000] **** SET: Misaligned resource pointer: df365a02 Type 07 Len 0
[17179596.760000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[17179596.760000] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 50
[17179596.796000] ts: Compaq touchscreen protocol output
[17179596.832000] gameport: EMU10K1 is pci0000:04:08.1/gameport0, io 0xc800, speed 1028kHz
[17179597.404000] lp0: using parport0 (interrupt-driven).
[17179597.440000] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[17179597.576000] EXT3 FS on sda1, internal journal
[17179597.724000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179597.724000] md: bitmap version 4.39
[17179597.924000] NET: Registered protocol family 17
[17179598.256000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179599.696000] NET: Registered protocol family 10
[17179599.696000] lo: Disabled Privacy Extensions
[17179599.696000] IPv6 over IPv4 tunneling driver
[17179601.848000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179601.904000] NTFS volume version 3.0.
[17179606.172000] ACPI: Power Button (FF) [PWRF]
[17179606.172000] ACPI: Power Button (CM) [PWRB]
[17179606.172000] ACPI: Sleep Button (CM) [SLPB]
[17179606.240000] ibm_acpi: ec object not found
[17179606.268000] pcc_acpi: loading...
[17179606.716000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[17179606.716000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8 (1350 mV)
[17179606.716000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8 (1350 mV)
[17179606.716000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[17179606.716000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[17179606.716000] cpu_init done, current fid 0xe, vid 0x8
[17179610.172000] Linux agpgart interface v0.101 (c) Dave Jones
[17179610.200000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179610.200000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179610.200000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179610.252000] **** SET: Misaligned resource pointer: de0c0b02 Type 07 Len 0
[17179610.252000] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[17179610.252000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 50
[17179610.536000] wlan0: no IPv6 routers present
[17179611.004000] ppdev: user-space parallel port driver
[17179611.372000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179611.372000] apm: overridden by ACPI.
[17179612.016000] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17179614.788000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 50
[17179615.516000] Bluetooth: Core ver 2.8
[17179615.516000] NET: Registered protocol family 31
[17179615.516000] Bluetooth: HCI device and connection manager initialized
[17179615.516000] Bluetooth: HCI socket layer initialized
[17179615.560000] Bluetooth: L2CAP ver 2.8
[17179615.560000] Bluetooth: L2CAP socket layer initialized
[17179615.564000] Bluetooth: RFCOMM socket layer initialized
[17179615.564000] Bluetooth: RFCOMM TTY layer initialized
[17179615.564000] Bluetooth: RFCOMM ver 1.7
[17179619.236000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC5] -> G
```

---

### Post by JNowka on 2006-09-02
I don't have ATI card, but I did a little search. I found a guide on installing drivers for your card.  I don't know if you tried to follow this or not, but I find it easiest to follow the guides.  Alot of the time there are alot of things you have to do to the system by hand when installing new drivers.

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

---

### Post by varean on 2006-09-02
I followed a guide similar to that.  Here is the link to it: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I am using the latest version of ati-drivers (8.28.8)

---

### Post by varean on 2006-09-08
Hate to do this, but *bump*

---

