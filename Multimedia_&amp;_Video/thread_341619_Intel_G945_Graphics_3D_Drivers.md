---
title: "Intel G945 Graphics 3D Drivers"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by Volmarias on 2007-01-18
Hi, I have the terrible feeling that this isn't going to get any responses. ](*,) 

My new laptop has an Intel G945 Integrated graphics card. Despite Intel's great boasts of having fantastic linux support, I've found it impossible to actually find a binary to use for 3D Acceleration. (They said they had a Debian binary. They lied... ) I've been able to download the Mesa3D driver source, but unable to compile it (various errors, really don't have the patience at the moment to sit down and try and fix them).

In any event, I can't be the only person running Linux with an Intel card and the want for 3D acceleration. If anyone can suggest where to look for binaries, or at the least the next step to take, please Please PLEASE post!

Thanks! :KS

---

### Post by Fitzy_oz on 2007-01-18
> **Volmarias said:**
> Hi, I have the terrible feeling that this isn't going to get any responses. ](*,) 

My new laptop has an Intel G945 Integrated graphics card. Despite Intel's great boasts of having fantastic linux support, I've found it impossible to actually find a binary to use for 3D Acceleration. (They said they had a Debian binary. They lied... ) I've been able to download the Mesa3D driver source, but unable to compile it (various errors, really don't have the patience at the moment to sit down and try and fix them).

In any event, I can't be the only person running Linux with an Intel card and the want for 3D acceleration. If anyone can suggest where to look for binaries, or at the least the next step to take, please Please PLEASE post!

Thanks! :KS

Ubuntu should support your i945 out of the box intels drivers are open source, you shouldn't need to install or compile DRI or mesa3d, they're in the synaptic repos.  Jump to a terminal and type glxinfo and paste the output here for me.

---

### Post by Volmarias on 2007-01-18
Oh, I can do 3d, it's just astoundingly slow (especially compared to running on the windows partition!), which makes me think that software emulation is getting used.
```

volmarias@(my hostname here):~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x5b
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20050225
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays
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
0x5b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by Volmarias on 2007-01-18
Oh, and looking in synaptic, xserver-xorg-video-i810 is installed, but xserver-xorg-video-intel is not.

---

### Post by Fitzy_oz on 2007-01-18
> **Volmarias said:**
> Oh, and looking in synaptic, xserver-xorg-video-i810 is installed, but xserver-xorg-video-intel is not.

you could try the other driver - I used Suse 10.1 on my old IBM desktop which has an i815 init and it runs GLX and compiz unbeleivably well... And it only has 32mb of ram on it - I'll see if can find out what driver runs with Suse later today.  watch this space :)

---

### Post by Volmarias on 2007-01-18
Alright. How do I determine which driver to use? Is it in xorg.conf?

---

### Post by Fitzy_oz on 2007-01-18
> **Volmarias said:**
> Alright. How do I determine which driver to use? Is it in xorg.conf?

I belive it is in their yes.  If it says intel, it should automatically determine the best driver. I think the options are i815, i915 and i965.  Not sure though

---

### Post by imspecial on 2007-01-20
I am new to Ubuntu also and had this same problem. I have a Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller and I managed to get/compile the mesa3d driver from [http://intellinuxgraphics.org](http://intellinuxgraphics.org) using the following commands.

CVS is required for this so you need to do a (if you do not have it) ```
sudo apt-get install cvs
``` and then ran (this is directly from the download section on intellinuxgraphics.org) ```
cvs -d :pserver:anoncvs@anoncvs.freedesktop.org:/cvs/mesa checkout Mesa
```

I can now run Wolfenstein Enemy Territory at the same speed as that of windows

Also I found intellinuxgraphics.org directly from intel.com 's graphics drivers section so it is a legit site.

---

### Post by J.Vega on 2007-01-29
Maybe this Howto helps:
[http://www.ubuntuforums.org/showthread.php?t=326864](http://www.ubuntuforums.org/showthread.php?t=326864)

---

