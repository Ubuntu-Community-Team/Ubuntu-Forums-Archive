---
title: "Lockups with SiS630 when launching any DDraw/D3D applications with Wine"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by kissg1988 on 2007-08-21
Hello there,

I'm having some problems with my laptop using a SiS630 chipset.
My operating system is Ubuntu Feisty (7.04), with the latest updates installed.

When I try to run any native 3D applications, they work, but I experience some minor issues, like flickering objects (this happens very often when running OpenGL-based screen savers.)
I've tried to run Cube, it works okay. I get framerates around 25-30 fps.
If I try to run any DirecDraw of Direct3D-based applications under Wine, my computer locks up completely... I've read a lot on this on the net and I found, that the same problems exist with S3 Unichrome chips.

I hope you can help me, I really would like to lauch some games on my laptop.

Some outputs of commands, that may help you, if you want to help me (I hope so.. :))

```

**kissg@kissg:~$ dmesg | grep drm**
[   67.176384] [drm] Initialized drm 1.1.0 20060810
[   67.248532] [drm] Initialized sis 1.3.0 20070626 on minor 0

```
```

**kissg@kissg:~$ less /var/log/Xorg.0.log | grep SIS**
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
        SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
        SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
        SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
        SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
(--) Chipset SIS630/730 found
(II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 7.2.0.0)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See http://www.winischhofer.at/linuxsisvga.shtml
(II) SIS(0): *** for documentation and updates.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0xA000
(**) SIS(0): Depth 24, (--) framebuffer bpp 32
(==) SIS(0): RGB weight 888
(==) SIS(0): Default visual is TrueColor
(--) SIS(0): Video BIOS version "2.02.3f" found (old SiS data layout)
(**) SIS(0): Option "MaxXFBMem" "12288"
(**) SIS(0): Option "EnableSiSCtrl" "yes"
(**) SIS(0): MaxXFBMem: Framebuffer memory shall be limited to 12288 KB
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Using HW cursor
(==) SIS(0): Color HW cursor is disabled
(==) SIS(0): TurboQueue enabled
(==) SIS(0): Hotkey display switching is disabled
(II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SIS(0):          whether enabled or disabled. This is no driver bug.
(**) SIS(0): SiSCtrl utility interface is enabled
(==) SIS(0): DRI enabled
(--) SIS(0): Shared Memory Area is on DIMM1
(--) SIS(0): DRAM type: SDR SDRAM
(--) SIS(0): Memory clock: 100.226 MHz
(--) SIS(0): (Adapter assumes MCLK being 66 Mhz)
(--) SIS(0): DRAM bus width: 64 bit
(--) SIS(0): Linear framebuffer at 0xF0000000
(--) SIS(0): MMIO registers at 0xEC100000 (size 64K)
(--) SIS(0): VideoRAM: 32768 KB
(II) SIS(0): Using 12288K of framebuffer memory at offset 0K
(--) SIS(0): Hardware supports two video overlays
(--) SIS(0): Detected LVDS transmitter (External chip ID 4)
(--) SIS(0): Detected Chrontel 7005 TV encoder (ID 0x3a; chip ID 4)
(--) SIS(0): Chrontel: Detected TV connected to SVIDEO output
(--) SIS(0): No CRT1/VGA detected
(--) SIS(0): Detected LCD/plasma panel (1024x768, 15, non-exp., RGB18 [f2e9ff])
(--) SIS(0): Detected default TV standard PAL
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): CRT1 gamma correction is enabled
(--) SIS(0): CRT2 gamma correction not supported by hardware
(--) SIS(0): Memory bandwidth at 32 bpp is 200.452 MHz

```

I've left out some log messages regarding resolutions. The list is quite long and I can't see any problems with them.

