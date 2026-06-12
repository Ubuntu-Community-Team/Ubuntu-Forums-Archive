---
title: "No Direct rendering with ATI 9200 SE"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by DarkWizzard on 2006-06-18
Sorry that I had to make a new thread for this old problem but I 've tryed many things and can't seem to figure it out.
I have an ATI Radeon 9200 SE video card and after upgrading to Dapper I lost 3D acceleration.
I managed with hard work to get it working in Breezy.But can't remember how I dit it.
So everything seems fine in the /var/log/Xorg.0.log.

```

...
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		24 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
**(II) fglrx(0): Direct rendering enabled**
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 832 x 632
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): Interrupt handler installed at IRQ 177.
(==) RandR enabled
(II) Setting vga for screen 0.
...

```

But the output of glxinfo is: 
```

:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: No**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None


```

fglrxinfo says:
```

:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

fgl_glxgears gives me the folowing:
```

:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  33
  Current serial number in output stream:  33

```


dmesg |grep fglrx has no output.

And my Xorg.conf file can be found [here]("http://darkwizard.phoenix-hosting.org/xorg.conf")

I think that I managed to fix this problem in breezy by somehow forcing the kernel to load module drm.

:~$ sudo modprobe drm
FATAL: Error inserting drm (/lib/modules/2.6.15-23-386/kernel/drivers/char/drm/drm.ko): Cannot allocate memory

It can't seem to load it with fglrx tried adding it to /etc/modules but no luck.
only modules : fglrx, agpgart,intel_agp are loaded and it doesn't wan't to load drm.Maybe this is normal.
Maybe there are some symlink problems.Any help would be apretiated.
And sorry again for making a new thread.

---

### Post by yyagol on 2006-06-18
I have the same 9200 SE ...i gave up on it
the new ati drivers and the ubuntu drivers would not
work properly for this card. i whent thrugh every HOW-TO
and all forums and i manage to install it but had problems with
gamma that could not be fix ..mabye you can tell me how
you manage to fix this problem ?

---

### Post by Klemik on 2006-06-18
[QUOTE=yyagol]I have the same 9200 SE ...i gave up on it
the new ati drivers and the ubuntu drivers would not
work properly for this card. i whent thrugh every HOW-TO
and all forums and i manage to install it but had problems with
gamma that could not be fix ..mabye you can tell me how
you manage to fix this problem ?[/QUOTE]

Could you tell me how did you manage to install ?
I mean does  it work (3D Accel) for you ?
I have same video card and that problem:
[http://ubuntuforums.org/showthread.php?p=1153763#post1153763](http://ubuntuforums.org/showthread.php?p=1153763#post1153763)

---

### Post by DarkWizzard on 2006-06-19
It has to work.It worked in breezy.The Xorg.0.log says everything is ok maybe I have a problem with the libGL.so.1.2 . Maybe it's not the official ati.I'm not sure.

If you have it working then try fglrxcontrol to adjust the gamma.

I think it worked on the Kubuntu 6.06 Live cd.
And then there has to be a way to do it.The card isn't that old.

---

### Post by yyagol on 2006-06-19
[QUOTE=Klemik]Could you tell me how did you manage to install ?
I mean does  it work (3D Accel) for you ?
I have same video card and that problem:
[http://ubuntuforums.org/showthread.php?p=1153763#post1153763](http://ubuntuforums.org/showthread.php?p=1153763#post1153763)[/QUOTE]

i thing your problem is not the same your problem seems to be 
somthing to do with gcc and the kernel-headers 
[QUOTE=Klemik][Message] Kernel Module : Precompiled kernel module version mismatched.[/QUOTE]
try to install the 
headers for your kernel like this :
```
$sudo apt-get install linux-headers-$(uname -r)
```
in any case [QUOTE=Ivhassel]The **latest** ATI drivers don't work with **R280** chips. Install the previous ATI drivers. Howto is around somewhere.
Good luck :)[/QUOTE]
so i guess we stack with the old problem , mabey we need to upgrade this cards?#-o

---

### Post by DarkWizzard on 2006-06-19
xorg-driver-fglrx 
Installed version:7.0.0-8.25.18+2.6.15.11-2

> 
Video driver for ATI graphics accelerators
Video driver for the ATI Radeon and FireGL graphics accelerators.
This version of the ATI driver officially supports: * ATI Radeon 8500, 9000, 9100, ** 9200 **, 9250 (R2xx) * ATI Radeon 9500, 9550, 9600, 9700, 9800, X300, X400, X600 (R3xx) * ATI Radeon X700, X800 (R4xx) * ATI Mobility 9000, 9600, 9800 * ATI FireGL 8700, 8800, E1, E2, X1, X2, X3, Z1, T2, 5100, 7100, 7200 * ATI Mobility FireGL 9000, T2, T2e
This package provides 2D display drivers and hardware accelerated OpenGL.


It has to suport it.And in my case the driver works and loads.At least according to /var/log/Xorg.0.log I think it's a problem with some OpenGL packages.Does anyone have the Ati version of libGL.so.1.2 ?

---

### Post by yyagol on 2006-06-19
I know it should
just untile amonth ago i had XP dual-boot on my comp 
when i upgrade my driver for the XP version it worked beter
and i could play **F.E.A.R** witch i could'nt withe the original driver
so i guess it should work.
tel me did you also had the gamma problem ?

---

### Post by DarkWizzard on 2006-06-19
No everything worked fine before the update.

Now I'm changing strategy.I removed everything what is fglrx and changed back to the ati driver.It should suport my card.Acording to Xorg.0.log everything worked fine.It says direct rendering enabled.But glxinfo says that there is no direct rendering.

---

### Post by yyagol on 2006-06-19
dose dri loads ?
```
~$ grep DRI /var/log/Xorg.0.log
(II) Loading extension XFree86-DRI
(==) fglrx(0): NoDRI = NO
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): [DRI] installation complete

