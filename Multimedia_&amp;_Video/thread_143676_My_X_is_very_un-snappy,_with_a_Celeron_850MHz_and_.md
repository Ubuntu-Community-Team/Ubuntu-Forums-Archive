---
title: "My X is very un-snappy, with a Celeron 850MHz and Intel 810e integrated video."
date: 2006-03-12
forum: Multimedia &amp; Video
---

### Post by OfficeLinebacker on 2006-03-12
So I've been told this hardware should be plenty for fien performance in GNOME, but it's not.  I've tried IceWm and it's slightly better, but I don't think it's performing up to it's potential, especially given that Win98 was snappier.  
 
 
Are there special considerations for this chipset?
 
I did reconfigure X and the system seemed to recognize that it was an 810e.  
 
I've seen mention of drivers at freedesktop.org, but I wouldn't even knwo how to begin.
 
Another alternative would be to put in a very basic PCI Video card, but I am wary of adding new hardware now that my install is stable (not easy to get to this point!)
 
Thanks!

---

### Post by OfficeLinebacker on 2006-03-13
bump

---

### Post by aysiu on 2006-03-13
IceWM is only *slightly* better? Something's wrong. What kind of RAM do you have--128 MB? 64 MB?

---

### Post by OfficeLinebacker on 2006-03-14
I have 384 and I tried allocating 64 to video with no improvement.

---

### Post by Teroedni on 2006-03-14
I think you have X server problems 



Could you post your Xorg.0.log file here?
All of it;)

```
sudo gedit /var/log/Xorg.0.log

```

I will read it true too see if i can spot any problem:)

---