```

(II) SIS(0): 2D acceleration enabled
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 32768 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 630
(II) SIS(0): VESA VBE OEM Product Rev: 2.02.3f
(==) SIS(0): Write-combining range (0xf0000000,0x2000000)
(II) SIS(0): Setting standard mode 0x64
(II) SIS(0): [drm] loaded kernel module for "sis" driver
(II) SIS(0): [drm] DRM interface version 1.3
(II) SIS(0): [drm] created "sis" driver at busid "pci:0000:01:00.0"
(II) SIS(0): [drm] added 8192 byte SAREA at 0xd6b54000
(II) SIS(0): [drm] mapped SAREA 0xd6b54000 to 0xb59e3000
(II) SIS(0): [drm] framebuffer handle = 0xf0000000
(II) SIS(0): [drm] added 1 reserved context for kernel
(II) SIS(0): [dri] Video RAM memory heap: 0xc00000 to 0x1f7f000 (19964KB)
(II) SIS(0): [drm] MMIO registers mapped to 0xec100000
(II) SIS(0): [drm] AGP enabled
(II) SIS(0): [drm] Allocated 8MB AGP memory
(II) SIS(0): [drm] Bound 8MB AGP memory
(II) SIS(0): [drm] No valid IRQ number for device 1:0:0 (code -22)
(II) SIS(0): [dri] Visual configs initialized
(II) SIS(0): Framebuffer from (0,0) to (1023,3069)
(II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
(--) SIS(0): CPU frequency 1102.58Mhz
(II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
(--) SIS(0):    Checked libc memcpy()...        118.8 MiB/s
(--) SIS(0):    Checked built-in-1 memcpy()...  118.8 MiB/s
(--) SIS(0):    Checked built-in-2 memcpy()...  50.4 MiB/s
(--) SIS(0):    Checked MMX memcpy()...         121.7 MiB/s
(--) SIS(0):    Checked SSE memcpy()...         188.0 MiB/s
(--) SIS(0):    Checked MMX2 memcpy()...        179.9 MiB/s
(--) SIS(0): Using SSE method for aligned data transfers to video RAM
(--) SIS(0): Using MMX2 method for unaligned data transfers to video RAM
(==) SIS(0): Backing store disabled
(==) SIS(0): Silken mouse enabled
(**) SIS(0): DPMS enabled
(II) SIS(0): Using SiS300/315/330/340 series HW Xv
(II) SIS(0): X context handle = 0x1
(II) SIS(0): [drm] installed DRM signal handler
(II) SIS(0): [DRI] installation complete
(II) SIS(0): Direct rendering enabled
(II) SIS(0): Initialized SISCTRL extension version 0.1
(II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1

```
```

**kissg@kissg:~$ X -version**

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux kissg 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present

```
```

**kissg@kissg:~$ wine --version**
wine-0.9.33

```

I ran Wine with WINEDEBUG=+relay, the error message I get is:
```

main/renderbuffer.c:2041: _mesa_add_renderbuffer:  assertion "bufferName ==
BUFFER_DEPTH || bufferName == BUFFER_STENCIL ||
fb->Attachment[bufferName].Renderbuffer == ((void *)0)" failed

```

Any replies will be appreciated!

---

### Post by kissg1988 on 2007-08-21
glxinfo output:

```

**kissg@kissg:~$ glxinfo**
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Eric Anholt
OpenGL renderer string: Mesa DRI SiS 20060710 AGP 1x x86/MMX/SSE
OpenGL version string: 1.2 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_packed_pixels, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_OES_read_format, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x4a 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

glxgears output:
```

**kissg@kissg:~$ glxgears**
727 frames in 5.0 seconds = 145.260 FPS
755 frames in 5.0 seconds = 150.875 FPS
588 frames in 5.0 seconds = 117.142 FPS
757 frames in 5.0 seconds = 150.570 FPS

```

---

### Post by kissg1988 on 2007-08-21
Do you have any information about this problem? I really need some help!
I think, there's a bug in the sis dri driver. Is there a fix, maybe?

---

### Post by kissg1988 on 2007-08-21
Anyone with the same problem?

---

### Post by kissg1988 on 2007-08-22
Any ideas?

---

### Post by vyruss on 2008-05-15
Same problem here, SiS630 graphics.
This happens with every app that uses 3D, not only through wine.

Why don't you try reporting a bug on launchpad.net ?

---