```

---

### Post by DarkWizzard on 2006-06-19
```

:~$ grep DRI /var/log/Xorg.0.log
(II) Loading extension XFree86-DRI
(II) RADEON(0): [dri] Found DRI library version 1.2.0 and kernel module version 1.24.0
(**) RADEON(0): DRI New memory map param
(**) RADEON(0): DRI Finishing init !
(II) RADEON(0): [DRI] installation complete
(WW) RADEON(0): DRI init changed memory map, adjusting ...

```
```

:~$ cat /var/log/Xorg.0.log |grep Direct
(II) RADEON(0): Direct rendering enabled

```
```

:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow

```

```

:~$ lsmod |grep drm
drm                    73236  2 radeon
agpgart                34888  2 drm,intel_agp

```
```

:~$ sudo modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.15-23-386/volatile/fglrx.ko): Operation not permitted

```

I think it would work if I could somehow force it to load drm and fglrx together 

But it doesn't want to do that.I tryed adding it to /etc/modules/ but it loads 
fglrx OR drm but I would need it to load both. Just can't understand whats the problem.

---

### Post by yyagol on 2006-06-19
how is the mtrr ? they had that problem too 
```
~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size= 512MB: write-back, count=1
reg01: base=0xe0000000 (3584MB), size= 128MB: write-combining, count=4
reg02: base=0xf0000000 (3840MB), size=  64MB: write-combining, count=1
```

---

### Post by DarkWizzard on 2006-06-19
```

~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size= 256MB: write-back, count=1
reg01: base=0xd8000000 (3456MB), size= 128MB: write-combining, count=1
reg02: base=0xd0000000 (3328MB), size= 128MB: write-combining, count=1

```

I'll try this:

[http://www.ubuntuforums.org/showthread.php?t=197471](http://www.ubuntuforums.org/showthread.php?t=197471)

---

### Post by yyagol on 2006-06-19
i wish i could play with the amchine like you
but it took me to long to build and i got no intetion of breaking it
i took another look and drm module is loaded in your system
while on mine its not !!!
i found [this  Discussion]("http://ubuntuforums.org/showthread.php?t=76116&page=92") mabye it can help out

---

### Post by DarkWizzard on 2006-06-20
Guys I got it working.

So here is what i have done.Our card (the Radeon 9200 SE ) is suported by the ati drivers that come with dapper.Why use fglrx?
I blacklisted the fglrx driver in /etc/default/linux-restricted-modules-common .
I added drm to /etc/modules.Set the driver in xorg.conf to ati and booted the kubuntu live cd, copyed the file /usr/lib/libGL.so.1.2 booted back to kubuntu.
Replaced the old libGL.so.1.2 with the one from the live cd and got Direct rendering:Yes in glxinfo.

Now fglrxinfo says:
```

:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20041207 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.4.1

```

```

:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: Yes**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20041207 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram,
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

And all my games work.And I don't have that annoying bug that fglrx freezes when returning from virtual terminal.

---

### Post by yyagol on 2006-06-20
Great news =D>  =D> 
dose the TV out work as well ?
and do you have any side efects like i did with the gamma ?


you encorage me to reinstall again ....this time from scratch.
i install Dapper server then slowly install all nessery to run x-server with fluxbox ( i dont like kubuntu )
now i will try to install as you did ...corss fingers

---

### Post by DarkWizzard on 2006-06-20
Haven't tryed the tvout.No side efects.The driver isn't the fastest but planet penguin racer, supertux, xmoto work really well. 

Good luck :)

---

### Post by yyagol on 2006-06-20
Ok i falow the how to on ATI's and found out this :
[QUOTE=ATI Proprietary Linux Driver]	Note: 	In order to use the fglrx internal AGP support, you have to make sure that the kernel agpgart support is not active, i.e. it is not compiled into the kernel and the kernel modules are not loaded. If the fglrx kernel module detects that the kernel agpgart support is active, it will automatically use that even if its internal AGP support is requested in order to avoid conflicts that can cause problems under some circumstances.
[/QUOTE]
while in my case :
```
~$ lsmod | grep agp
sis_agp                 9028  1 
agpgart                36784  2 drm,sis_agp
```
i will try to kiill it befor compiling the fglrx module
i guess the best way is to do it all without X runing
also found that in order for 3D we need **POSIX Shared Memory**
in my case :
```
~$ ls -l /dev/shm
total 0

```

---

### Post by Galban on 2006-06-20
New drivers can work with your 9200Se card, not out the box from repos neither Ati's isntaller, but  that's for sure, you could get it working. Chek in this forum for libGL.1.2.so. Here is the proof(in blue): 

rodolfo@amdasus:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON [COLOR="Blue"]9000[/COLOR] PRO DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-[COLOR="Blue"]8.25.18[/COLOR])

---

