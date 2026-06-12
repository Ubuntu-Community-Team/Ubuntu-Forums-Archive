---
title: "No direct rendering on IBM X41 (Intel i915 chipset)"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by cdos on 2006-09-18
I'm having issues with direct rendering.  After starting X, my glxinfo | grep direct results in:
```

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

So then, I looked at /var/log/Xorg.0.log and here's all of the i810 lines
```

(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
        i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 915GM
(--) I810(0): Chipset: "915GM"
(--) I810(0): Linear framebuffer at 0xC0000000
(--) I810(0): IO registers at addr 0xA0080000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 7932 kB stolen memory.
(II) I810(0): Kernel reported 238592 total, 1 used
(II) I810(0): I830CheckAvailableMemory: 954364 kB available
(II) I810(0): Monitoring connected displays enabled
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 12288 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 7932 kByte
(**) I810(0): VideoRAM: 262144 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 1239
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
(II) I810(0): Display Info: CRT: attached: FALSE, present: TRUE, size: (720,400)(II) I810(0): Display Info: TV: attached: FALSE, present: TRUE, size: (1024,768)(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,2059)
(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1024,768)
(II) I810(0): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,2059)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,2059)
(II) I810(0): Size of device LFP (local flat panel) is 1024 x 768
(II) I810(0): No active displays on Pipe A.
(II) I810(0): Currently active displays on Pipe B:
(II) I810(0):   LFP (local flat panel)
(II) I810(0): Lowest common panel size for pipe B is 1024 x 768
(==) I810(0): Display is using Pipe B
(--) I810(0): Maximum frambuffer space: 261976 kByte
(II) I810(0): VESA VBE PanelID read successfully
(II) I810(0): PanelID returned panel resolution : 1024x768
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(--) I810(0): A non-CRT device is attached to pipe B.
(--) I810(0): Maximum space available for video modes: 12288 kByte
(II) I810(0): Generic Monitor: Using hsync range of 30.00-65.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 50.00-75.00 Hz
(WW) I810(0): Allocation with DRI tiling enabled would exceed the
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(==) I810(0): DPI set to (75, 75)
(==) I810(0): VBE Restore workaround: enabled.
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 512 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 6144 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0xffff000 (0x36d73000)
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0xfffb000 (0x1dff4000)
(II) I810(0): Allocated 4 kB for Overlay registers at 0xfffa000 (0x22ac0000).
(WW) I810(0): xf86AllocateGARTMemory: allocation of 16 pages failed
(II) I810(0): Allocated 64 kB for the scratch buffer at 0xffea000
(II) I810(0): [drm] DRM interface version 1.2
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [drm] added 8192 byte SAREA at 0xf8d88000
(II) I810(0): [drm] mapped SAREA 0xf8d88000 to 0xb7896000
(II) I810(0): [drm] framebuffer handle = 0xc0020000
(II) I810(0): [drm] added 1 reserved context for kernel
(WW) I810(0): xf86AllocateGARTMemory: allocation of 8 pages failed
(II) I810(0): Allocated 32 kB for the logical context at 0xffe2000.
(WW) I810(0): xf86AllocateGARTMemory: allocation of 768 pages failed
(II) I810(0): Allocated 3072 kB for the back buffer at 0xfce2000.
(WW) I810(0): xf86AllocateGARTMemory: allocation of 768 pages failed
(II) I810(0): Allocated 3072 kB for the depth buffer at 0xf9e2000.
(II) I810(0): Allocated 248832 kB for textures at 0x620000
(WW) I810(0): xf86AllocateGARTMemory: allocation of 61793 pages failed
(II) I810(0): 0x81ff130: Memory at offset 0x00020000, size 6144 kBytes
(II) I810(0): 0x81ff748: Memory at offset 0x0ffff000, size 4 kBytes
(II) I810(0): 0x81ff7a8: Memory at offset 0x0fffb000, size 16 kBytes
(II) I810(0): 0x81ff714: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x81ff170: Memory at offset 0x0ffea000, size 64 kBytes
(II) I810(0): 0x81fad20: Memory at offset 0x0fffa000, size 4 kBytes
(II) I810(0): 0x81ff308: Memory at offset 0x0ffe2000, size 32 kBytes
(II) I810(0): 0x81ff328: Memory at offset 0x0fce2000, size 3072 kBytes
(II) I810(0): 0x81ff348: Memory at offset 0x0f9e2000, size 3072 kBytes
(II) I810(0): 0x81ff368: Memory at offset 0x00620000, size 248832 kBytes
(II) I810(0): [drm] Registers = 0xa0080000
(II) I810(0): [drm] ring buffer = 0xc0000000
(II) I810(0): [drm] init sarea width,height = 1024 x 768 (pitch 1024)
(II) I810(0): [drm] Mapping front buffer
(II) I810(0): [drm] Front Buffer = 0xc0020000
(II) I810(0): [drm] Back Buffer = 0xcfce2000
(II) I810(0): [drm] Depth Buffer = 0xcf9e2000
(II) I810(0): [drm] textures = 0xc0620000
(II) I810(0): [drm] Initialized kernel agp heap manager, 254803968
(II) I810(0): [drm] dma control initialized, using IRQ 177
(II) I810(0): [dri] visual configs initialized
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0ffe2000 (pgoffset 65506)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0fce2000 (pgoffset 64738)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0f9e2000 (pgoffset 63970)
(--) I810(0): A non-CRT device is attached to pipe B.
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x00000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) I810(0): DPMS enabled
(II) I810(0): Set up overlay video
(II) I810(0): Set up textured video
(II) I810(0): X context handle = 0x1
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
(II) I810(0): libshadow is version 1.0.0, required 1.1.0 or greater for rotation.
(WW) I810(0): Option "UseFBDev" is not used
(II) I810(0): Rotating to 0 degrees
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
(--) I810(0): A non-CRT device is attached to pipe B.
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(WW) I810(0): Successfully set original devices (2)
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0ffe2000 (pgoffset 65506)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0fce2000 (pgoffset 64738)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0f9e2000 (pgoffset 63970)
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(II) I810(0): Generic Monitor: Using hsync range of 30.00-65.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 50.00-75.00 Hz
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(--) I810(0): A non-CRT device is attached to pipe B.
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x00000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): [drm] dma control initialized, using IRQ 177
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
(--) I810(0): A non-CRT device is attached to pipe B.
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(WW) I810(0): Successfully set original devices (2)
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0ffe2000 (pgoffset 65506)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0fce2000 (pgoffset 64738)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0f9e2000 (pgoffset 63970)
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(II) I810(0): Generic Monitor: Using hsync range of 30.00-65.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 50.00-75.00 Hz
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(--) I810(0): A non-CRT device is attached to pipe B.
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x00000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): [drm] dma control initialized, using IRQ 177
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
(--) I810(0): A non-CRT device is attached to pipe B.
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(WW) I810(0): Successfully set original devices (2)
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0ffe2000 (pgoffset 65506)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0fce2000 (pgoffset 64738)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0f9e2000 (pgoffset 63970)
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(II) I810(0): Generic Monitor: Using hsync range of 30.00-65.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 50.00-75.00 Hz
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(--) I810(0): A non-CRT device is attached to pipe B.
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x00000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): [drm] dma control initialized, using IRQ 177
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
(--) I810(0): A non-CRT device is attached to pipe B.
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(WW) I810(0): Successfully set original devices (2)
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0ffe2000 (pgoffset 65506)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0fce2000 (pgoffset 64738)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0f9e2000 (pgoffset 63970)
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(II) I810(0): Generic Monitor: Using hsync range of 30.00-65.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 50.00-75.00 Hz
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(--) I810(0): A non-CRT device is attached to pipe B.
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x00000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): [drm] dma control initialized, using IRQ 177
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
(--) I810(0): A non-CRT device is attached to pipe B.
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(WW) I810(0): Successfully set original devices (2)
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0ffe2000 (pgoffset 65506)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0fce2000 (pgoffset 64738)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0f9e2000 (pgoffset 63970)
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(II) I810(0): Generic Monitor: Using hsync range of 30.00-65.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 50.00-75.00 Hz
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(--) I810(0): A non-CRT device is attached to pipe B.
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x00000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): [drm] dma control initialized, using IRQ 177
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
(--) I810(0): A non-CRT device is attached to pipe B.
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(WW) I810(0): Successfully set original devices (2)
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0ffe2000 (pgoffset 65506)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0fce2000 (pgoffset 64738)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0f9e2000 (pgoffset 63970)
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(II) I810(0): Generic Monitor: Using hsync range of 30.00-65.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 50.00-75.00 Hz
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(--) I810(0): A non-CRT device is attached to pipe B.
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x00000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): [drm] dma control initialized, using IRQ 177
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
(--) I810(0): A non-CRT device is attached to pipe B.
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(WW) I810(0): Successfully set original devices (2)
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0ffe2000 (pgoffset 65506)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0fce2000 (pgoffset 64738)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0f9e2000 (pgoffset 63970)
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(II) I810(0): Generic Monitor: Using hsync range of 30.00-65.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 50.00-75.00 Hz
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(--) I810(0): A non-CRT device is attached to pipe B.
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x00000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): [drm] dma control initialized, using IRQ 177

```

From the log, it seems as if the dri should be working, but again as noted above there is no direct rendering.

When I type lsmod | grep i915 I get:
```

i915                   21664  1
drm                    78484  2 i915

```

Does anyone know where the direct rendering is failing?  I've tried reinstalling some packages to no avail.

Any help is appreciated.

---

### Post by cdos on 2006-09-18
Also, here's my xorg.conf if it helps.  I kept trying to bump up the VideoRam setting, but it didn't appear to work.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        262144
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "dri"
        Mode    0666
EndSection

```

---

