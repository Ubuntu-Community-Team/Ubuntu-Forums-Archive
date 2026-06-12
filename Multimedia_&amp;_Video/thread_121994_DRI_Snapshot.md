---
title: "DRI Snapshot"
date: 2006-01-26
forum: Multimedia &amp; Video
---

### Post by CitizenKane on 2006-01-26
I was wondering how to install the DRI snapshots found at [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/).  My graphics chipset it the Intel 915gm and I have had no success getting 3d acceleration to work.  But, another has and it requires a snapshot installation.  I looked around and I really couldn't find a guide on how to do this.  Any help is appreciated.

---

### Post by CitizenKane on 2006-01-27
**ANY** help would be greatly appreciated.

---

### Post by knubbe on 2006-01-29
[QUOTE=CitizenKane]I was wondering how to install the DRI snapshots found at [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/).  My graphics chipset it the Intel 915gm and I have had no success getting 3d acceleration to work.  But, another has and it requires a snapshot installation.  I looked around and I really couldn't find a guide on how to do this.  Any help is appreciated.[/QUOTE]

I also have the Intel 915Gm. I followed the instructions in this thread but used the intel-snapshots, and it works fine:
[http://www.ubuntuforums.org/showthread.php?t=75393](http://www.ubuntuforums.org/showthread.php?t=75393)

[I]Edit:
Maybe i should add I use the following snapshots: **"i915-20060107-linux.i386"** and **"common-20060107-linux.i386"**. [/I]

---

### Post by CitizenKane on 2006-01-29
> Maybe i should add I use the following snapshots: "i915-20060107-linux.i386" and "common-20060107-linux.i386".

Those seem to have been removed from [http://dri.freedesktop.org/snapshots](http://dri.freedesktop.org/snapshots).
I have the common one along with the i810 driver.  I tried the newest i915 snapshot (along with common) and since that the driver has simply failed to initialize.  I thought this might be an xorg.conf problem so I made the following change.

```
driver "i915"
```
Which just ended crashing X and so i changed it back

I also tried the 20060107 driver with the i810 and that has changed nothing.
If I simply need to use the i915 20060107 drivers to fix things, then it would be great if someone could post a link or possibly upload it to yousendit.com or something because I can't find them anywhere.  Or maybe I destroyed it all and need to fix it.  My glxinfo is below.

```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
```

It is important to notice the OpenGL Render String.

Thanks for the help.

---

### Post by az on 2006-01-30
[QUOTE=CitizenKane]I was wondering how to install the DRI snapshots found at [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/).  My graphics chipset it the Intel 915gm and I have had no success getting 3d acceleration to work.  But, another has and it requires a snapshot installation.  I looked around and I really couldn't find a guide on how to do this.  Any help is appreciated.[/QUOTE]

Install the linux-headers package that matches your running kernel (type uname -r).  Also install build-essential and gcc-3.4.

Extract the shapshots (tar xvzf) and enter the directory (cd dripkg) and run the install script.

---

### Post by CitizenKane on 2006-01-30
> Install the linux-headers package that matches your running kernel (type uname -r). Also install build-essential and gcc-3.4.

Extract the shapshots (tar xvzf) and enter the directory (cd dripkg) and run the install script.

I had already done that, and i have the linux headers package, in my case 2.6.12-10-686.  After having done that I get this before Glxinfo spits stuff out.

```
ERROR!  sizeof(I830DRIRec) does not match passed size from device driver
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
```

---

### Post by darth_mall on 2006-01-30
I too am having this problem. I never had any problems getting DRI up and running on this laptop with Gentoo, so it must be possible. If anyone has any suggestions, they would be much appreciated.

---

### Post by Burkey on 2006-02-16
Exact same problem here, am looking into maybe compiling a new kernel.

Also to note that from my Xorg log file I have..

```

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

```

However, further down it says
```

(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
(==) RandR enabled

```

Which seems a little bit odd!  Also, I used snapshot 20060206

---

### Post by tthomas48 on 2006-07-20
This link:

[http://lists.alioth.debian.org/pipermail/pkg-mesa-devel/2006-May/000213.html](http://lists.alioth.debian.org/pipermail/pkg-mesa-devel/2006-May/000213.html)

seems to indicate the issue is in mesa. Has anyone tested this out?

---

### Post by tthomas48 on 2006-07-20
Hmm, so I decided to try it out, and it works.

You'll need to download the following packages:

libgl1-mesa-dev_6.5.0.cvs.20060524-1_i386.deb
mesa-common-dev_6.5.0.cvs.20060524-1_all.deb
libgl1-mesa-glx_6.5.0.cvs.20060524-1_i386.deb
libgl1-mesa-dri_6.5.0.cvs.20060524-1_i386.deb

They're pretty easy to search for on google using something like this:

libgl1-mesa-dri site:[http://packages.debian.org/experimental/](http://packages.debian.org/experimental/)

I installed the 4 packages and immediately my glxgears started working properly.

---

