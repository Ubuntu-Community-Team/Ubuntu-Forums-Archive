---
title: "Open source ATI driver EXTREMELY slow..."
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by Starlight on 2007-02-23
Hello :)

I have a Radeon 9550 video card. I've decided to switch from the fglrx driver to the open source ATI driver, so that AIGLX would work... and I have a problem. When I use this driver, OpenGL games are extremely slow (just a few FPS, and they worked very smoothly on fglrx). I've even noticed that some 2D stuff is also very slow, such as selecting an area on the desktop... it worked well before. Here's what I get when I use glxinfo:

```
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample,
    GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_gpu_program_parameters,
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

---

### Post by Stemp on 2007-02-23
> OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x TCL

AGP x1 ? in your section device add this line 

```
Option          "AGPMode"               "8"
```

Look at others options in my [xorg.conf]("http://ubuntufr.free.fr/upload/xorg.conf.radeon") for an ATI 9600.

---

### Post by Starlight on 2007-02-23
> **Stemp said:**
> AGP x1 ? in your section device add this line 

```
Option          "AGPMode"               "8"
```

Look at others options in my [xorg.conf]("http://ubuntufr.free.fr/upload/xorg.conf.radeon") for an ATI 9600.
Thanks! I'll try to do it, and then I'll tell you here if it worked :)

---

### Post by Starlight on 2007-02-23
When I set AGPMode to 8, then glxinfo started to say AGP 8x but everything was still as slow as it was before... I tried adding some of the other options from your xorg.conf file, but it didn't change anything, it's still slow... and the AGPSize option causes errors and disables direct rendering... here's the error from the log:

	error	RADEON(0): [agp] Could not bind

	error	RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.



edit: The most interesting thing is that AIGLX and Beryl seem to work quite well... :)

edit2: oops, no they don't... Beryl is much slower than on XGL...

---

### Post by Stemp on 2007-02-23
try setting the agp speed to 4 or 2 ;)

If it's still not working, you certainly have a problem with your agp settings.

---

### Post by Starlight on 2007-02-23
I tried it, and it didn't change anything... it displays everything correctly, but it's very slow! (by the way, another 3D game, Planet Penguin Racer, works well!)

There are no AGP errors in the logs, but there are some strange warnings... here they are:

	warning	RADEON(0): DRI init changed memory map, adjusting ...

	warning	RADEON(0):   MC_FB_LOCATION  was: 0xb7ffb000 is: 0xb7ffb000

	warning	RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xd3ffd000

(some other messages here)

	warning	RADEON(0): Option "DRI" is not used

(some more messages)

	warning	AIGLX: 3D driver claims to not support visual 0x23

	warning	AIGLX: 3D driver claims to not support visual 0x24

	warning	AIGLX: 3D driver claims to not support visual 0x25

	warning	AIGLX: 3D driver claims to not support visual 0x26

	warning	AIGLX: 3D driver claims to not support visual 0x27

	warning	AIGLX: 3D driver claims to not support visual 0x28

	warning	AIGLX: 3D driver claims to not support visual 0x29

	warning	AIGLX: 3D driver claims to not support visual 0x2a

	warning	AIGLX: 3D driver claims to not support visual 0x2b

	warning	AIGLX: 3D driver claims to not support visual 0x2c

	warning	AIGLX: 3D driver claims to not support visual 0x2d

	warning	AIGLX: 3D driver claims to not support visual 0x2e

	warning	AIGLX: 3D driver claims to not support visual 0x2f

	warning	AIGLX: 3D driver claims to not support visual 0x30

	warning	AIGLX: 3D driver claims to not support visual 0x31

	warning	AIGLX: 3D driver claims to not support visual 0x32

---

### Post by Stemp on 2007-02-23
> There are no AGP errors in the logs, but there are some strange warnings... here they are:

What logs ? 
Do you mean in **/var/log/Xorg.0.log** ? 
To look at the errors in the X log : **cat /var/log/Xorg.0.log | grep EE**

---

### Post by Starlight on 2007-02-23
I used the KDE log viewer... and when I run that command, it only shows a couple of "Cannot open device /dev/wacom" errors, but I think it's not related to my problems with the radeon driver...

---

### Post by Stemp on 2007-02-24
No you're right the wacom devices problem is a bug in ubuntu xorg configuration.

So look at the warnings : **cat /var/log/Xorg.0.log | grep WW**

---

### Post by Starlight on 2007-02-24
ok... here's what I got:

(WW) RADEON: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(WW) RADEON(0): config file hsync range 28-204kHz not within DDC hsync ranges.
(WW) RADEON(0): config file vrefresh range 43-60Hz not within DDC vrefresh ranges.
(WW) (1280x960,Generic Monitor) mode clock 148.5MHz exceeds DDC maximum 140MHz
(WW) (1280x1024,Generic Monitor) mode clock 157.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,Generic Monitor) mode clock 162MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,Generic Monitor) mode clock 175.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,Generic Monitor) mode clock 189MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,Generic Monitor) mode clock 202.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,Generic Monitor) mode clock 229.5MHz exceeds DDC maximum 140MHz
(WW) (1792x1344,Generic Monitor) mode clock 204.8MHz exceeds DDC maximum 140MHz
(WW) (1792x1344,Generic Monitor) mode clock 261MHz exceeds DDC maximum 140MHz
(WW) (1856x1392,Generic Monitor) mode clock 218.3MHz exceeds DDC maximum 140MHz
(WW) (1856x1392,Generic Monitor) mode clock 288MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,Generic Monitor) mode clock 234MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,Generic Monitor) mode clock 297MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,Generic Monitor) mode clock 151MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,Generic Monitor) mode clock 155.8MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,Generic Monitor) mode clock 184MHz exceeds DDC maximum 140MHz
(WW) (1680x1050,Generic Monitor) mode clock 147.14MHz exceeds DDC maximum 140MHz
(WW) (1920x1200,Generic Monitor) mode clock 193.16MHz exceeds DDC maximum 140MHz
(WW) (1920x1200,Generic Monitor) mode clock 230MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,Generic Monitor) mode clock 341.35MHz exceeds DDC maximum 140MHz
(WW) (2048x1536,Generic Monitor) mode clock 266.95MHz exceeds DDC maximum 140MHz
(WW) (2048x1536,Generic Monitor) mode clock 340.48MHz exceeds DDC maximum 140MHz
(WW) (2048x1536,Generic Monitor) mode clock 388.04MHz exceeds DDC maximum 140MHz
(WW) RADEON(0): Enabling DRM support
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xb7ffb000 is: 0xb7ffb000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xd07fd000
(WW) RADEON(0): Option "DRI" is not used

---

### Post by koanhead on 2007-02-24
I have a similar problem. xorg.0.log says:

<snip>
II) RADEON(0): [drm] added 1 reserved context for kernel
(WW) RADEON(0): [agp] AGP not available
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module
is loaded before the radeon kernel module.
(**) RADEON(0): RADEONDRICloseScreen
</snip>

     I am using the open-source ati driver (radeon subsystem) for a Radeon 8500.

     I'm not sure exactly how one goes about ensuring that agpgart is loaded before the radeon module, or why it isn't already. Surely the radeon module isn't loaded until X starts?

---

### Post by koanhead on 2007-02-24
It turned out that I had blacklisted the agpgart module (in /etc/modules.d/blacklist) earlier when I was trying to get a pci-based geforce2 card to work in this machine. After removing the blacklist entry and rebooting I have 3d acceleration working fine- with open source drivers! RESULT!
     I'm as giddy as a school-girl, but I'm afraid my little story does not help with your problem. I'm still working on it.

---

### Post by Starlight on 2007-02-25
The weird thing for me is that direct rendering supposedly works.... but it's extremely slow. If I actually disable direct rendering, then 3D games work a little faster, but still very slow.

When I first installed Ubuntu, the open source ATI driver worked very fast, but the textures in some programs were totally messed up, so I decided to switch to the fglrx driver and everything worked well. And now when I switched back to the open source driver, all textures are displayed with no problems, but everything's very slow...

---

### Post by Stemp on 2007-02-25
Are you sure you deinstall all the fglrx stuff ?

---

### Post by Starlight on 2007-02-25
Yes, I think... I uninstalled the fglrx and fglrx-control packages.

---

### Post by Stemp on 2007-02-25
You should reinstall **xserver-xorg-video-ati** perhaps.

---

### Post by Starlight on 2007-02-28
I remember that I reinstalled it too, after uninstalling fglrx...

---