### Post by OfficeLinebacker on 2006-03-14
Oops. file is too long.  I'll have to split it into two posts.

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
    Before reporting problems, check http://wiki.X.Org
    to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar 12 22:45:11 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel Corporation 82810 CGC [Chipset Graphics Controller]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
    Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.2
    X.Org Video Driver: 0.7
    X.Org XInput driver : 0.4
    X.Org Server Extension : 0.2
    X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7120 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7121 card 8086,7123 rev 03 class 03,00,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2418 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2410 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2411 card 8086,2411 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2412 card 8086,2412 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2413 card 8086,2413 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2415 card 8086,5643 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:0a:0: chip 10ec,8029 card 10ec,8029 rev 00 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
    [0] -1    0    0x00002000 - 0x000020ff (0x100) IX[B]
    [1] -1    0    0x00002400 - 0x000024ff (0x100) IX[B]
    [2] -1    0    0x00002800 - 0x000028ff (0x100) IX[B]
    [3] -1    0    0x00002c00 - 0x00002cff (0x100) IX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:1:0) Intel Corp. 82810 CGC [Chipset Graphics Controller] rev 3, Mem @ 0xf8000000/26, 0xf4000000/19
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [6] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
    [0] -1    0    0xf4000000 - 0xf407ffff (0x80000) MX[B](B)
    [1] -1    0    0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
    [2] -1    0    0x00002000 - 0x0000201f (0x20) IX[B]
    [3] -1    0    0x00001300 - 0x0000133f (0x40) IX[B]
    [4] -1    0    0x00001200 - 0x000012ff (0x100) IX[B]
    [5] -1    0    0x000010b0 - 0x000010bf (0x10) IX[B]
    [6] -1    0    0x00001080 - 0x0000109f (0x20) IX[B]
    [7] -1    0    0x000010a0 - 0x000010af (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xf4000000 - 0xf407ffff (0x80000) MX[B](B)
    [1] -1    0    0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
    [2] -1    0    0x00002000 - 0x0000201f (0x20) IX[B]
    [3] -1    0    0x00001300 - 0x0000133f (0x40) IX[B]
    [4] -1    0    0x00001200 - 0x000012ff (0x100) IX[B]
    [5] -1    0    0x000010b0 - 0x000010bf (0x10) IX[B]
    [6] -1    0    0x00001080 - 0x0000109f (0x20) IX[B]
    [7] -1    0    0x000010a0 - 0x000010af (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [6] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0xf4000000 - 0xf407ffff (0x80000) MX[B](B)
    [6] -1    0    0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [9] -1    0    0x00002000 - 0x0000201f (0x20) IX[B]
    [10] -1    0    0x00001300 - 0x0000133f (0x40) IX[B]
    [11] -1    0    0x00001200 - 0x000012ff (0x100) IX[B]
    [12] -1    0    0x000010b0 - 0x000010bf (0x10) IX[B]
    [13] -1    0    0x00001080 - 0x0000109f (0x20) IX[B]
    [14] -1    0    0x000010a0 - 0x000010af (0x10) IX[B]
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 6.8.2, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.2
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.1.0
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "i810"
(II) Loading /usr/X11R6/lib/modules/drivers/i810_drv.o
(II) Module i810: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.4.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.4
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
    i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
    915GM, 945G
(II) Primary Device is: PCI 00:01:0
(--) Chipset i810 found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0xf4000000 - 0xf407ffff (0x80000) MX[B](B)
    [6] -1    0    0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [9] -1    0    0x00002000 - 0x0000201f (0x20) IX[B]
    [10] -1    0    0x00001300 - 0x0000133f (0x40) IX[B]
    [11] -1    0    0x00001200 - 0x000012ff (0x100) IX[B]
    [12] -1    0    0x000010b0 - 0x000010bf (0x10) IX[B]
    [13] -1    0    0x00001080 - 0x0000109f (0x20) IX[B]
    [14] -1    0    0x000010a0 - 0x000010af (0x10) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0xf4000000 - 0xf407ffff (0x80000) MX[B](B)
    [6] -1    0    0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
    [7] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [8] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [9] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [10] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [11] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [12] -1    0    0x00002000 - 0x0000201f (0x20) IX[B]
    [13] -1    0    0x00001300 - 0x0000133f (0x40) IX[B]
    [14] -1    0    0x00001200 - 0x000012ff (0x100) IX[B]
    [15] -1    0    0x000010b0 - 0x000010bf (0x10) IX[B]
    [16] -1    0    0x00001080 - 0x0000109f (0x20) IX[B]
    [17] -1    0    0x000010a0 - 0x000010af (0x10) IX[B]
    [18] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [19] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 0.7
(**) I810(0): Depth 24, (--) framebuffer bpp 24
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.2.0
    ABI class: X.Org Video Driver, version 0.7
(**) I810(0): DRI is disabled because it runs only at 16-bit depth.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 1024 kB
(II) I810(0): VESA VBE OEM: Intel(R) 8xx Chipset Video BIOS
(II) I810(0): VESA VBE OEM Software Rev: 4.1
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(R) 8xx Chipset
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: GWY  Model: 232c  Serial#: 50824
(II) I810(0): Year: 2001  Week: 17
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) I810(0): Signal levels configurable
(II) I810(0): Sync:  Separate  Composite
(II) I810(0): Max H-Image Size [cm]: horiz.: 36  vert.: 27
(II) I810(0): Gamma: 2.70
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): First detailed timing not preferred mode in violation of standard!(II) I810(0): GTF timings supported
(II) I810(0): redX: 0.638 redY: 0.326   greenX: 0.279 greenY: 0.602
(II) I810(0): blueX: 0.142 blueY: 0.062   whiteX: 0.282 whiteY: 0.298
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 720x400@88Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@67Hz
(II) I810(0): 640x480@72Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@56Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@72Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 832x624@75Hz
(II) I810(0): 1024x768@87Hz (interlaced)
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@70Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): 1152x870@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) I810(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) I810(0): #2: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) I810(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) I810(0): #4: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) I810(0): #5: hsize: 720  vsize 405  refresh: 70  vid: 51771
(II) I810(0): #6: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) I810(0): #7: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 202.5 MHz   Image Size:  350 x 262 mm
(II) I810(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) I810(0): v_active: 1200  v_sync: 1201  v_sync_end 1201 v_blanking: 1250 v_border: 0
(II) I810(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 95 kHz, PixClock max 200 MHz
(II) I810(0): Monitor name: Gateway EV910
(II) I810(0): Monitor name: 
(--) I810(0): Chipset: "i810"
(--) I810(0): Linear framebuffer at 0xF8000000
(--) I810(0): IO registers at addr 0xF4000000
(II) I810(0): I810CheckAvailableMemory: 327676k available
(**) I810(0): Will alloc AGP framebuffer: 65536 kByte
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(WW) I810(0): config file hsync range 28-49kHz not within DDC hsync ranges.
(WW) I810(0): config file vrefresh range 43-72Hz not within DDC vrefresh ranges.
(II) I810(0): Generic Monitor: Using hsync range of 28.00-49.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 43.00-72.00 Hz
(II) I810(0): Clock range:   9.50 to 136.00 MHz
(II) I810(0): Not using default mode "640x350" (vrefresh out of range)
(II) I810(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x400" (vrefresh out of range)
(II) I810(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "720x400" (vrefresh out of range)
(II) I810(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (vrefresh out of range)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (vrefresh out of range)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (vrefresh out of range)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (vrefresh out of range)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (hsync out of range)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (unknown reason)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (hsync out of range)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (hsync out of range)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (hsync out of range)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1152x864" (hsync out of range)
(II) I810(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x960" (hsync out of range)
(II) I810(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x1024" (hsync out of range)
(II) I810(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x1024" (hsync out of range)
(II) I810(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "832x624" (hsync out of range)
(II) I810(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x800" (hsync out of range)
(II) I810(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1152x864" (hsync out of range)
(II) I810(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (hsync out of range)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1440x900" (hsync out of range)
(II) I810(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1024" (hsync out of range)
(II) I810(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x768" (width too large for virtual size)
(II) I810(0): Not using default mode "1152x768" (width too large for virtual size)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) I810(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) I810(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) I810(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) I810(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) I810(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) I810(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) I810(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) I810(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) I810(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(--) I810(0): Display dimensions: (360, 270) mm
(--) I810(0): DPI set to (72, 72)

```

---

### Post by OfficeLinebacker on 2006-03-14
Oops. file is too long.  I'll have to split it into two posts.

```

(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 0.7
(II) I810(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xf4000000 - 0xf407ffff (0x80000) MS[B]
    [1] 0    0    0xf8000000 - 0xfbffffff (0x4000000) MS[B]
    [2] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [3] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [4] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [5] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [6] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [7] -1    0    0xf4000000 - 0xf407ffff (0x80000) MX[B](B)
    [8] -1    0    0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
    [9] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
    [10] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
    [11] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
    [12] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [13] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [14] -1    0    0x00002000 - 0x0000201f (0x20) IX[B]
    [15] -1    0    0x00001300 - 0x0000133f (0x40) IX[B]
    [16] -1    0    0x00001200 - 0x000012ff (0x100) IX[B]
    [17] -1    0    0x000010b0 - 0x000010bf (0x10) IX[B]
    [18] -1    0    0x00001080 - 0x0000109f (0x20) IX[B]
    [19] -1    0    0x000010a0 - 0x000010af (0x10) IX[B]
    [20] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [21] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) I810(0): Write-combining range (0xf8000000,0x4000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) I810(0): Setting dot clock to 65.0 MHz [ 0x3f 0xa 0x30 ] [ 65 12 3 ]
(II) I810(0): chose watermark 0x22214000: (tab.freq 65.0)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x00000000 (pgoffset 0)
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1024 pages failed
    (Cannot allocate memory)
(II) I810(0): No physical memory available for 4194304 bytes of DCACHE
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x04000000 (pgoffset 16384)
(WW) I810(0): xf86BindGARTMemory: binding of gart memory with key 1
    at offset 0x4000000 failed (Invalid argument)
(II) I810(0): Allocation of 4096 bytes for HW cursor failed
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x04000000 (pgoffset 16384)
(WW) I810(0): xf86BindGARTMemory: binding of gart memory with key 2
    at offset 0x4000000 failed (Invalid argument)
(II) I810(0): Allocation of 16384 bytes for ARGB HW cursor failed
(II) I810(0): Adding 512 scanlines for pixmap caching
(II) I810(0): Allocated Scratch Memory
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Horizontal and Vertical Lines
    Offscreen Pixmaps
    Setting up tile and stipple cache:
        16 128x128 slots
        4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(**) Option "dpms"
(**) I810(0): DPMS enabled
(WW) I810(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Got unexpected buttonTimer in state 0

``` 
Also,

DAMN you, 20 second rule!  *shakes fist

---

### Post by OfficeLinebacker on 2006-03-14
```


(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 0.7
(II) I810(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xf4000000 - 0xf407ffff (0x80000) MS[B]
    [1] 0    0    0xf8000000 - 0xfbffffff (0x4000000) MS[B]
    [2] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [3] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [4] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [5] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [6] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [7] -1    0    0xf4000000 - 0xf407ffff (0x80000) MX[B](B)
    [8] -1    0    0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
    [9] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
    [10] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
    [11] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
    [12] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [13] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [14] -1    0    0x00002000 - 0x0000201f (0x20) IX[B]
    [15] -1    0    0x00001300 - 0x0000133f (0x40) IX[B]
    [16] -1    0    0x00001200 - 0x000012ff (0x100) IX[B]
    [17] -1    0    0x000010b0 - 0x000010bf (0x10) IX[B]
    [18] -1    0    0x00001080 - 0x0000109f (0x20) IX[B]
    [19] -1    0    0x000010a0 - 0x000010af (0x10) IX[B]
    [20] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [21] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) I810(0): Write-combining range (0xf8000000,0x4000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) I810(0): Setting dot clock to 65.0 MHz [ 0x3f 0xa 0x30 ] [ 65 12 3 ]
(II) I810(0): chose watermark 0x22214000: (tab.freq 65.0)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x00000000 (pgoffset 0)
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1024 pages failed
    (Cannot allocate memory)
(II) I810(0): No physical memory available for 4194304 bytes of DCACHE
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x04000000 (pgoffset 16384)
(WW) I810(0): xf86BindGARTMemory: binding of gart memory with key 1
    at offset 0x4000000 failed (Invalid argument)
(II) I810(0): Allocation of 4096 bytes for HW cursor failed
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x04000000 (pgoffset 16384)
(WW) I810(0): xf86BindGARTMemory: binding of gart memory with key 2
    at offset 0x4000000 failed (Invalid argument)
(II) I810(0): Allocation of 16384 bytes for ARGB HW cursor failed
(II) I810(0): Adding 512 scanlines for pixmap caching
(II) I810(0): Allocated Scratch Memory
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Horizontal and Vertical Lines
    Offscreen Pixmaps
    Setting up tile and stipple cache:
        16 128x128 slots
        4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(**) Option "dpms"
(**) I810(0): DPMS enabled
(WW) I810(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Got unexpected buttonTimer in state 0

```

---

### Post by landotter on 2006-03-14
I have an i810 and it works fine, the card section of my xorg.conf reads

> Section "Device"
    Identifier    "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
    Driver        "i810"
    BusID        "PCI:0:1:0"
#    VideoRam    32
    Option        "UseFBDev"        "false"
EndSection


---

### Post by OfficeLinebacker on 2006-03-14
Whew.

Looks like several (WW)s .  I hope this gives you something to go on, and thanks!

---

### Post by landotter on 2006-03-14
btw, an i810 onboard should barely let you used GL screensavers, it's not a very powerful chip, but good enough for work.

---

### Post by OfficeLinebacker on 2006-03-14
I'll go ahead and find and post my Xorg.conf file also, landotter.

---

### Post by OfficeLinebacker on 2006-03-14
```

Section "Device"
    Identifier    "Intel Corporation 82810 CGC [Chipset Graphics Controller]"
    Driver        "i810"
    BusID        "PCI:0:1:0"
    VideoRam    65536
EndSection

```

---

### Post by landotter on 2006-03-14
comment out the videoram section, afaik it gets automatically allocated and that line confuses xorg.

---

### Post by landotter on 2006-03-14
If you absolutely can't fix it and you're in the US, get a $20 Nvidia 32mb card from Amazon. Works perfectly fine for basic use, Tux Racer, and most importantly, the bouncing cow screensaver. It will work out of the box, and you can just use Automatix to install the real driver.

---

### Post by OfficeLinebacker on 2006-03-14
Allocating more memory was one of my attempts to "FIX" this, it runs the same regardless.

---

### Post by OfficeLinebacker on 2006-03-14
Also, I do have some low-end PCI Video cards that I could throw in there.  I don't think they're even 32MB though.

---

### Post by OfficeLinebacker on 2006-03-16
Bump

---

### Post by Teroedni on 2006-03-17
```
(**) I810(0): DRI is disabled because it runs only at 16-bit depth.
```


If you use 16 bit depth instead you will get dri accel. Eg things will go faster;)

[COLOR="Red"]Demo!!!! this is taken from mine. Dont use it!!![/COLOR]
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40? [Unknown nVidia Card]"
	Monitor		"M1900"
	DefaultDepth	24<------here you set it.
	SubSection "Display"
```
[COLOR="Red"]Demo!!!![/COLOR]

Change your default depth from 24 to 16 and dri should work:)





```
(==) I810(0): Backing store disabled
```
I dont know about Intel, but on old ati card it helps to turn  backings store on

In your display section write this
```
 Option "backingstore" "true"
```


Here is some info for your card
[http://www.die.net/doc/linux/man/man4/i810.4.html](http://www.die.net/doc/linux/man/man4/i810.4.html)

---

### Post by OfficeLinebacker on 2006-03-17
> **Teroedni]```
(**) I810(0): DRI is disabled because it runs only at 16-bit depth.
``` 

If you use 16 bit depth instead you will get dri accel. Eg things will go faster said:**
> Demo!!!! this is taken from mine. Dont use it!!![/COLOR]
```
Section &quot;Screen&quot;
    Identifier    &quot;Default Screen&quot;
    Device        &quot;NVIDIA Corporation NV40? [Unknown nVidia Card]&quot;
    Monitor        &quot;M1900&quot;
    DefaultDepth    24<------here you set it.
    SubSection &quot;Display&quot;
``` [COLOR=Red]Demo!!!![/COLOR]

Change your default depth from 24 to 16 and dri should work:)





```
(==) I810(0): Backing store disabled
``` I dont know about Intel, but on old ati card it helps to turn  backings store on

In your display section write this
```
 Option &quot;backingstore&quot; &quot;true&quot;
``` 

Here is some info for your card
[http://www.die.net/doc/linux/man/man4/i810.4.html]("http://www.die.net/doc/linux/man/man4/i810.4.html")   OK, this is exactly the type o thing I was looking for!  Set depth to 16 and commented out the part about allocating 64MB vRAM.  Once I get back in I will try backingstore.

---

### Post by OfficeLinebacker on 2006-03-17
Well, whaddya know?  Awesome.  THAT was the solution.  THANK YOU.

---

### Post by OfficeLinebacker on 2006-03-17
couldn't find a "Display" section in xorg.conf so no glory on that one, but the main problem is solved.  We're   GOODTOGO  makes hand wave motion

---