### Post by Nicksha on 2006-06-20
That's right. And also, tv-out does not work with ati driver, only with fglrx, so this solution would be the way to go.
[http://www.ubuntuforums.org/showthread.php?t=185033](http://www.ubuntuforums.org/showthread.php?t=185033)

About gamma problems: If it's the one where your monitor is too bright, but tv-out is normal, this is what is happening: the gamma issue only appears when you have tv connected while booting the computer. You should unplug it, reboot, but it has to be plugged back in before Ubuntu's login screen appears (the one where you type in your username and password). Then it will all be fine - fglrx detects that tv is connected, and it won't brighten your monitor.

---

### Post by DarkWizzard on 2006-06-20
Yeah it should work with fglrx. It worked in breezy ...

---

### Post by yyagol on 2006-06-20
[QUOTE=Nicksha]About gamma problems: If it's the one where your monitor is too bright, but tv-out is normal, this is what is happening: the gamma issue only appears when you have tv connected while booting the computer. You should unplug it, reboot, but it has to be plugged back in before Ubuntu's login screen appears (the one where you type in your username and password). Then it will all be fine - fglrx detects that tv is connected, and it won't brighten your monitor.[/QUOTE]
so I did install it complitly ....how did you find it
i would never think of doing that ,it make no sence  but thank you for that
when i get home from work i will try it .

---

### Post by Nicksha on 2006-06-20
Yea, I know... it makes no sense. When I first upgraded to Breezy the gamma problem was killing me. I don't remember which driver version introduced that, but for me, it was hours of "fun" until I gave up on it, and much later stumbled upon the workaround, while complaining to a friend about it not working. It was like an Easter egg on DVDs:) I guess ATI just finds hiding important driver features very entertaining.

---

### Post by yyagol on 2006-06-21
[QUOTE=Nicksha]I guess ATI just finds hiding important driver features very entertaining.[/QUOTE]
[SIZE="5"]So true !! 
I know my next card is not going to be an ATI i had enogh[/SIZE]

---

### Post by TetsuoTW on 2006-06-25
[QUOTE=DarkWizzard]Guys I got it working.

So here is what i have done.Our card (the Radeon 9200 SE ) is suported by the ati drivers that come with dapper.Why use fglrx?
I blacklisted the fglrx driver in /etc/default/linux-restricted-modules-common .
I added drm to /etc/modules.Set the driver in xorg.conf to ati and booted the kubuntu live cd, copyed the file /usr/lib/libGL.so.1.2 booted back to kubuntu.
Replaced the old libGL.so.1.2 with the one from the live cd and got Direct rendering:Yes in glxinfo.[/quote]
Sorry if I sound like a total noob, but can you explain how to do this a bit more simply? I have no idea what any of that up there means....

---

### Post by TetsuoTW on 2006-06-27
bumping for help/great justice

---

### Post by DarkWizzard on 2006-06-27
It got broken again. I can't understand what is causing this problem.I tryed replacing the file another time.But same error.


```

:~$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 5.0.3 r200 (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri//r200_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri//r200_dri.so failed (/usr/X11R6/lib/modules/dri//r200_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: r200_dri.so
libGL: XF86DRIGetClientDriverName: 5.0.3 r200 (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri//r200_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri//r200_dri.so failed (/usr/X11R6/lib/modules/dri//r200_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: r200_dri.so
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow

```

Does anyone have a normal, working libGL.so.1.2 file ? 
I'm pretty sure that the problem is in that file because : 
```

:~$ cat /var/log/Xorg.0.log |grep Direct
(II) RADEON(0): Direct rendering enabled

```

I'll never buy an ATI video card again ...  :mad:

---

### Post by TetsuoTW on 2006-06-28
Seriously, are you going to help me at all by explaining what you did a bit more easily, or am I just going to have to give up?

---

### Post by DarkWizzard on 2006-06-28
Look this is not the best method at all.It worked with simpler games like supertux, xmoto and other simple OpenGL apps but I got a catastrophic framerate while playing Warsow.But I'll tell you what I have done.

So I opened the /etc/default/linux-restricted-modules-common file and added 
```

DISABLED_MODULES="fglrx"

```

Changed the following in the file /etc/X11/xorg.conf : 
```

Section "Device"
        Identifier      "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
        Driver          **"ati" **
        BusID           "PCI:1:0:0"

``` instead of fglrx.

And changed the file /etc/modules/ and added the following lines:
```

agpgart
drm
radeon

```

And after that I booted from the Kubuntu 6.06 Live cd and replaced the file /usr/lib/libGL.so.1.2 from the libGL.so.1.2 file from the live cd.

If you don't have the Kubuntu live cd then you can find that file [here]("http://darkwizard.phoenix-hosting.org/libGL.so.1.2").
After downloading type:** sudo cp /[where you saved it]/libGL.so.1.2 /usr/lib/libGL.so.1.2**.

And reboot and it should work.Worked for me **once**.**It DOESN'T ANYMORE **.
But maybe it's worth a try.

---

### Post by whatever on 2006-06-28
[QUOTE=DarkWizzard]but I got a catastrophic framerate while playing Warsow.[/QUOTE]
disabling bloom in warsow should help a lot!

---

### Post by DarkWizzard on 2006-07-13
Ok guys.This time I got it working good.Fglrx works.And fglrxinfo shows the right thing.
Reed this : [http://www.ubuntuforums.org/showthread.php?t=197471](http://www.ubuntuforums.org/showthread.php?t=197471) .
It worked for me.
Except it wasn't a clean dapper install.I removed xorg-driver-fglrx and switched to ati in my xorg.conf.Downloaded the 8.25 version of the driver from ati.com and used the installer.After that i switched back to fglrx in xorg.conf and rebooted.In "LIBGL_DEBUG=verbose glxinfo" I got error messages that libGL didn't match the driver version.So I did like it said in the howto and downloaded the 8.24.8 version of the driver from ati.com.Extracted it and overwritten the file libGL.so.1.2 in /usr/bin and /usr/bin/fglrx . It got it working. Million thanks to Galban .

---

### Post by DarkWizzard on 2006-07-14
I explained more detailed on my site:
[http://www.darkwizzard.rulz.hu/](http://www.darkwizzard.rulz.hu/)
Articles 

Hope it helps.

---

