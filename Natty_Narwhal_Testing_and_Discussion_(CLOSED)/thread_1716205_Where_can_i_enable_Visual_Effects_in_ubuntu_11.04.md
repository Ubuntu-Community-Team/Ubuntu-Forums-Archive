---
title: "Where can i enable Visual Effects in ubuntu 11.04"
date: 2011-03-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by reptilezone2002 on 2011-03-28
Where can i enable Visual Effects in ubuntu 11.04 theres no visual effect tab on appearance window or change background window

how can i change visual effects to extra

---

### Post by overdrank on 2011-03-28
Moved to Natty Narwhal Testing and Discussion :)

---

### Post by lucazade on 2011-03-28
> **reptilezone2002 said:**
> Where can i enable Visual Effects in ubuntu 11.04 theres no visual effect tab on appearance window or change background window

how can i change visual effects to extra  


You have to logout and select another session with effects enabled from bottom panel of GDM login page.
That tab is no more present in natty.

If you are using unity2d, as it seems, you can start compiz from command line:
compiz --replace

---

### Post by coffeecat on 2011-03-28
EDIT: posted in error - apologies.

---

### Post by rbrick49 on 2011-03-28
ron@ron:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (opengl) - Fatal: Software rendering detected
compiz (opengl) - Error: initScreen failed
compiz (core) - Error: Couldn't activate plugin 'opengl'
Initializing decor options...done
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'cube' failed
compiz (core) - Error: Couldn't activate plugin 'cube'
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'unitymtgrabhandles' failed
compiz (core) - Error: Couldn't activate plugin 'unitymtgrabhandles'
Starting unity-window-decorator
extents are 1 1 23 4 129
extents are 1 1 23 4 129

(unity-window-decorator:2597): Gdk-CRITICAL **: IA__gdk_drawable_set_colormap: assertion `cmap == NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed

heres what I get I am running an ati 6950 graphics card and I am starting to get really angry because I know nvidia will run 3d on this system

---

### Post by lucazade on 2011-03-28
> **rbrick49 said:**
> ron@ron:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (opengl) - Fatal: Software rendering detected
compiz (opengl) - Error: initScreen failed
compiz (core) - Error: Couldn't activate plugin 'opengl'
Initializing decor options...done
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'cube' failed
compiz (core) - Error: Couldn't activate plugin 'cube'
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'unitymtgrabhandles' failed
compiz (core) - Error: Couldn't activate plugin 'unitymtgrabhandles'
Starting unity-window-decorator
extents are 1 1 23 4 129
extents are 1 1 23 4 129

(unity-window-decorator:2597): Gdk-CRITICAL **: IA__gdk_drawable_set_colormap: assertion `cmap == NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed

heres what I get

it seems your graphic card is not working well:
"compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing"

post the output of 
lspci -v | grep VGA
and
glxinfo

---

### Post by rbrick49 on 2011-03-28
here you go
ron@ron:~$ lspci -v | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Cayman PRO [AMD Radeon 6900 Series] (prog-if 00 [VGA controller])

---

### Post by lucazade on 2011-03-28
ok.. post also the output of "glxinfo"

you should see something like this if texture_from_pixmap extension is supported:
```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, [COLOR="Red"]GLX_EXT_texture_from_pixmap[/COLOR],
```

---

### Post by rbrick49 on 2011-03-28
this is going to take up 3 pages
```
ron@ron:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_INTEL_swap_event
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.10.1
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_copy_buffer, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_map_buffer_range, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_provoking_vertex, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow_ambient, 
    GL_ARB_shadow, GL_ARB_sync, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_depth_bounds_test, GL_EXT_draw_buffers2, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_shader_objects, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture3D, GL_EXT_texture_array, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_EXT_vertex_array, GL_OES_read_format, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_object_purgeable, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_resize_buffers, GL_MESA_texture_array, 
    GL_MESA_window_pos, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_point_sprite, GL_NV_texgen_reflection, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGI_texture_color_table, GL_SUN_multi_draw_arrays
```

64 GLX Visuals
```
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c3 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c6 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0c7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0c8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0c9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0ca 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0cb 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0cc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0cd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ce 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0cf 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0d7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0d8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0d9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0da 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0db 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0dc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0dd 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0de 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0df 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0e5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0e6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0e7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0e8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ea 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0eb 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ec 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ed 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ee 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ef 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f0 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f1 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0f5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0f6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0f7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0f8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0f9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0fa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0fb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0fc 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0fd 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0fe 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ff 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x041 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
```

128 GLXFBConfigs:
```
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x042  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x043  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x044  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x045  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x046  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x047  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x048  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x049  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x04a  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x04b  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x04c  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x04d  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x04e  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x04f  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x050  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x051  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x052  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x053  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x054  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x055  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x056  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x057  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x058  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x059  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x05a  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x05b  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x05c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x05d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x05e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x05f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x060  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x062 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x063 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x064 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x065 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x06a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x06c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x06d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x06e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x070 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x071 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x072 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x073 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x074 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x076 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x078 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x079 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x07a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x07b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x07c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x07d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x07e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x080 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x081 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x082  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x083  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x084  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x085  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x086  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x087  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x088  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x089  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x08a  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x08b  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x08c  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x08d  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x08e  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x08f  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x090  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x091  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x092  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x093  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x094  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x095  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x096  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x097  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x098  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x099  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x09a  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x09b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x09c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x09d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x09e  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x09f  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x0a0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x0a1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x0a2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0a7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0aa 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ab 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ac 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ad 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ae 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0af 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b3 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0b4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0b6 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0b7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0b8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0b9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0ba 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0bb 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0bc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0bd 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0be 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0bf 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0c0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
```

---

### Post by lucazade on 2011-03-28
texture from pixmap is supported but unfortunately you are using a software emulation of Opengl

```
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.10.1
OpenGL shading language version string: 1.20
OpenGL extensions:
```

post also this two files (Use the CODE tags when you post  output)

/var/log/Xorg.0.log
and
/etc/X11/xorg.conf

---

### Post by rbrick49 on 2011-03-28
what do you mean by code tags lucazade

---

### Post by lucazade on 2011-03-28
> **rbrick49 said:**
> what do you mean by code tags lucazade

look at the screenshot ;)

use that button to embed code, this way won't take pages!

---

### Post by rbrick49 on 2011-03-28
here you go
```
[    14.031] 
X.Org X Server 1.10.0
Release Date: 2011-2-25
[    14.031] X Protocol Version 11, Revision 0
[    14.031] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    14.031] Current Operating System: Linux ron 2.6.38-7-generic #39-Ubuntu SMP Fri Mar 25 21:24:57 UTC 2011 x86_64
[    14.031] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-7-generic root=UUID=2234dc2a-8077-4be5-b12f-b10675cf3680 ro quiet splash vt.handoff=7
[    14.031] Build Date: 25 March 2011  01:46:34AM
[    14.031] xorg-server 2:1.10.0-0ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    14.031] Current version of pixman: 0.20.2
[    14.031] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    14.031] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.032] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 28 18:35:40 2011
[    14.085] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.085] (==) No Layout section.  Using the first Screen section.
[    14.085] (==) No screen section available. Using defaults.
[    14.085] (**) |-->Screen "Default Screen Section" (0)
[    14.085] (**) |   |-->Monitor "<default monitor>"
[    14.086] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    14.086] (==) Automatically adding devices
[    14.086] (==) Automatically enabling devices
[    14.086] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.086] 	Entry deleted from font path.
[    14.086] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.086] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.086] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.086] (II) Loader magic: 0x7e0280
[    14.086] (II) Module ABI versions:
[    14.086] 	X.Org ANSI C Emulation: 0.4
[    14.086] 	X.Org Video Driver: 10.0
[    14.086] 	X.Org XInput driver : 12.3
[    14.086] 	X.Org Server Extension : 5.0
[    14.087] (--) PCI:*(0:1:0:0) 1002:6719:1043:03ba rev 0, Mem @ 0xd0000000/268435456, 0xfbee0000/131072, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    14.087] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.087] (II) LoadModule: "extmod"
[    14.147] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.147] (II) Module extmod: vendor="X.Org Foundation"
[    14.147] 	compiled for 1.10.0, module version = 1.0.0
[    14.147] 	Module class: X.Org Server Extension
[    14.147] 	ABI class: X.Org Server Extension, version 5.0
[    14.147] (II) Loading extension MIT-SCREEN-SAVER
[    14.147] (II) Loading extension XFree86-VidModeExtension
[    14.147] (II) Loading extension XFree86-DGA
[    14.147] (II) Loading extension DPMS
[    14.147] (II) Loading extension XVideo
[    14.147] (II) Loading extension XVideo-MotionCompensation
[    14.147] (II) Loading extension X-Resource
[    14.147] (II) LoadModule: "dbe"
[    14.147] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.147] (II) Module dbe: vendor="X.Org Foundation"
[    14.147] 	compiled for 1.10.0, module version = 1.0.0
[    14.147] 	Module class: X.Org Server Extension
[    14.147] 	ABI class: X.Org Server Extension, version 5.0
[    14.147] (II) Loading extension DOUBLE-BUFFER
[    14.147] (II) LoadModule: "glx"
[    14.147] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.148] (II) Module glx: vendor="X.Org Foundation"
[    14.148] 	compiled for 1.10.0, module version = 1.0.0
[    14.148] 	ABI class: X.Org Server Extension, version 5.0
[    14.148] (==) AIGLX enabled
[    14.148] (II) Loading extension GLX
[    14.148] (II) LoadModule: "record"
[    14.148] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.148] (II) Module record: vendor="X.Org Foundation"
[    14.148] 	compiled for 1.10.0, module version = 1.13.0
[    14.148] 	Module class: X.Org Server Extension
[    14.148] 	ABI class: X.Org Server Extension, version 5.0
[    14.148] (II) Loading extension RECORD
[    14.148] (II) LoadModule: "dri"
[    14.148] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.148] (II) Module dri: vendor="X.Org Foundation"
[    14.148] 	compiled for 1.10.0, module version = 1.0.0
[    14.148] 	ABI class: X.Org Server Extension, version 5.0
[    14.148] (II) Loading extension XFree86-DRI
[    14.148] (II) LoadModule: "dri2"
[    14.149] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.149] (II) Module dri2: vendor="X.Org Foundation"
[    14.149] 	compiled for 1.10.0, module version = 1.2.0
[    14.149] 	ABI class: X.Org Server Extension, version 5.0
[    14.149] (II) Loading extension DRI2
[    14.149] (==) Matched fglrx as autoconfigured driver 0
[    14.149] (==) Matched ati as autoconfigured driver 1
[    14.149] (==) Matched vesa as autoconfigured driver 2
[    14.149] (==) Matched fbdev as autoconfigured driver 3
[    14.149] (==) Assigned the driver to the xf86ConfigLayout
[    14.149] (II) LoadModule: "fglrx"
[    14.149] (WW) Warning, couldn't open module fglrx
[    14.149] (II) UnloadModule: "fglrx"
[    14.149] (II) Unloading fglrx
[    14.149] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    14.149] (II) LoadModule: "ati"
[    14.150] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    14.150] (II) Module ati: vendor="X.Org Foundation"
[    14.150] 	compiled for 1.10.0, module version = 6.14.0
[    14.150] 	Module class: X.Org Video Driver
[    14.150] 	ABI class: X.Org Video Driver, version 10.0
[    14.150] (II) LoadModule: "radeon"
[    14.150] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    14.150] (II) Module radeon: vendor="X.Org Foundation"
[    14.150] 	compiled for 1.10.0, module version = 6.14.0
[    14.150] 	Module class: X.Org Video Driver
[    14.150] 	ABI class: X.Org Video Driver, version 10.0
[    14.151] (II) LoadModule: "vesa"
[    14.151] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.151] (II) Module vesa: vendor="X.Org Foundation"
[    14.151] 	compiled for 1.10.0, module version = 2.3.0
[    14.151] 	Module class: X.Org Video Driver
[    14.151] 	ABI class: X.Org Video Driver, version 10.0
[    14.151] (II) LoadModule: "fbdev"
[    14.151] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.151] (II) Module fbdev: vendor="X.Org Foundation"
[    14.151] 	compiled for 1.10.0, module version = 0.4.2
[    14.151] 	ABI class: X.Org Video Driver, version 10.0
[    14.151] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS,
	Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS
[    14.158] (II) VESA: driver for VESA chipsets: vesa
[    14.158] (II) FBDEV: driver for framebuffer: fbdev
[    14.158] (++) using VT number 7

[    14.159] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.159] (WW) Falling back to old probe method for fbdev
[    14.159] (II) Loading sub module "fbdevhw"
[    14.159] (II) LoadModule: "fbdevhw"
[    14.159] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.159] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.159] 	compiled for 1.10.0, module version = 0.0.2
[    14.159] 	ABI class: X.Org Video Driver, version 10.0
[    14.159] (II) Loading sub module "vbe"
[    14.159] (II) LoadModule: "vbe"
[    14.159] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    14.159] (II) Module vbe: vendor="X.Org Foundation"
[    14.159] 	compiled for 1.10.0, module version = 1.1.0
[    14.159] 	ABI class: X.Org Video Driver, version 10.0
[    14.160] (II) Loading sub module "int10"
[    14.160] (II) LoadModule: "int10"
[    14.160] (II) Loading /usr/lib/xorg/modules/libint10.so
[    14.160] (II) Module int10: vendor="X.Org Foundation"
[    14.160] 	compiled for 1.10.0, module version = 1.0.0
[    14.160] 	ABI class: X.Org Video Driver, version 10.0
[    14.160] (II) VESA(0): initializing int10
[    14.164] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    14.165] (II) VESA(0): VESA BIOS detected
[    14.165] (II) VESA(0): VESA VBE Version 3.0
[    14.165] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    14.165] (II) VESA(0): VESA VBE OEM: AMD ATOMBIOS
[    14.165] (II) VESA(0): VESA VBE OEM Software Rev: 13.8
[    14.165] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    14.165] (II) VESA(0): VESA VBE OEM Product: CAYMAN
[    14.165] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    14.246] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    14.246] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    14.246] (==) VESA(0): RGB weight 888
[    14.246] (==) VESA(0): Default visual is TrueColor
[    14.246] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.246] (II) Loading sub module "ddc"
[    14.246] (II) LoadModule: "ddc"
[    14.246] (II) Module "ddc" already built-in
[    14.246] (II) VESA(0): VESA VBE DDC supported
[    14.246] (II) VESA(0): VESA VBE DDC Level 2
[    14.246] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    14.510] (II) VESA(0): VESA VBE DDC read successfully
[    14.510] (II) VESA(0): Manufacturer: HWP  Model: 2822  Serial#: 16843009
[    14.510] (II) VESA(0): Year: 2009  Week: 35
[    14.510] (II) VESA(0): EDID Version: 1.3
[    14.510] (II) VESA(0): Digital Display Input
[    14.510] (II) VESA(0): Max Image Size [cm]: horiz.: 51  vert.: 29
[    14.510] (II) VESA(0): Gamma: 2.20
[    14.510] (II) VESA(0): DPMS capabilities: StandBy Suspend Off
[    14.510] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.510] (II) VESA(0): Default color space is primary color space
[    14.510] (II) VESA(0): First detailed timing is preferred mode
[    14.510] (II) VESA(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    14.510] (II) VESA(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    14.510] (II) VESA(0): Supported established timings:
[    14.510] (II) VESA(0): 720x400@70Hz
[    14.510] (II) VESA(0): 640x480@60Hz
[    14.510] (II) VESA(0): 800x600@60Hz
[    14.510] (II) VESA(0): 1024x768@60Hz
[    14.510] (II) VESA(0): Manufacturer's mask: 0
[    14.510] (II) VESA(0): Supported standard timings:
[    14.510] (II) VESA(0): #0: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    14.510] (II) VESA(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    14.510] (II) VESA(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    14.510] (II) VESA(0): #3: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    14.510] (II) VESA(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    14.510] (II) VESA(0): #5: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    14.510] (II) VESA(0): Supported detailed timing:
[    14.510] (II) VESA(0): clock: 148.5 MHz   Image Size:  510 x 287 mm
[    14.510] (II) VESA(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    14.510] (II) VESA(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    14.510] (II) VESA(0): Ranges: V min: 48 V max: 76 Hz, H min: 24 H max: 94 kHz, PixClock max 175 MHz
[    14.510] (II) VESA(0): Monitor name: HP 2309
[    14.510] (II) VESA(0): Serial No: 3CQ9350TM3
[    14.510] (II) VESA(0): EDID (in hex):
[    14.510] (II) VESA(0): 	00ffffffffffff0022f0222801010101
[    14.510] (II) VESA(0): 	2313010380331d78eeee95a3544c9926
[    14.510] (II) VESA(0): 	0f5054a10800814081809500a940b300
[    14.510] (II) VESA(0): 	d1c001010101023a801871382d40582c
[    14.511] (II) VESA(0): 	4500fe1f1100001e000000fd00304c18
[    14.511] (II) VESA(0): 	5e11000a202020202020000000fc0048
[    14.511] (II) VESA(0): 	5020323330390a2020202020000000ff
[    14.511] (II) VESA(0): 	0033435139333530544d330a20200023
[    14.511] (II) VESA(0): EDID vendor "HWP", prod id 10274
[    14.511] (II) VESA(0): Using EDID range info for horizontal sync
[    14.511] (II) VESA(0): Using EDID range info for vertical refresh
[    14.511] (II) VESA(0): Printing DDC gathered Modelines:
[    14.511] (II) VESA(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    14.511] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.511] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.511] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    14.511] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.511] (II) VESA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    14.511] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.511] (II) VESA(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    14.511] (II) VESA(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    14.511] (II) VESA(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    14.511] (II) VESA(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    14.511] (II) VESA(0): Searching for matching VESA mode(s):
[    14.512] Mode: 100 (640x400)
[    14.512] 	ModeAttributes: 0xbb
[    14.512] 	WinAAttributes: 0x7
[    14.512] 	WinBAttributes: 0x0
[    14.512] 	WinGranularity: 64
[    14.512] 	WinSize: 64
[    14.512] 	WinASegment: 0xa000
[    14.512] 	WinBSegment: 0x0
[    14.512] 	WinFuncPtr: 0xc00051ab
[    14.512] 	BytesPerScanline: 640
[    14.512] 	XResolution: 640
[    14.512] 	YResolution: 400
[    14.512] 	XCharSize: 8
[    14.512] 	YCharSize: 16
[    14.512] 	NumberOfPlanes: 1
[    14.512] 	BitsPerPixel: 8
[    14.512] 	NumberOfBanks: 1
[    14.512] 	MemoryModel: 4
[    14.512] 	BankSize: 0
[    14.512] 	NumberOfImages: 63
[    14.512] 	RedMaskSize: 0
[    14.512] 	RedFieldPosition: 0
[    14.512] 	GreenMaskSize: 0
[    14.512] 	GreenFieldPosition: 0
[    14.512] 	BlueMaskSize: 0
[    14.512] 	BlueFieldPosition: 0
[    14.512] 	RsvdMaskSize: 0
[    14.512] 	RsvdFieldPosition: 0
[    14.512] 	DirectColorModeInfo: 0
[    14.512] 	PhysBasePtr: 0xd0000000
[    14.512] 	LinBytesPerScanLine: 640
[    14.512] 	BnkNumberOfImagePages: 63
[    14.512] 	LinNumberOfImagePages: 63
[    14.512] 	LinRedMaskSize: 0
[    14.512] 	LinRedFieldPosition: 0
[    14.512] 	LinGreenMaskSize: 0
[    14.512] 	LinGreenFieldPosition: 0
[    14.512] 	LinBlueMaskSize: 0
[    14.512] 	LinBlueFieldPosition: 0
[    14.512] 	LinRsvdMaskSize: 0
[    14.512] 	LinRsvdFieldPosition: 0
[    14.512] 	MaxPixelClock: 400000000
[    14.513] Mode: 101 (640x480)
[    14.513] 	ModeAttributes: 0xbb
[    14.513] 	WinAAttributes: 0x7
[    14.513] 	WinBAttributes: 0x0
[    14.513] 	WinGranularity: 64
[    14.513] 	WinSize: 64
[    14.513] 	WinASegment: 0xa000
[    14.513] 	WinBSegment: 0x0
[    14.513] 	WinFuncPtr: 0xc00051ab
[    14.513] 	BytesPerScanline: 640
[    14.513] 	XResolution: 640
[    14.513] 	YResolution: 480
[    14.513] 	XCharSize: 8
[    14.513] 	YCharSize: 16
[    14.513] 	NumberOfPlanes: 1
[    14.513] 	BitsPerPixel: 8
[    14.513] 	NumberOfBanks: 1
[    14.513] 	MemoryModel: 4
[    14.513] 	BankSize: 0
[    14.513] 	NumberOfImages: 50
[    14.513] 	RedMaskSize: 0
[    14.513] 	RedFieldPosition: 0
[    14.513] 	GreenMaskSize: 0
[    14.513] 	GreenFieldPosition: 0
[    14.513] 	BlueMaskSize: 0
[    14.513] 	BlueFieldPosition: 0
[    14.513] 	RsvdMaskSize: 0
[    14.513] 	RsvdFieldPosition: 0
[    14.513] 	DirectColorModeInfo: 0
[    14.513] 	PhysBasePtr: 0xd0000000
[    14.513] 	LinBytesPerScanLine: 640
[    14.513] 	BnkNumberOfImagePages: 50
[    14.513] 	LinNumberOfImagePages: 50
[    14.513] 	LinRedMaskSize: 0
[    14.513] 	LinRedFieldPosition: 0
[    14.513] 	LinGreenMaskSize: 0
[    14.513] 	LinGreenFieldPosition: 0
[    14.513] 	LinBlueMaskSize: 0
[    14.513] 	LinBlueFieldPosition: 0
[    14.513] 	LinRsvdMaskSize: 0
[    14.513] 	LinRsvdFieldPosition: 0
[    14.513] 	MaxPixelClock: 400000000
[    14.514] Mode: 103 (800x600)
[    14.514] 	ModeAttributes: 0xbb
[    14.514] 	WinAAttributes: 0x7
[    14.514] 	WinBAttributes: 0x0
[    14.514] 	WinGranularity: 64
[    14.514] 	WinSize: 64
[    14.514] 	WinASegment: 0xa000
[    14.514] 	WinBSegment: 0x0
[    14.514] 	WinFuncPtr: 0xc00051ab
[    14.514] 	BytesPerScanline: 832
[    14.514] 	XResolution: 800
[    14.514] 	YResolution: 600
[    14.514] 	XCharSize: 8
[    14.514] 	YCharSize: 14
[    14.514] 	NumberOfPlanes: 1
[    14.514] 	BitsPerPixel: 8
[    14.514] 	NumberOfBanks: 1
[    14.514] 	MemoryModel: 4
[    14.514] 	BankSize: 0
[    14.514] 	NumberOfImages: 31
[    14.514] 	RedMaskSize: 0
[    14.514] 	RedFieldPosition: 0
[    14.514] 	GreenMaskSize: 0
[    14.514] 	GreenFieldPosition: 0
[    14.514] 	BlueMaskSize: 0
[    14.514] 	BlueFieldPosition: 0
[    14.514] 	RsvdMaskSize: 0
[    14.514] 	RsvdFieldPosition: 0
[    14.514] 	DirectColorModeInfo: 0
[    14.514] 	PhysBasePtr: 0xd0000000
[    14.514] 	LinBytesPerScanLine: 832
[    14.515] 	BnkNumberOfImagePages: 31
[    14.515] 	LinNumberOfImagePages: 31
[    14.515] 	LinRedMaskSize: 0
[    14.515] 	LinRedFieldPosition: 0
[    14.515] 	LinGreenMaskSize: 0
[    14.515] 	LinGreenFieldPosition: 0
[    14.515] 	LinBlueMaskSize: 0
[    14.515] 	LinBlueFieldPosition: 0
[    14.515] 	LinRsvdMaskSize: 0
[    14.515] 	LinRsvdFieldPosition: 0
[    14.515] 	MaxPixelClock: 400000000
[    14.516] Mode: 105 (1024x768)
[    14.516] 	ModeAttributes: 0xbb
[    14.516] 	WinAAttributes: 0x7
[    14.516] 	WinBAttributes: 0x0
[    14.516] 	WinGranularity: 64
[    14.516] 	WinSize: 64
[    14.516] 	WinASegment: 0xa000
[    14.516] 	WinBSegment: 0x0
[    14.516] 	WinFuncPtr: 0xc00051ab
[    14.516] 	BytesPerScanline: 1024
[    14.516] 	XResolution: 1024
[    14.516] 	YResolution: 768
[    14.516] 	XCharSize: 8
[    14.516] 	YCharSize: 16
[    14.516] 	NumberOfPlanes: 1
[    14.516] 	BitsPerPixel: 8
[    14.516] 	NumberOfBanks: 1
[    14.516] 	MemoryModel: 4
[    14.516] 	BankSize: 0
[    14.516] 	NumberOfImages: 18
[    14.516] 	RedMaskSize: 0
[    14.516] 	RedFieldPosition: 0
[    14.516] 	GreenMaskSize: 0
[    14.516] 	GreenFieldPosition: 0
[    14.516] 	BlueMaskSize: 0
[    14.516] 	BlueFieldPosition: 0
[    14.516] 	RsvdMaskSize: 0
[    14.516] 	RsvdFieldPosition: 0
[    14.516] 	DirectColorModeInfo: 0
[    14.516] 	PhysBasePtr: 0xd0000000
[    14.516] 	LinBytesPerScanLine: 1024
[    14.516] 	BnkNumberOfImagePages: 18
[    14.516] 	LinNumberOfImagePages: 18
[    14.516] 	LinRedMaskSize: 0
[    14.516] 	LinRedFieldPosition: 0
[    14.516] 	LinGreenMaskSize: 0
[    14.516] 	LinGreenFieldPosition: 0
[    14.516] 	LinBlueMaskSize: 0
[    14.516] 	LinBlueFieldPosition: 0
[    14.516] 	LinRsvdMaskSize: 0
[    14.516] 	LinRsvdFieldPosition: 0
[    14.516] 	MaxPixelClock: 400000000
[    14.517] Mode: 107 (1280x1024)
[    14.517] 	ModeAttributes: 0xbb
[    14.517] 	WinAAttributes: 0x7
[    14.517] 	WinBAttributes: 0x0
[    14.517] 	WinGranularity: 64
[    14.517] 	WinSize: 64
[    14.517] 	WinASegment: 0xa000
[    14.517] 	WinBSegment: 0x0
[    14.517] 	WinFuncPtr: 0xc00051ab
[    14.517] 	BytesPerScanline: 1280
[    14.517] 	XResolution: 1280
[    14.517] 	YResolution: 1024
[    14.517] 	XCharSize: 8
[    14.517] 	YCharSize: 16
[    14.517] 	NumberOfPlanes: 1
[    14.517] 	BitsPerPixel: 8
[    14.517] 	NumberOfBanks: 1
[    14.517] 	MemoryModel: 4
[    14.517] 	BankSize: 0
[    14.517] 	NumberOfImages: 11
[    14.517] 	RedMaskSize: 0
[    14.517] 	RedFieldPosition: 0
[    14.517] 	GreenMaskSize: 0
[    14.517] 	GreenFieldPosition: 0
[    14.517] 	BlueMaskSize: 0
[    14.517] 	BlueFieldPosition: 0
[    14.517] 	RsvdMaskSize: 0
[    14.517] 	RsvdFieldPosition: 0
[    14.517] 	DirectColorModeInfo: 0
[    14.517] 	PhysBasePtr: 0xd0000000
[    14.517] 	LinBytesPerScanLine: 1280
[    14.517] 	BnkNumberOfImagePages: 11
[    14.517] 	LinNumberOfImagePages: 11
[    14.517] 	LinRedMaskSize: 0
[    14.517] 	LinRedFieldPosition: 0
[    14.517] 	LinGreenMaskSize: 0
[    14.517] 	LinGreenFieldPosition: 0
[    14.517] 	LinBlueMaskSize: 0
[    14.517] 	LinBlueFieldPosition: 0
[    14.517] 	LinRsvdMaskSize: 0
[    14.517] 	LinRsvdFieldPosition: 0
[    14.517] 	MaxPixelClock: 400000000
[    14.518] Mode: 110 (640x480)
[    14.518] 	ModeAttributes: 0xbb
[    14.518] 	WinAAttributes: 0x7
[    14.518] 	WinBAttributes: 0x0
[    14.518] 	WinGranularity: 64
[    14.518] 	WinSize: 64
[    14.518] 	WinASegment: 0xa000
[    14.518] 	WinBSegment: 0x0
[    14.518] 	WinFuncPtr: 0xc00051ab
[    14.518] 	BytesPerScanline: 1280
[    14.518] 	XResolution: 640
[    14.518] 	YResolution: 480
[    14.518] 	XCharSize: 8
[    14.518] 	YCharSize: 16
[    14.518] 	NumberOfPlanes: 1
[    14.518] 	BitsPerPixel: 16
[    14.518] 	NumberOfBanks: 1
[    14.518] 	MemoryModel: 6
[    14.518] 	BankSize: 0
[    14.518] 	NumberOfImages: 24
[    14.518] 	RedMaskSize: 5
[    14.518] 	RedFieldPosition: 10
[    14.518] 	GreenMaskSize: 5
[    14.518] 	GreenFieldPosition: 5
[    14.518] 	BlueMaskSize: 5
[    14.518] 	BlueFieldPosition: 0
[    14.518] 	RsvdMaskSize: 0
[    14.518] 	RsvdFieldPosition: 0
[    14.518] 	DirectColorModeInfo: 0
[    14.518] 	PhysBasePtr: 0xd0000000
[    14.518] 	LinBytesPerScanLine: 1280
[    14.518] 	BnkNumberOfImagePages: 24
[    14.518] 	LinNumberOfImagePages: 24
[    14.518] 	LinRedMaskSize: 5
[    14.518] 	LinRedFieldPosition: 10
[    14.519] 	LinGreenMaskSize: 5
[    14.519] 	LinGreenFieldPosition: 5
[    14.519] 	LinBlueMaskSize: 5
[    14.519] 	LinBlueFieldPosition: 0
[    14.519] 	LinRsvdMaskSize: 0
[    14.519] 	LinRsvdFieldPosition: 0
[    14.519] 	MaxPixelClock: 400000000
[    14.520] Mode: 111 (640x480)
[    14.520] 	ModeAttributes: 0xbb
[    14.520] 	WinAAttributes: 0x7
[    14.520] 	WinBAttributes: 0x0
[    14.520] 	WinGranularity: 64
[    14.520] 	WinSize: 64
[    14.520] 	WinASegment: 0xa000
[    14.520] 	WinBSegment: 0x0
[    14.520] 	WinFuncPtr: 0xc00051ab
[    14.520] 	BytesPerScanline: 1280
[    14.520] 	XResolution: 640
[    14.520] 	YResolution: 480
[    14.520] 	XCharSize: 8
[    14.520] 	YCharSize: 16
[    14.520] 	NumberOfPlanes: 1
[    14.520] 	BitsPerPixel: 16
[    14.520] 	NumberOfBanks: 1
[    14.520] 	MemoryModel: 6
[    14.520] 	BankSize: 0
[    14.520] 	NumberOfImages: 24
[    14.520] 	RedMaskSize: 5
[    14.520] 	RedFieldPosition: 11
[    14.520] 	GreenMaskSize: 6
[    14.520] 	GreenFieldPosition: 5
[    14.520] 	BlueMaskSize: 5
[    14.520] 	BlueFieldPosition: 0
[    14.520] 	RsvdMaskSize: 0
[    14.520] 	RsvdFieldPosition: 0
[    14.520] 	DirectColorModeInfo: 0
[    14.520] 	PhysBasePtr: 0xd0000000
[    14.520] 	LinBytesPerScanLine: 1280
[    14.520] 	BnkNumberOfImagePages: 24
[    14.520] 	LinNumberOfImagePages: 24
[    14.520] 	LinRedMaskSize: 5
[    14.520] 	LinRedFieldPosition: 11
[    14.520] 	LinGreenMaskSize: 6
[    14.520] 	LinGreenFieldPosition: 5
[    14.520] 	LinBlueMaskSize: 5
[    14.520] 	LinBlueFieldPosition: 0
[    14.520] 	LinRsvdMaskSize: 0
[    14.520] 	LinRsvdFieldPosition: 0
[    14.520] 	MaxPixelClock: 400000000
[    14.521] Mode: 113 (800x600)
[    14.521] 	ModeAttributes: 0xbb
[    14.521] 	WinAAttributes: 0x7
[    14.521] 	WinBAttributes: 0x0
[    14.521] 	WinGranularity: 64
[    14.521] 	WinSize: 64
[    14.521] 	WinASegment: 0xa000
[    14.521] 	WinBSegment: 0x0
[    14.521] 	WinFuncPtr: 0xc00051ab
[    14.521] 	BytesPerScanline: 1600
[    14.521] 	XResolution: 800
[    14.521] 	YResolution: 600
[    14.521] 	XCharSize: 8
[    14.521] 	YCharSize: 14
[    14.521] 	NumberOfPlanes: 1
[    14.521] 	BitsPerPixel: 16
[    14.521] 	NumberOfBanks: 1
[    14.521] 	MemoryModel: 6
[    14.521] 	BankSize: 0
[    14.521] 	NumberOfImages: 16
[    14.521] 	RedMaskSize: 5
[    14.521] 	RedFieldPosition: 10
[    14.521] 	GreenMaskSize: 5
[    14.521] 	GreenFieldPosition: 5
[    14.521] 	BlueMaskSize: 5
[    14.521] 	BlueFieldPosition: 0
[    14.521] 	RsvdMaskSize: 0
[    14.521] 	RsvdFieldPosition: 0
[    14.521] 	DirectColorModeInfo: 0
[    14.521] 	PhysBasePtr: 0xd0000000
[    14.521] 	LinBytesPerScanLine: 1600
[    14.521] 	BnkNumberOfImagePages: 16
[    14.521] 	LinNumberOfImagePages: 16
[    14.521] 	LinRedMaskSize: 5
[    14.521] 	LinRedFieldPosition: 10
[    14.521] 	LinGreenMaskSize: 5
[    14.521] 	LinGreenFieldPosition: 5
[    14.521] 	LinBlueMaskSize: 5
[    14.521] 	LinBlueFieldPosition: 0
[    14.521] 	LinRsvdMaskSize: 0
[    14.521] 	LinRsvdFieldPosition: 0
[    14.521] 	MaxPixelClock: 400000000
[    14.522] Mode: 114 (800x600)
[    14.522] 	ModeAttributes: 0xbb
[    14.522] 	WinAAttributes: 0x7
[    14.522] 	WinBAttributes: 0x0
[    14.522] 	WinGranularity: 64
[    14.522] 	WinSize: 64
[    14.522] 	WinASegment: 0xa000
[    14.522] 	WinBSegment: 0x0
[    14.522] 	WinFuncPtr: 0xc00051ab
[    14.522] 	BytesPerScanline: 1600
[    14.522] 	XResolution: 800
[    14.522] 	YResolution: 600
[    14.522] 	XCharSize: 8
[    14.522] 	YCharSize: 14
[    14.522] 	NumberOfPlanes: 1
[    14.522] 	BitsPerPixel: 16
[    14.522] 	NumberOfBanks: 1
[    14.522] 	MemoryModel: 6
[    14.522] 	BankSize: 0
[    14.522] 	NumberOfImages: 16
[    14.522] 	RedMaskSize: 5
[    14.522] 	RedFieldPosition: 11
[    14.522] 	GreenMaskSize: 6
[    14.522] 	GreenFieldPosition: 5
[    14.522] 	BlueMaskSize: 5
[    14.522] 	BlueFieldPosition: 0
[    14.522] 	RsvdMaskSize: 0
[    14.522] 	RsvdFieldPosition: 0
[    14.522] 	DirectColorModeInfo: 0
[    14.522] 	PhysBasePtr: 0xd0000000
[    14.522] 	LinBytesPerScanLine: 1600
[    14.522] 	BnkNumberOfImagePages: 16
[    14.522] 	LinNumberOfImagePages: 16
[    14.522] 	LinRedMaskSize: 5
[    14.522] 	LinRedFieldPosition: 11
[    14.522] 	LinGreenMaskSize: 6
[    14.522] 	LinGreenFieldPosition: 5
[    14.522] 	LinBlueMaskSize: 5
[    14.522] 	LinBlueFieldPosition: 0
[    14.522] 	LinRsvdMaskSize: 0
[    14.522] 	LinRsvdFieldPosition: 0
[    14.522] 	MaxPixelClock: 400000000
[    14.523] Mode: 116 (1024x768)
[    14.523] 	ModeAttributes: 0xbb
[    14.523] 	WinAAttributes: 0x7
[    14.523] 	WinBAttributes: 0x0
[    14.523] 	WinGranularity: 64
[    14.523] 	WinSize: 64
[    14.523] 	WinASegment: 0xa000
[    14.523] 	WinBSegment: 0x0
[    14.523] 	WinFuncPtr: 0xc00051ab
[    14.523] 	BytesPerScanline: 2048
[    14.523] 	XResolution: 1024
[    14.523] 	YResolution: 768
[    14.523] 	XCharSize: 8
[    14.523] 	YCharSize: 16
[    14.523] 	NumberOfPlanes: 1
[    14.524] 	BitsPerPixel: 16
[    14.524] 	NumberOfBanks: 1
[    14.524] 	MemoryModel: 6
[    14.524] 	BankSize: 0
[    14.524] 	NumberOfImages: 9
[    14.524] 	RedMaskSize: 5
[    14.524] 	RedFieldPosition: 10
[    14.524] 	GreenMaskSize: 5
[    14.524] 	GreenFieldPosition: 5
[    14.524] 	BlueMaskSize: 5
[    14.524] 	BlueFieldPosition: 0
[    14.524] 	RsvdMaskSize: 0
[    14.524] 	RsvdFieldPosition: 0
[    14.524] 	DirectColorModeInfo: 0
[    14.524] 	PhysBasePtr: 0xd0000000
[    14.524] 	LinBytesPerScanLine: 2048
[    14.524] 	BnkNumberOfImagePages: 9
[    14.524] 	LinNumberOfImagePages: 9
[    14.524] 	LinRedMaskSize: 5
[    14.524] 	LinRedFieldPosition: 10
[    14.524] 	LinGreenMaskSize: 5
[    14.524] 	LinGreenFieldPosition: 5
[    14.524] 	LinBlueMaskSize: 5
[    14.524] 	LinBlueFieldPosition: 0
[    14.524] 	LinRsvdMaskSize: 0
[    14.524] 	LinRsvdFieldPosition: 0
[    14.524] 	MaxPixelClock: 400000000
[    14.525] Mode: 117 (1024x768)
[    14.525] 	ModeAttributes: 0xbb
[    14.525] 	WinAAttributes: 0x7
[    14.525] 	WinBAttributes: 0x0
[    14.525] 	WinGranularity: 64
[    14.525] 	WinSize: 64
[    14.525] 	WinASegment: 0xa000
[    14.525] 	WinBSegment: 0x0
[    14.525] 	WinFuncPtr: 0xc00051ab
[    14.525] 	BytesPerScanline: 2048
[    14.525] 	XResolution: 1024
[    14.525] 	YResolution: 768
[    14.525] 	XCharSize: 8
[    14.525] 	YCharSize: 16
[    14.525] 	NumberOfPlanes: 1
[    14.525] 	BitsPerPixel: 16
[    14.525] 	NumberOfBanks: 1
[    14.525] 	MemoryModel: 6
[    14.525] 	BankSize: 0
[    14.525] 	NumberOfImages: 9
[    14.525] 	RedMaskSize: 5
[    14.525] 	RedFieldPosition: 11
[    14.525] 	GreenMaskSize: 6
[    14.525] 	GreenFieldPosition: 5
[    14.525] 	BlueMaskSize: 5
[    14.525] 	BlueFieldPosition: 0
[    14.525] 	RsvdMaskSize: 0
[    14.525] 	RsvdFieldPosition: 0
[    14.525] 	DirectColorModeInfo: 0
[    14.525] 	PhysBasePtr: 0xd0000000
[    14.525] 	LinBytesPerScanLine: 2048
[    14.525] 	BnkNumberOfImagePages: 9
[    14.525] 	LinNumberOfImagePages: 9
[    14.525] 	LinRedMaskSize: 5
[    14.525] 	LinRedFieldPosition: 11
[    14.525] 	LinGreenMaskSize: 6
[    14.525] 	LinGreenFieldPosition: 5
[    14.525] 	LinBlueMaskSize: 5
[    14.525] 	LinBlueFieldPosition: 0
[    14.525] 	LinRsvdMaskSize: 0
[    14.525] 	LinRsvdFieldPosition: 0
[    14.525] 	MaxPixelClock: 400000000
[    14.526] Mode: 119 (1280x1024)
[    14.526] 	ModeAttributes: 0xbb
[    14.526] 	WinAAttributes: 0x7
[    14.526] 	WinBAttributes: 0x0
[    14.526] 	WinGranularity: 64
[    14.526] 	WinSize: 64
[    14.526] 	WinASegment: 0xa000
[    14.526] 	WinBSegment: 0x0
[    14.526] 	WinFuncPtr: 0xc00051ab
[    14.526] 	BytesPerScanline: 2560
[    14.526] 	XResolution: 1280
[    14.526] 	YResolution: 1024
[    14.526] 	XCharSize: 8
[    14.526] 	YCharSize: 16
[    14.526] 	NumberOfPlanes: 1
[    14.526] 	BitsPerPixel: 16
[    14.526] 	NumberOfBanks: 1
[    14.526] 	MemoryModel: 6
[    14.526] 	BankSize: 0
[    14.526] 	NumberOfImages: 5
[    14.526] 	RedMaskSize: 5
[    14.526] 	RedFieldPosition: 10
[    14.526] 	GreenMaskSize: 5
[    14.526] 	GreenFieldPosition: 5
[    14.526] 	BlueMaskSize: 5
[    14.526] 	BlueFieldPosition: 0
[    14.526] 	RsvdMaskSize: 0
[    14.526] 	RsvdFieldPosition: 0
[    14.526] 	DirectColorModeInfo: 0
[    14.526] 	PhysBasePtr: 0xd0000000
[    14.526] 	LinBytesPerScanLine: 2560
[    14.526] 	BnkNumberOfImagePages: 5
[    14.526] 	LinNumberOfImagePages: 5
[    14.526] 	LinRedMaskSize: 5
[    14.526] 	LinRedFieldPosition: 10
[    14.526] 	LinGreenMaskSize: 5
[    14.526] 	LinGreenFieldPosition: 5
[    14.526] 	LinBlueMaskSize: 5
[    14.526] 	LinBlueFieldPosition: 0
[    14.526] 	LinRsvdMaskSize: 0
[    14.526] 	LinRsvdFieldPosition: 0
[    14.526] 	MaxPixelClock: 400000000
[    14.527] Mode: 11a (1280x1024)
[    14.527] 	ModeAttributes: 0xbb
[    14.527] 	WinAAttributes: 0x7
[    14.527] 	WinBAttributes: 0x0
[    14.527] 	WinGranularity: 64
[    14.527] 	WinSize: 64
[    14.527] 	WinASegment: 0xa000
[    14.527] 	WinBSegment: 0x0
[    14.527] 	WinFuncPtr: 0xc00051ab
[    14.527] 	BytesPerScanline: 2560
[    14.527] 	XResolution: 1280
[    14.527] 	YResolution: 1024
[    14.527] 	XCharSize: 8
[    14.527] 	YCharSize: 16
[    14.527] 	NumberOfPlanes: 1
[    14.527] 	BitsPerPixel: 16
[    14.527] 	NumberOfBanks: 1
[    14.527] 	MemoryModel: 6
[    14.527] 	BankSize: 0
[    14.527] 	NumberOfImages: 5
[    14.527] 	RedMaskSize: 5
[    14.527] 	RedFieldPosition: 11
[    14.528] 	GreenMaskSize: 6
[    14.528] 	GreenFieldPosition: 5
[    14.528] 	BlueMaskSize: 5
[    14.528] 	BlueFieldPosition: 0
[    14.528] 	RsvdMaskSize: 0
[    14.528] 	RsvdFieldPosition: 0
[    14.528] 	DirectColorModeInfo: 0
[    14.528] 	PhysBasePtr: 0xd0000000
[    14.528] 	LinBytesPerScanLine: 2560
[    14.528] 	BnkNumberOfImagePages: 5
[    14.528] 	LinNumberOfImagePages: 5
[    14.528] 	LinRedMaskSize: 5
[    14.528] 	LinRedFieldPosition: 11
[    14.528] 	LinGreenMaskSize: 6
[    14.528] 	LinGreenFieldPosition: 5
[    14.528] 	LinBlueMaskSize: 5
[    14.528] 	LinBlueFieldPosition: 0
[    14.528] 	LinRsvdMaskSize: 0
[    14.528] 	LinRsvdFieldPosition: 0
[    14.528] 	MaxPixelClock: 400000000
[    14.529] Mode: 10d (320x200)
[    14.529] 	ModeAttributes: 0xbb
[    14.529] 	WinAAttributes: 0x7
[    14.529] 	WinBAttributes: 0x0
[    14.529] 	WinGranularity: 64
[    14.529] 	WinSize: 64
[    14.529] 	WinASegment: 0xa000
[    14.529] 	WinBSegment: 0x0
[    14.529] 	WinFuncPtr: 0xc00051ab
[    14.529] 	BytesPerScanline: 640
[    14.529] 	XResolution: 320
[    14.529] 	YResolution: 200
[    14.529] 	XCharSize: 8
[    14.529] 	YCharSize: 8
[    14.529] 	NumberOfPlanes: 1
[    14.529] 	BitsPerPixel: 16
[    14.529] 	NumberOfBanks: 1
[    14.529] 	MemoryModel: 6
[    14.529] 	BankSize: 0
[    14.529] 	NumberOfImages: 127
[    14.529] 	RedMaskSize: 5
[    14.529] 	RedFieldPosition: 10
[    14.529] 	GreenMaskSize: 5
[    14.529] 	GreenFieldPosition: 5
[    14.529] 	BlueMaskSize: 5
[    14.529] 	BlueFieldPosition: 0
[    14.529] 	RsvdMaskSize: 0
[    14.529] 	RsvdFieldPosition: 0
[    14.529] 	DirectColorModeInfo: 0
[    14.529] 	PhysBasePtr: 0xd0000000
[    14.529] 	LinBytesPerScanLine: 640
[    14.529] 	BnkNumberOfImagePages: 127
[    14.529] 	LinNumberOfImagePages: 127
[    14.529] 	LinRedMaskSize: 5
[    14.529] 	LinRedFieldPosition: 10
[    14.529] 	LinGreenMaskSize: 5
[    14.529] 	LinGreenFieldPosition: 5
[    14.529] 	LinBlueMaskSize: 5
[    14.529] 	LinBlueFieldPosition: 0
[    14.529] 	LinRsvdMaskSize: 0
[    14.529] 	LinRsvdFieldPosition: 0
[    14.529] 	MaxPixelClock: 400000000
[    14.530] Mode: 10e (320x200)
[    14.530] 	ModeAttributes: 0xbb
[    14.530] 	WinAAttributes: 0x7
[    14.530] 	WinBAttributes: 0x0
[    14.530] 	WinGranularity: 64
[    14.530] 	WinSize: 64
[    14.530] 	WinASegment: 0xa000
[    14.530] 	WinBSegment: 0x0
[    14.530] 	WinFuncPtr: 0xc00051ab
[    14.530] 	BytesPerScanline: 640
[    14.530] 	XResolution: 320
[    14.530] 	YResolution: 200
[    14.530] 	XCharSize: 8
[    14.530] 	YCharSize: 8
[    14.530] 	NumberOfPlanes: 1
[    14.530] 	BitsPerPixel: 16
[    14.530] 	NumberOfBanks: 1
[    14.530] 	MemoryModel: 6
[    14.530] 	BankSize: 0
[    14.530] 	NumberOfImages: 127
[    14.530] 	RedMaskSize: 5
[    14.530] 	RedFieldPosition: 11
[    14.530] 	GreenMaskSize: 6
[    14.530] 	GreenFieldPosition: 5
[    14.530] 	BlueMaskSize: 5
[    14.530] 	BlueFieldPosition: 0
[    14.530] 	RsvdMaskSize: 0
[    14.530] 	RsvdFieldPosition: 0
[    14.530] 	DirectColorModeInfo: 0
[    14.530] 	PhysBasePtr: 0xd0000000
[    14.530] 	LinBytesPerScanLine: 640
[    14.530] 	BnkNumberOfImagePages: 127
[    14.530] 	LinNumberOfImagePages: 127
[    14.530] 	LinRedMaskSize: 5
[    14.530] 	LinRedFieldPosition: 11
[    14.530] 	LinGreenMaskSize: 6
[    14.530] 	LinGreenFieldPosition: 5
[    14.530] 	LinBlueMaskSize: 5
[    14.530] 	LinBlueFieldPosition: 0
[    14.530] 	LinRsvdMaskSize: 0
[    14.530] 	LinRsvdFieldPosition: 0
[    14.530] 	MaxPixelClock: 400000000
[    14.531] *Mode: 120 (320x200)
[    14.531] 	ModeAttributes: 0xbb
[    14.531] 	WinAAttributes: 0x7
[    14.531] 	WinBAttributes: 0x0
[    14.531] 	WinGranularity: 64
[    14.531] 	WinSize: 64
[    14.531] 	WinASegment: 0xa000
[    14.531] 	WinBSegment: 0x0
[    14.531] 	WinFuncPtr: 0xc00051ab
[    14.531] 	BytesPerScanline: 1280
[    14.531] 	XResolution: 320
[    14.531] 	YResolution: 200
[    14.531] 	XCharSize: 8
[    14.531] 	YCharSize: 8
[    14.531] 	NumberOfPlanes: 1
[    14.531] 	BitsPerPixel: 32
[    14.531] 	NumberOfBanks: 1
[    14.531] 	MemoryModel: 6
[    14.531] 	BankSize: 0
[    14.531] 	NumberOfImages: 63
[    14.531] 	RedMaskSize: 8
[    14.531] 	RedFieldPosition: 16
[    14.531] 	GreenMaskSize: 8
[    14.531] 	GreenFieldPosition: 8
[    14.531] 	BlueMaskSize: 8
[    14.531] 	BlueFieldPosition: 0
[    14.531] 	RsvdMaskSize: 0
[    14.531] 	RsvdFieldPosition: 0
[    14.531] 	DirectColorModeInfo: 0
[    14.531] 	PhysBasePtr: 0xd0000000
[    14.531] 	LinBytesPerScanLine: 1280
[    14.531] 	BnkNumberOfImagePages: 63
[    14.531] 	LinNumberOfImagePages: 63
[    14.531] 	LinRedMaskSize: 8
[    14.531] 	LinRedFieldPosition: 16
[    14.531] 	LinGreenMaskSize: 8
[    14.531] 	LinGreenFieldPosition: 8
[    14.531] 	LinBlueMaskSize: 8
[    14.531] 	LinBlueFieldPosition: 0
[    14.531] 	LinRsvdMaskSize: 0
[    14.531] 	LinRsvdFieldPosition: 0
[    14.531] 	MaxPixelClock: 400000000
[    14.532] Mode: 193 (320x240)
[    14.532] 	ModeAttributes: 0xbb
[    14.532] 	WinAAttributes: 0x7
[    14.532] 	WinBAttributes: 0x0
[    14.532] 	WinGranularity: 64
[    14.532] 	WinSize: 64
[    14.532] 	WinASegment: 0xa000
[    14.533] 	WinBSegment: 0x0
[    14.533] 	WinFuncPtr: 0xc00051ab
[    14.533] 	BytesPerScanline: 320
[    14.533] 	XResolution: 320
[    14.533] 	YResolution: 240
[    14.533] 	XCharSize: 8
[    14.533] 	YCharSize: 8
[    14.533] 	NumberOfPlanes: 1
[    14.533] 	BitsPerPixel: 8
[    14.533] 	NumberOfBanks: 1
[    14.533] 	MemoryModel: 4
[    14.533] 	BankSize: 0
[    14.533] 	NumberOfImages: 127
[    14.533] 	RedMaskSize: 0
[    14.533] 	RedFieldPosition: 0
[    14.533] 	GreenMaskSize: 0
[    14.533] 	GreenFieldPosition: 0
[    14.533] 	BlueMaskSize: 0
[    14.533] 	BlueFieldPosition: 0
[    14.533] 	RsvdMaskSize: 0
[    14.533] 	RsvdFieldPosition: 0
[    14.533] 	DirectColorModeInfo: 0
[    14.533] 	PhysBasePtr: 0xd0000000
[    14.533] 	LinBytesPerScanLine: 320
[    14.533] 	BnkNumberOfImagePages: 127
[    14.533] 	LinNumberOfImagePages: 127
[    14.533] 	LinRedMaskSize: 0
[    14.533] 	LinRedFieldPosition: 0
[    14.533] 	LinGreenMaskSize: 0
[    14.533] 	LinGreenFieldPosition: 0
[    14.533] 	LinBlueMaskSize: 0
[    14.533] 	LinBlueFieldPosition: 0
[    14.533] 	LinRsvdMaskSize: 0
[    14.533] 	LinRsvdFieldPosition: 0
[    14.533] 	MaxPixelClock: 400000000
[    14.534] Mode: 195 (320x240)
[    14.534] 	ModeAttributes: 0xbb
[    14.534] 	WinAAttributes: 0x7
[    14.534] 	WinBAttributes: 0x0
[    14.534] 	WinGranularity: 64
[    14.534] 	WinSize: 64
[    14.534] 	WinASegment: 0xa000
[    14.534] 	WinBSegment: 0x0
[    14.534] 	WinFuncPtr: 0xc00051ab
[    14.534] 	BytesPerScanline: 640
[    14.534] 	XResolution: 320
[    14.534] 	YResolution: 240
[    14.534] 	XCharSize: 8
[    14.534] 	YCharSize: 8
[    14.534] 	NumberOfPlanes: 1
[    14.534] 	BitsPerPixel: 16
[    14.534] 	NumberOfBanks: 1
[    14.534] 	MemoryModel: 6
[    14.534] 	BankSize: 0
[    14.534] 	NumberOfImages: 84
[    14.534] 	RedMaskSize: 5
[    14.534] 	RedFieldPosition: 11
[    14.534] 	GreenMaskSize: 6
[    14.534] 	GreenFieldPosition: 5
[    14.534] 	BlueMaskSize: 5
[    14.534] 	BlueFieldPosition: 0
[    14.534] 	RsvdMaskSize: 0
[    14.534] 	RsvdFieldPosition: 0
[    14.534] 	DirectColorModeInfo: 0
[    14.534] 	PhysBasePtr: 0xd0000000
[    14.534] 	LinBytesPerScanLine: 640
[    14.534] 	BnkNumberOfImagePages: 84
[    14.534] 	LinNumberOfImagePages: 84
[    14.534] 	LinRedMaskSize: 5
[    14.534] 	LinRedFieldPosition: 11
[    14.534] 	LinGreenMaskSize: 6
[    14.534] 	LinGreenFieldPosition: 5
[    14.534] 	LinBlueMaskSize: 5
[    14.534] 	LinBlueFieldPosition: 0
[    14.534] 	LinRsvdMaskSize: 0
[    14.534] 	LinRsvdFieldPosition: 0
[    14.534] 	MaxPixelClock: 400000000
[    14.535] *Mode: 196 (320x240)
[    14.535] 	ModeAttributes: 0xbb
[    14.535] 	WinAAttributes: 0x7
[    14.535] 	WinBAttributes: 0x0
[    14.535] 	WinGranularity: 64
[    14.535] 	WinSize: 64
[    14.535] 	WinASegment: 0xa000
[    14.535] 	WinBSegment: 0x0
[    14.535] 	WinFuncPtr: 0xc00051ab
[    14.535] 	BytesPerScanline: 1280
[    14.535] 	XResolution: 320
[    14.535] 	YResolution: 240
[    14.535] 	XCharSize: 8
[    14.535] 	YCharSize: 8
[    14.535] 	NumberOfPlanes: 1
[    14.535] 	BitsPerPixel: 32
[    14.535] 	NumberOfBanks: 1
[    14.535] 	MemoryModel: 6
[    14.535] 	BankSize: 0
[    14.535] 	NumberOfImages: 50
[    14.535] 	RedMaskSize: 8
[    14.535] 	RedFieldPosition: 16
[    14.535] 	GreenMaskSize: 8
[    14.535] 	GreenFieldPosition: 8
[    14.535] 	BlueMaskSize: 8
[    14.535] 	BlueFieldPosition: 0
[    14.535] 	RsvdMaskSize: 0
[    14.535] 	RsvdFieldPosition: 0
[    14.535] 	DirectColorModeInfo: 0
[    14.535] 	PhysBasePtr: 0xd0000000
[    14.535] 	LinBytesPerScanLine: 1280
[    14.535] 	BnkNumberOfImagePages: 50
[    14.535] 	LinNumberOfImagePages: 50
[    14.535] 	LinRedMaskSize: 8
[    14.535] 	LinRedFieldPosition: 16
[    14.535] 	LinGreenMaskSize: 8
[    14.535] 	LinGreenFieldPosition: 8
[    14.535] 	LinBlueMaskSize: 8
[    14.535] 	LinBlueFieldPosition: 0
[    14.535] 	LinRsvdMaskSize: 0
[    14.535] 	LinRsvdFieldPosition: 0
[    14.535] 	MaxPixelClock: 400000000
[    14.536] Mode: 1b3 (512x384)
[    14.536] 	ModeAttributes: 0xbb
[    14.536] 	WinAAttributes: 0x7
[    14.536] 	WinBAttributes: 0x0
[    14.536] 	WinGranularity: 64
[    14.536] 	WinSize: 64
[    14.536] 	WinASegment: 0xa000
[    14.536] 	WinBSegment: 0x0
[    14.536] 	WinFuncPtr: 0xc00051ab
[    14.536] 	BytesPerScanline: 512
[    14.536] 	XResolution: 512
[    14.536] 	YResolution: 384
[    14.536] 	XCharSize: 8
[    14.536] 	YCharSize: 16
[    14.536] 	NumberOfPlanes: 1
[    14.536] 	BitsPerPixel: 8
[    14.536] 	NumberOfBanks: 1
[    14.536] 	MemoryModel: 4
[    14.536] 	BankSize: 0
[    14.536] 	NumberOfImages: 63
[    14.536] 	RedMaskSize: 0
[    14.536] 	RedFieldPosition: 0
[    14.536] 	GreenMaskSize: 0
[    14.536] 	GreenFieldPosition: 0
[    14.536] 	BlueMaskSize: 0
[    14.536] 	BlueFieldPosition: 0
[    14.536] 	RsvdMaskSize: 0
[    14.536] 	RsvdFieldPosition: 0
[    14.536] 	DirectColorModeInfo: 0
[    14.536] 	PhysBasePtr: 0xd0000000
[    14.537] 	LinBytesPerScanLine: 512
[    14.537] 	BnkNumberOfImagePages: 63
[    14.537] 	LinNumberOfImagePages: 63
[    14.537] 	LinRedMaskSize: 0
[    14.537] 	LinRedFieldPosition: 0
[    14.537] 	LinGreenMaskSize: 0
[    14.537] 	LinGreenFieldPosition: 0
[    14.537] 	LinBlueMaskSize: 0
[    14.537] 	LinBlueFieldPosition: 0
[    14.537] 	LinRsvdMaskSize: 0
[    14.537] 	LinRsvdFieldPosition: 0
[    14.537] 	MaxPixelClock: 400000000
[    14.538] Mode: 1b5 (512x384)
[    14.538] 	ModeAttributes: 0xbb
[    14.538] 	WinAAttributes: 0x7
[    14.538] 	WinBAttributes: 0x0
[    14.538] 	WinGranularity: 64
[    14.538] 	WinSize: 64
[    14.538] 	WinASegment: 0xa000
[    14.538] 	WinBSegment: 0x0
[    14.538] 	WinFuncPtr: 0xc00051ab
[    14.538] 	BytesPerScanline: 1024
[    14.538] 	XResolution: 512
[    14.538] 	YResolution: 384
[    14.538] 	XCharSize: 8
[    14.538] 	YCharSize: 16
[    14.538] 	NumberOfPlanes: 1
[    14.538] 	BitsPerPixel: 16
[    14.538] 	NumberOfBanks: 1
[    14.538] 	MemoryModel: 6
[    14.538] 	BankSize: 0
[    14.538] 	NumberOfImages: 35
[    14.538] 	RedMaskSize: 5
[    14.538] 	RedFieldPosition: 11
[    14.538] 	GreenMaskSize: 6
[    14.538] 	GreenFieldPosition: 5
[    14.538] 	BlueMaskSize: 5
[    14.538] 	BlueFieldPosition: 0
[    14.538] 	RsvdMaskSize: 0
[    14.538] 	RsvdFieldPosition: 0
[    14.538] 	DirectColorModeInfo: 0
[    14.538] 	PhysBasePtr: 0xd0000000
[    14.538] 	LinBytesPerScanLine: 1024
[    14.538] 	BnkNumberOfImagePages: 35
[    14.538] 	LinNumberOfImagePages: 35
[    14.538] 	LinRedMaskSize: 5
[    14.538] 	LinRedFieldPosition: 11
[    14.538] 	LinGreenMaskSize: 6
[    14.538] 	LinGreenFieldPosition: 5
[    14.538] 	LinBlueMaskSize: 5
[    14.538] 	LinBlueFieldPosition: 0
[    14.538] 	LinRsvdMaskSize: 0
[    14.538] 	LinRsvdFieldPosition: 0
[    14.538] 	MaxPixelClock: 400000000
[    14.539] *Mode: 1b6 (512x384)
[    14.539] 	ModeAttributes: 0xbb
[    14.539] 	WinAAttributes: 0x7
[    14.539] 	WinBAttributes: 0x0
[    14.539] 	WinGranularity: 64
[    14.539] 	WinSize: 64
[    14.539] 	WinASegment: 0xa000
[    14.539] 	WinBSegment: 0x0
[    14.539] 	WinFuncPtr: 0xc00051ab
[    14.539] 	BytesPerScanline: 2048
[    14.539] 	XResolution: 512
[    14.539] 	YResolution: 384
[    14.539] 	XCharSize: 8
[    14.539] 	YCharSize: 16
[    14.539] 	NumberOfPlanes: 1
[    14.539] 	BitsPerPixel: 32
[    14.539] 	NumberOfBanks: 1
[    14.539] 	MemoryModel: 6
[    14.539] 	BankSize: 0
[    14.539] 	NumberOfImages: 18
[    14.539] 	RedMaskSize: 8
[    14.539] 	RedFieldPosition: 16
[    14.539] 	GreenMaskSize: 8
[    14.539] 	GreenFieldPosition: 8
[    14.539] 	BlueMaskSize: 8
[    14.539] 	BlueFieldPosition: 0
[    14.539] 	RsvdMaskSize: 0
[    14.539] 	RsvdFieldPosition: 0
[    14.539] 	DirectColorModeInfo: 0
[    14.539] 	PhysBasePtr: 0xd0000000
[    14.539] 	LinBytesPerScanLine: 2048
[    14.539] 	BnkNumberOfImagePages: 18
[    14.539] 	LinNumberOfImagePages: 18
[    14.539] 	LinRedMaskSize: 8
[    14.539] 	LinRedFieldPosition: 16
[    14.539] 	LinGreenMaskSize: 8
[    14.539] 	LinGreenFieldPosition: 8
[    14.539] 	LinBlueMaskSize: 8
[    14.539] 	LinBlueFieldPosition: 0
[    14.539] 	LinRsvdMaskSize: 0
[    14.539] 	LinRsvdFieldPosition: 0
[    14.539] 	MaxPixelClock: 400000000
[    14.540] Mode: 1c3 (640x350)
[    14.540] 	ModeAttributes: 0xbb
[    14.540] 	WinAAttributes: 0x7
[    14.540] 	WinBAttributes: 0x0
[    14.540] 	WinGranularity: 64
[    14.540] 	WinSize: 64
[    14.540] 	WinASegment: 0xa000
[    14.540] 	WinBSegment: 0x0
[    14.540] 	WinFuncPtr: 0xc00051ab
[    14.540] 	BytesPerScanline: 640
[    14.540] 	XResolution: 640
[    14.540] 	YResolution: 350
[    14.540] 	XCharSize: 8
[    14.540] 	YCharSize: 14
[    14.540] 	NumberOfPlanes: 1
[    14.540] 	BitsPerPixel: 8
[    14.540] 	NumberOfBanks: 1
[    14.540] 	MemoryModel: 4
[    14.540] 	BankSize: 0
[    14.540] 	NumberOfImages: 63
[    14.540] 	RedMaskSize: 0
[    14.540] 	RedFieldPosition: 0
[    14.540] 	GreenMaskSize: 0
[    14.540] 	GreenFieldPosition: 0
[    14.540] 	BlueMaskSize: 0
[    14.540] 	BlueFieldPosition: 0
[    14.540] 	RsvdMaskSize: 0
[    14.540] 	RsvdFieldPosition: 0
[    14.540] 	DirectColorModeInfo: 0
[    14.540] 	PhysBasePtr: 0xd0000000
[    14.540] 	LinBytesPerScanLine: 640
[    14.540] 	BnkNumberOfImagePages: 63
[    14.540] 	LinNumberOfImagePages: 63
[    14.540] 	LinRedMaskSize: 0
[    14.540] 	LinRedFieldPosition: 0
[    14.540] 	LinGreenMaskSize: 0
[    14.540] 	LinGreenFieldPosition: 0
[    14.540] 	LinBlueMaskSize: 0
[    14.540] 	LinBlueFieldPosition: 0
[    14.540] 	LinRsvdMaskSize: 0
[    14.541] 	LinRsvdFieldPosition: 0
[    14.541] 	MaxPixelClock: 400000000
[    14.542] Mode: 1c5 (640x350)
[    14.542] 	ModeAttributes: 0xbb
[    14.542] 	WinAAttributes: 0x7
[    14.542] 	WinBAttributes: 0x0
[    14.542] 	WinGranularity: 64
[    14.542] 	WinSize: 64
[    14.542] 	WinASegment: 0xa000
[    14.542] 	WinBSegment: 0x0
[    14.542] 	WinFuncPtr: 0xc00051ab
[    14.542] 	BytesPerScanline: 1280
[    14.542] 	XResolution: 640
[    14.542] 	YResolution: 350
[    14.542] 	XCharSize: 8
[    14.542] 	YCharSize: 14
[    14.542] 	NumberOfPlanes: 1
[    14.542] 	BitsPerPixel: 16
[    14.542] 	NumberOfBanks: 1
[    14.542] 	MemoryModel: 6
[    14.542] 	BankSize: 0
[    14.542] 	NumberOfImages: 35
[    14.542] 	RedMaskSize: 5
[    14.542] 	RedFieldPosition: 11
[    14.542] 	GreenMaskSize: 6
[    14.542] 	GreenFieldPosition: 5
[    14.542] 	BlueMaskSize: 5
[    14.542] 	BlueFieldPosition: 0
[    14.542] 	RsvdMaskSize: 0
[    14.542] 	RsvdFieldPosition: 0
[    14.542] 	DirectColorModeInfo: 0
[    14.542] 	PhysBasePtr: 0xd0000000
[    14.542] 	LinBytesPerScanLine: 1280
[    14.542] 	BnkNumberOfImagePages: 35
[    14.542] 	LinNumberOfImagePages: 35
[    14.542] 	LinRedMaskSize: 5
[    14.542] 	LinRedFieldPosition: 11
[    14.542] 	LinGreenMaskSize: 6
[    14.542] 	LinGreenFieldPosition: 5
[    14.542] 	LinBlueMaskSize: 5
[    14.542] 	LinBlueFieldPosition: 0
[    14.542] 	LinRsvdMaskSize: 0
[    14.542] 	LinRsvdFieldPosition: 0
[    14.542] 	MaxPixelClock: 400000000
[    14.543] *Mode: 1c6 (640x350)
[    14.543] 	ModeAttributes: 0xbb
[    14.543] 	WinAAttributes: 0x7
[    14.543] 	WinBAttributes: 0x0
[    14.543] 	WinGranularity: 64
[    14.543] 	WinSize: 64
[    14.543] 	WinASegment: 0xa000
[    14.543] 	WinBSegment: 0x0
[    14.543] 	WinFuncPtr: 0xc00051ab
[    14.543] 	BytesPerScanline: 2560
[    14.543] 	XResolution: 640
[    14.543] 	YResolution: 350
[    14.543] 	XCharSize: 8
[    14.543] 	YCharSize: 14
[    14.543] 	NumberOfPlanes: 1
[    14.543] 	BitsPerPixel: 32
[    14.543] 	NumberOfBanks: 1
[    14.543] 	MemoryModel: 6
[    14.543] 	BankSize: 0
[    14.543] 	NumberOfImages: 17
[    14.543] 	RedMaskSize: 8
[    14.543] 	RedFieldPosition: 16
[    14.543] 	GreenMaskSize: 8
[    14.543] 	GreenFieldPosition: 8
[    14.543] 	BlueMaskSize: 8
[    14.543] 	BlueFieldPosition: 0
[    14.543] 	RsvdMaskSize: 0
[    14.543] 	RsvdFieldPosition: 0
[    14.543] 	DirectColorModeInfo: 0
[    14.543] 	PhysBasePtr: 0xd0000000
[    14.543] 	LinBytesPerScanLine: 2560
[    14.543] 	BnkNumberOfImagePages: 17
[    14.543] 	LinNumberOfImagePages: 17
[    14.543] 	LinRedMaskSize: 8
[    14.543] 	LinRedFieldPosition: 16
[    14.543] 	LinGreenMaskSize: 8
[    14.543] 	LinGreenFieldPosition: 8
[    14.543] 	LinBlueMaskSize: 8
[    14.543] 	LinBlueFieldPosition: 0
[    14.543] 	LinRsvdMaskSize: 0
[    14.543] 	LinRsvdFieldPosition: 0
[    14.543] 	MaxPixelClock: 400000000
[    14.544] Mode: 133 (720x400)
[    14.544] 	ModeAttributes: 0xbb
[    14.544] 	WinAAttributes: 0x7
[    14.544] 	WinBAttributes: 0x0
[    14.544] 	WinGranularity: 64
[    14.544] 	WinSize: 64
[    14.544] 	WinASegment: 0xa000
[    14.544] 	WinBSegment: 0x0
[    14.544] 	WinFuncPtr: 0xc00051ab
[    14.544] 	BytesPerScanline: 768
[    14.544] 	XResolution: 720
[    14.544] 	YResolution: 400
[    14.544] 	XCharSize: 8
[    14.544] 	YCharSize: 16
[    14.544] 	NumberOfPlanes: 1
[    14.544] 	BitsPerPixel: 8
[    14.544] 	NumberOfBanks: 1
[    14.544] 	MemoryModel: 4
[    14.544] 	BankSize: 0
[    14.544] 	NumberOfImages: 50
[    14.544] 	RedMaskSize: 0
[    14.544] 	RedFieldPosition: 0
[    14.544] 	GreenMaskSize: 0
[    14.544] 	GreenFieldPosition: 0
[    14.544] 	BlueMaskSize: 0
[    14.544] 	BlueFieldPosition: 0
[    14.544] 	RsvdMaskSize: 0
[    14.544] 	RsvdFieldPosition: 0
[    14.544] 	DirectColorModeInfo: 0
[    14.544] 	PhysBasePtr: 0xd0000000
[    14.544] 	LinBytesPerScanLine: 768
[    14.544] 	BnkNumberOfImagePages: 50
[    14.544] 	LinNumberOfImagePages: 50
[    14.544] 	LinRedMaskSize: 0
[    14.544] 	LinRedFieldPosition: 0
[    14.544] 	LinGreenMaskSize: 0
[    14.544] 	LinGreenFieldPosition: 0
[    14.544] 	LinBlueMaskSize: 0
[    14.544] 	LinBlueFieldPosition: 0
[    14.544] 	LinRsvdMaskSize: 0
[    14.545] 	LinRsvdFieldPosition: 0
[    14.545] 	MaxPixelClock: 400000000
[    14.546] Mode: 135 (720x400)
[    14.546] 	ModeAttributes: 0xbb
[    14.546] 	WinAAttributes: 0x7
[    14.546] 	WinBAttributes: 0x0
[    14.546] 	WinGranularity: 64
[    14.546] 	WinSize: 64
[    14.546] 	WinASegment: 0xa000
[    14.546] 	WinBSegment: 0x0
[    14.546] 	WinFuncPtr: 0xc00051ab
[    14.546] 	BytesPerScanline: 1472
[    14.546] 	XResolution: 720
[    14.546] 	YResolution: 400
[    14.546] 	XCharSize: 8
[    14.546] 	YCharSize: 16
[    14.546] 	NumberOfPlanes: 1
[    14.546] 	BitsPerPixel: 16
[    14.546] 	NumberOfBanks: 1
[    14.546] 	MemoryModel: 6
[    14.546] 	BankSize: 0
[    14.546] 	NumberOfImages: 27
[    14.546] 	RedMaskSize: 5
[    14.546] 	RedFieldPosition: 11
[    14.546] 	GreenMaskSize: 6
[    14.546] 	GreenFieldPosition: 5
[    14.546] 	BlueMaskSize: 5
[    14.546] 	BlueFieldPosition: 0
[    14.546] 	RsvdMaskSize: 0
[    14.546] 	RsvdFieldPosition: 0
[    14.546] 	DirectColorModeInfo: 0
[    14.546] 	PhysBasePtr: 0xd0000000
[    14.546] 	LinBytesPerScanLine: 1472
[    14.546] 	BnkNumberOfImagePages: 27
[    14.546] 	LinNumberOfImagePages: 27
[    14.546] 	LinRedMaskSize: 5
[    14.546] 	LinRedFieldPosition: 11
[    14.546] 	LinGreenMaskSize: 6
[    14.546] 	LinGreenFieldPosition: 5
[    14.546] 	LinBlueMaskSize: 5
[    14.546] 	LinBlueFieldPosition: 0
[    14.546] 	LinRsvdMaskSize: 0
[    14.546] 	LinRsvdFieldPosition: 0
[    14.546] 	MaxPixelClock: 400000000
[    14.547] *Mode: 136 (720x400)
[    14.547] 	ModeAttributes: 0xbb
[    14.547] 	WinAAttributes: 0x7
[    14.547] 	WinBAttributes: 0x0
[    14.547] 	WinGranularity: 64
[    14.547] 	WinSize: 64
[    14.547] 	WinASegment: 0xa000
[    14.547] 	WinBSegment: 0x0
[    14.547] 	WinFuncPtr: 0xc00051ab
[    14.547] 	BytesPerScanline: 2944
[    14.547] 	XResolution: 720
[    14.547] 	YResolution: 400
[    14.547] 	XCharSize: 8
[    14.547] 	YCharSize: 16
[    14.547] 	NumberOfPlanes: 1
[    14.547] 	BitsPerPixel: 32
[    14.547] 	NumberOfBanks: 1
[    14.547] 	MemoryModel: 6
[    14.547] 	BankSize: 0
[    14.547] 	NumberOfImages: 13
[    14.547] 	RedMaskSize: 8
[    14.547] 	RedFieldPosition: 16
[    14.547] 	GreenMaskSize: 8
[    14.547] 	GreenFieldPosition: 8
[    14.547] 	BlueMaskSize: 8
[    14.547] 	BlueFieldPosition: 0
[    14.547] 	RsvdMaskSize: 0
[    14.547] 	RsvdFieldPosition: 0
[    14.547] 	DirectColorModeInfo: 0
[    14.547] 	PhysBasePtr: 0xd0000000
[    14.547] 	LinBytesPerScanLine: 2944
[    14.547] 	BnkNumberOfImagePages: 13
[    14.547] 	LinNumberOfImagePages: 13
[    14.547] 	LinRedMaskSize: 8
[    14.547] 	LinRedFieldPosition: 16
[    14.547] 	LinGreenMaskSize: 8
[    14.547] 	LinGreenFieldPosition: 8
[    14.547] 	LinBlueMaskSize: 8
[    14.547] 	LinBlueFieldPosition: 0
[    14.547] 	LinRsvdMaskSize: 0
[    14.547] 	LinRsvdFieldPosition: 0
[    14.547] 	MaxPixelClock: 400000000
[    14.548] Mode: 153 (1152x864)
[    14.548] 	ModeAttributes: 0xbb
[    14.548] 	WinAAttributes: 0x7
[    14.548] 	WinBAttributes: 0x0
[    14.548] 	WinGranularity: 64
[    14.548] 	WinSize: 64
[    14.548] 	WinASegment: 0xa000
[    14.548] 	WinBSegment: 0x0
[    14.548] 	WinFuncPtr: 0xc00051ab
[    14.548] 	BytesPerScanline: 1152
[    14.548] 	XResolution: 1152
[    14.548] 	YResolution: 864
[    14.548] 	XCharSize: 8
[    14.548] 	YCharSize: 16
[    14.548] 	NumberOfPlanes: 1
[    14.548] 	BitsPerPixel: 8
[    14.548] 	NumberOfBanks: 1
[    14.548] 	MemoryModel: 4
[    14.548] 	BankSize: 0
[    14.548] 	NumberOfImages: 15
[    14.548] 	RedMaskSize: 0
[    14.548] 	RedFieldPosition: 0
[    14.548] 	GreenMaskSize: 0
[    14.548] 	GreenFieldPosition: 0
[    14.548] 	BlueMaskSize: 0
[    14.548] 	BlueFieldPosition: 0
[    14.548] 	RsvdMaskSize: 0
[    14.548] 	RsvdFieldPosition: 0
[    14.548] 	DirectColorModeInfo: 0
[    14.548] 	PhysBasePtr: 0xd0000000
[    14.548] 	LinBytesPerScanLine: 1152
[    14.548] 	BnkNumberOfImagePages: 15
[    14.548] 	LinNumberOfImagePages: 15
[    14.548] 	LinRedMaskSize: 0
[    14.548] 	LinRedFieldPosition: 0
[    14.548] 	LinGreenMaskSize: 0
[    14.548] 	LinGreenFieldPosition: 0
[    14.548] 	LinBlueMaskSize: 0
[    14.548] 	LinBlueFieldPosition: 0
[    14.548] 	LinRsvdMaskSize: 0
[    14.548] 	LinRsvdFieldPosition: 0
[    14.548] 	MaxPixelClock: 400000000
[    14.550] Mode: 155 (1152x864)
[    14.550] 	ModeAttributes: 0xbb
[    14.550] 	WinAAttributes: 0x7
[    14.550] 	WinBAttributes: 0x0
[    14.550] 	WinGranularity: 64
[    14.550] 	WinSize: 64
[    14.550] 	WinASegment: 0xa000
[    14.550] 	WinBSegment: 0x0
[    14.550] 	WinFuncPtr: 0xc00051ab
[    14.550] 	BytesPerScanline: 2304
[    14.550] 	XResolution: 1152
[    14.550] 	YResolution: 864
[    14.550] 	XCharSize: 8
[    14.550] 	YCharSize: 16
[    14.550] 	NumberOfPlanes: 1
[    14.550] 	BitsPerPixel: 16
[    14.550] 	NumberOfBanks: 1
[    14.550] 	MemoryModel: 6
[    14.550] 	BankSize: 0
[    14.550] 	NumberOfImages: 7
[    14.550] 	RedMaskSize: 5
[    14.550] 	RedFieldPosition: 11
[    14.550] 	GreenMaskSize: 6
[    14.550] 	GreenFieldPosition: 5
[    14.550] 	BlueMaskSize: 5
[    14.550] 	BlueFieldPosition: 0
[    14.550] 	RsvdMaskSize: 0
[    14.550] 	RsvdFieldPosition: 0
[    14.550] 	DirectColorModeInfo: 0
[    14.550] 	PhysBasePtr: 0xd0000000
[    14.550] 	LinBytesPerScanLine: 2304
[    14.550] 	BnkNumberOfImagePages: 7
[    14.550] 	LinNumberOfImagePages: 7
[    14.550] 	LinRedMaskSize: 5
[    14.550] 	LinRedFieldPosition: 11
[    14.550] 	LinGreenMaskSize: 6
[    14.550] 	LinGreenFieldPosition: 5
[    14.550] 	LinBlueMaskSize: 5
[    14.550] 	LinBlueFieldPosition: 0
[    14.550] 	LinRsvdMaskSize: 0
[    14.550] 	LinRsvdFieldPosition: 0
[    14.550] 	MaxPixelClock: 400000000
[    14.551] *Mode: 156 (1152x864)
[    14.551] 	ModeAttributes: 0xbb
[    14.551] 	WinAAttributes: 0x7
[    14.551] 	WinBAttributes: 0x0
[    14.551] 	WinGranularity: 64
[    14.551] 	WinSize: 64
[    14.551] 	WinASegment: 0xa000
[    14.551] 	WinBSegment: 0x0
[    14.551] 	WinFuncPtr: 0xc00051ab
[    14.551] 	BytesPerScanline: 4608
[    14.551] 	XResolution: 1152
[    14.551] 	YResolution: 864
[    14.551] 	XCharSize: 8
[    14.551] 	YCharSize: 16
[    14.551] 	NumberOfPlanes: 1
[    14.551] 	BitsPerPixel: 32
[    14.551] 	NumberOfBanks: 1
[    14.551] 	MemoryModel: 6
[    14.551] 	BankSize: 0
[    14.551] 	NumberOfImages: 3
[    14.551] 	RedMaskSize: 8
[    14.551] 	RedFieldPosition: 16
[    14.551] 	GreenMaskSize: 8
[    14.551] 	GreenFieldPosition: 8
[    14.551] 	BlueMaskSize: 8
[    14.551] 	BlueFieldPosition: 0
[    14.551] 	RsvdMaskSize: 0
[    14.551] 	RsvdFieldPosition: 0
[    14.551] 	DirectColorModeInfo: 0
[    14.551] 	PhysBasePtr: 0xd0000000
[    14.551] 	LinBytesPerScanLine: 4608
[    14.551] 	BnkNumberOfImagePages: 3
[    14.551] 	LinNumberOfImagePages: 3
[    14.551] 	LinRedMaskSize: 8
[    14.551] 	LinRedFieldPosition: 16
[    14.551] 	LinGreenMaskSize: 8
[    14.551] 	LinGreenFieldPosition: 8
[    14.551] 	LinBlueMaskSize: 8
[    14.551] 	LinBlueFieldPosition: 0
[    14.551] 	LinRsvdMaskSize: 0
[    14.551] 	LinRsvdFieldPosition: 0
[    14.551] 	MaxPixelClock: 400000000
[    14.552] Mode: 163 (1280x960)
[    14.552] 	ModeAttributes: 0xbb
[    14.552] 	WinAAttributes: 0x7
[    14.552] 	WinBAttributes: 0x0
[    14.552] 	WinGranularity: 64
[    14.552] 	WinSize: 64
[    14.552] 	WinASegment: 0xa000
[    14.552] 	WinBSegment: 0x0
[    14.552] 	WinFuncPtr: 0xc00051ab
[    14.552] 	BytesPerScanline: 1280
[    14.552] 	XResolution: 1280
[    14.552] 	YResolution: 960
[    14.552] 	XCharSize: 8
[    14.552] 	YCharSize: 16
[    14.552] 	NumberOfPlanes: 1
[    14.552] 	BitsPerPixel: 8
[    14.552] 	NumberOfBanks: 1
[    14.552] 	MemoryModel: 4
[    14.552] 	BankSize: 0
[    14.553] 	NumberOfImages: 12
[    14.553] 	RedMaskSize: 0
[    14.553] 	RedFieldPosition: 0
[    14.553] 	GreenMaskSize: 0
[    14.553] 	GreenFieldPosition: 0
[    14.553] 	BlueMaskSize: 0
[    14.553] 	BlueFieldPosition: 0
[    14.553] 	RsvdMaskSize: 0
[    14.553] 	RsvdFieldPosition: 0
[    14.553] 	DirectColorModeInfo: 0
[    14.553] 	PhysBasePtr: 0xd0000000
[    14.553] 	LinBytesPerScanLine: 1280
[    14.553] 	BnkNumberOfImagePages: 12
[    14.553] 	LinNumberOfImagePages: 12
[    14.553] 	LinRedMaskSize: 0
[    14.553] 	LinRedFieldPosition: 0
[    14.553] 	LinGreenMaskSize: 0
[    14.553] 	LinGreenFieldPosition: 0
[    14.553] 	LinBlueMaskSize: 0
[    14.553] 	LinBlueFieldPosition: 0
[    14.553] 	LinRsvdMaskSize: 0
[    14.553] 	LinRsvdFieldPosition: 0
[    14.553] 	MaxPixelClock: 400000000
[    14.554] Mode: 165 (1280x960)
[    14.554] 	ModeAttributes: 0xbb
[    14.554] 	WinAAttributes: 0x7
[    14.554] 	WinBAttributes: 0x0
[    14.554] 	WinGranularity: 64
[    14.554] 	WinSize: 64
[    14.554] 	WinASegment: 0xa000
[    14.554] 	WinBSegment: 0x0
[    14.554] 	WinFuncPtr: 0xc00051ab
[    14.554] 	BytesPerScanline: 2560
[    14.554] 	XResolution: 1280
[    14.554] 	YResolution: 960
[    14.554] 	XCharSize: 8
[    14.554] 	YCharSize: 16
[    14.554] 	NumberOfPlanes: 1
[    14.554] 	BitsPerPixel: 16
[    14.554] 	NumberOfBanks: 1
[    14.554] 	MemoryModel: 6
[    14.554] 	BankSize: 0
[    14.554] 	NumberOfImages: 5
[    14.554] 	RedMaskSize: 5
[    14.554] 	RedFieldPosition: 11
[    14.554] 	GreenMaskSize: 6
[    14.554] 	GreenFieldPosition: 5
[    14.554] 	BlueMaskSize: 5
[    14.554] 	BlueFieldPosition: 0
[    14.554] 	RsvdMaskSize: 0
[    14.554] 	RsvdFieldPosition: 0
[    14.554] 	DirectColorModeInfo: 0
[    14.554] 	PhysBasePtr: 0xd0000000
[    14.554] 	LinBytesPerScanLine: 2560
[    14.554] 	BnkNumberOfImagePages: 5
[    14.554] 	LinNumberOfImagePages: 5
[    14.554] 	LinRedMaskSize: 5
[    14.554] 	LinRedFieldPosition: 11
[    14.554] 	LinGreenMaskSize: 6
[    14.554] 	LinGreenFieldPosition: 5
[    14.554] 	LinBlueMaskSize: 5
[    14.554] 	LinBlueFieldPosition: 0
[    14.554] 	LinRsvdMaskSize: 0
[    14.554] 	LinRsvdFieldPosition: 0
[    14.554] 	MaxPixelClock: 400000000
[    14.555] *Mode: 166 (1280x960)
[    14.555] 	ModeAttributes: 0xbb
[    14.555] 	WinAAttributes: 0x7
[    14.555] 	WinBAttributes: 0x0
[    14.555] 	WinGranularity: 64
[    14.555] 	WinSize: 64
[    14.555] 	WinASegment: 0xa000
[    14.555] 	WinBSegment: 0x0
[    14.555] 	WinFuncPtr: 0xc00051ab
[    14.555] 	BytesPerScanline: 5120
[    14.555] 	XResolution: 1280
[    14.555] 	YResolution: 960
[    14.555] 	XCharSize: 8
[    14.555] 	YCharSize: 16
[    14.555] 	NumberOfPlanes: 1
[    14.555] 	BitsPerPixel: 32
[    14.555] 	NumberOfBanks: 1
[    14.555] 	MemoryModel: 6
[    14.555] 	BankSize: 0
[    14.555] 	NumberOfImages: 2
[    14.555] 	RedMaskSize: 8
[    14.555] 	RedFieldPosition: 16
[    14.555] 	GreenMaskSize: 8
[    14.555] 	GreenFieldPosition: 8
[    14.555] 	BlueMaskSize: 8
[    14.555] 	BlueFieldPosition: 0
[    14.555] 	RsvdMaskSize: 0
[    14.555] 	RsvdFieldPosition: 0
[    14.555] 	DirectColorModeInfo: 0
[    14.555] 	PhysBasePtr: 0xd0000000
[    14.555] 	LinBytesPerScanLine: 5120
[    14.555] 	BnkNumberOfImagePages: 2
[    14.555] 	LinNumberOfImagePages: 2
[    14.555] 	LinRedMaskSize: 8
[    14.555] 	LinRedFieldPosition: 16
[    14.555] 	LinGreenMaskSize: 8
[    14.555] 	LinGreenFieldPosition: 8
[    14.555] 	LinBlueMaskSize: 8
[    14.555] 	LinBlueFieldPosition: 0
[    14.555] 	LinRsvdMaskSize: 0
[    14.555] 	LinRsvdFieldPosition: 0
[    14.555] 	MaxPixelClock: 400000000
[    14.557] *Mode: 121 (640x480)
[    14.557] 	ModeAttributes: 0xbb
[    14.557] 	WinAAttributes: 0x7
[    14.557] 	WinBAttributes: 0x0
[    14.557] 	WinGranularity: 64
[    14.557] 	WinSize: 64
[    14.557] 	WinASegment: 0xa000
[    14.557] 	WinBSegment: 0x0
[    14.557] 	WinFuncPtr: 0xc00051ab
[    14.557] 	BytesPerScanline: 2560
[    14.557] 	XResolution: 640
[    14.557] 	YResolution: 480
[    14.557] 	XCharSize: 8
[    14.557] 	YCharSize: 16
[    14.557] 	NumberOfPlanes: 1
[    14.557] 	BitsPerPixel: 32
[    14.557] 	NumberOfBanks: 1
[    14.557] 	MemoryModel: 6
[    14.557] 	BankSize: 0
[    14.557] 	NumberOfImages: 12
[    14.557] 	RedMaskSize: 8
[    14.557] 	RedFieldPosition: 16
[    14.557] 	GreenMaskSize: 8
[    14.557] 	GreenFieldPosition: 8
[    14.557] 	BlueMaskSize: 8
[    14.557] 	BlueFieldPosition: 0
[    14.557] 	RsvdMaskSize: 0
[    14.557] 	RsvdFieldPosition: 0
[    14.557] 	DirectColorModeInfo: 0
[    14.557] 	PhysBasePtr: 0xd0000000
[    14.557] 	LinBytesPerScanLine: 2560
[    14.557] 	BnkNumberOfImagePages: 12
[    14.557] 	LinNumberOfImagePages: 12
[    14.557] 	LinRedMaskSize: 8
[    14.557] 	LinRedFieldPosition: 16
[    14.557] 	LinGreenMaskSize: 8
[    14.557] 	LinGreenFieldPosition: 8
[    14.557] 	LinBlueMaskSize: 8
[    14.557] 	LinBlueFieldPosition: 0
[    14.557] 	LinRsvdMaskSize: 0
[    14.557] 	LinRsvdFieldPosition: 0
[    14.557] 	MaxPixelClock: 400000000
[    14.558] *Mode: 122 (800x600)
[    14.558] 	ModeAttributes: 0xbb
[    14.558] 	WinAAttributes: 0x7
[    14.558] 	WinBAttributes: 0x0
[    14.558] 	WinGranularity: 64
[    14.558] 	WinSize: 64
[    14.558] 	WinASegment: 0xa000
[    14.558] 	WinBSegment: 0x0
[    14.558] 	WinFuncPtr: 0xc00051ab
[    14.558] 	BytesPerScanline: 3200
[    14.558] 	XResolution: 800
[    14.558] 	YResolution: 600
[    14.558] 	XCharSize: 8
[    14.558] 	YCharSize: 14
[    14.558] 	NumberOfPlanes: 1
[    14.558] 	BitsPerPixel: 32
[    14.558] 	NumberOfBanks: 1
[    14.558] 	MemoryModel: 6
[    14.558] 	BankSize: 0
[    14.558] 	NumberOfImages: 7
[    14.558] 	RedMaskSize: 8
[    14.558] 	RedFieldPosition: 16
[    14.558] 	GreenMaskSize: 8
[    14.558] 	GreenFieldPosition: 8
[    14.558] 	BlueMaskSize: 8
[    14.558] 	BlueFieldPosition: 0
[    14.558] 	RsvdMaskSize: 0
[    14.558] 	RsvdFieldPosition: 0
[    14.558] 	DirectColorModeInfo: 0
[    14.558] 	PhysBasePtr: 0xd0000000
[    14.558] 	LinBytesPerScanLine: 3200
[    14.558] 	BnkNumberOfImagePages: 7
[    14.558] 	LinNumberOfImagePages: 7
[    14.558] 	LinRedMaskSize: 8
[    14.558] 	LinRedFieldPosition: 16
[    14.558] 	LinGreenMaskSize: 8
[    14.558] 	LinGreenFieldPosition: 8
[    14.559] 	LinBlueMaskSize: 8
[    14.559] 	LinBlueFieldPosition: 0
[    14.559] 	LinRsvdMaskSize: 0
[    14.559] 	LinRsvdFieldPosition: 0
[    14.559] 	MaxPixelClock: 400000000
[    14.560] *Mode: 123 (1024x768)
[    14.560] 	ModeAttributes: 0xbb
[    14.560] 	WinAAttributes: 0x7
[    14.560] 	WinBAttributes: 0x0
[    14.560] 	WinGranularity: 64
[    14.560] 	WinSize: 64
[    14.560] 	WinASegment: 0xa000
[    14.560] 	WinBSegment: 0x0
[    14.560] 	WinFuncPtr: 0xc00051ab
[    14.560] 	BytesPerScanline: 4096
[    14.560] 	XResolution: 1024
[    14.560] 	YResolution: 768
[    14.560] 	XCharSize: 8
[    14.560] 	YCharSize: 16
[    14.560] 	NumberOfPlanes: 1
[    14.560] 	BitsPerPixel: 32
[    14.560] 	NumberOfBanks: 1
[    14.560] 	MemoryModel: 6
[    14.560] 	BankSize: 0
[    14.560] 	NumberOfImages: 4
[    14.560] 	RedMaskSize: 8
[    14.560] 	RedFieldPosition: 16
[    14.560] 	GreenMaskSize: 8
[    14.560] 	GreenFieldPosition: 8
[    14.560] 	BlueMaskSize: 8
[    14.560] 	BlueFieldPosition: 0
[    14.560] 	RsvdMaskSize: 0
[    14.560] 	RsvdFieldPosition: 0
[    14.560] 	DirectColorModeInfo: 0
[    14.560] 	PhysBasePtr: 0xd0000000
[    14.560] 	LinBytesPerScanLine: 4096
[    14.560] 	BnkNumberOfImagePages: 4
[    14.560] 	LinNumberOfImagePages: 4
[    14.560] 	LinRedMaskSize: 8
[    14.560] 	LinRedFieldPosition: 16
[    14.560] 	LinGreenMaskSize: 8
[    14.560] 	LinGreenFieldPosition: 8
[    14.560] 	LinBlueMaskSize: 8
[    14.560] 	LinBlueFieldPosition: 0
[    14.560] 	LinRsvdMaskSize: 0
[    14.560] 	LinRsvdFieldPosition: 0
[    14.560] 	MaxPixelClock: 400000000
[    14.566] *Mode: 124 (1280x1024)
[    14.566] 	ModeAttributes: 0xbb
[    14.566] 	WinAAttributes: 0x7
[    14.566] 	WinBAttributes: 0x0
[    14.566] 	WinGranularity: 64
[    14.566] 	WinSize: 64
[    14.566] 	WinASegment: 0xa000
[    14.566] 	WinBSegment: 0x0
[    14.566] 	WinFuncPtr: 0xc00051ab
[    14.566] 	BytesPerScanline: 5120
[    14.566] 	XResolution: 1280
[    14.566] 	YResolution: 1024
[    14.566] 	XCharSize: 8
[    14.566] 	YCharSize: 16
[    14.566] 	NumberOfPlanes: 1
[    14.566] 	BitsPerPixel: 32
[    14.566] 	NumberOfBanks: 1
[    14.566] 	MemoryModel: 6
[    14.566] 	BankSize: 0
[    14.566] 	NumberOfImages: 2
[    14.566] 	RedMaskSize: 8
[    14.566] 	RedFieldPosition: 16
[    14.566] 	GreenMaskSize: 8
[    14.566] 	GreenFieldPosition: 8
[    14.566] 	BlueMaskSize: 8
[    14.566] 	BlueFieldPosition: 0
[    14.566] 	RsvdMaskSize: 0
[    14.566] 	RsvdFieldPosition: 0
[    14.566] 	DirectColorModeInfo: 0
[    14.566] 	PhysBasePtr: 0xd0000000
[    14.566] 	LinBytesPerScanLine: 5120
[    14.566] 	BnkNumberOfImagePages: 2
[    14.566] 	LinNumberOfImagePages: 2
[    14.566] 	LinRedMaskSize: 8
[    14.566] 	LinRedFieldPosition: 16
[    14.566] 	LinGreenMaskSize: 8
[    14.566] 	LinGreenFieldPosition: 8
[    14.566] 	LinBlueMaskSize: 8
[    14.566] 	LinBlueFieldPosition: 0
[    14.566] 	LinRsvdMaskSize: 0
[    14.566] 	LinRsvdFieldPosition: 0
[    14.566] 	MaxPixelClock: 400000000
[    14.568] Mode: 143 (1400x1050)
[    14.568] 	ModeAttributes: 0xbb
[    14.568] 	WinAAttributes: 0x7
[    14.568] 	WinBAttributes: 0x0
[    14.568] 	WinGranularity: 64
[    14.568] 	WinSize: 64
[    14.568] 	WinASegment: 0xa000
[    14.568] 	WinBSegment: 0x0
[    14.568] 	WinFuncPtr: 0xc00051ab
[    14.568] 	BytesPerScanline: 1408
[    14.568] 	XResolution: 1400
[    14.568] 	YResolution: 1050
[    14.568] 	XCharSize: 8
[    14.568] 	YCharSize: 16
[    14.568] 	NumberOfPlanes: 1
[    14.568] 	BitsPerPixel: 8
[    14.568] 	NumberOfBanks: 1
[    14.568] 	MemoryModel: 4
[    14.568] 	BankSize: 0
[    14.568] 	NumberOfImages: 10
[    14.568] 	RedMaskSize: 0
[    14.568] 	RedFieldPosition: 0
[    14.568] 	GreenMaskSize: 0
[    14.568] 	GreenFieldPosition: 0
[    14.568] 	BlueMaskSize: 0
[    14.568] 	BlueFieldPosition: 0
[    14.568] 	RsvdMaskSize: 0
[    14.568] 	RsvdFieldPosition: 0
[    14.568] 	DirectColorModeInfo: 0
[    14.568] 	PhysBasePtr: 0xd0000000
[    14.568] 	LinBytesPerScanLine: 1408
[    14.568] 	BnkNumberOfImagePages: 10
[    14.568] 	LinNumberOfImagePages: 10
[    14.568] 	LinRedMaskSize: 0
[    14.568] 	LinRedFieldPosition: 0
[    14.568] 	LinGreenMaskSize: 0
[    14.568] 	LinGreenFieldPosition: 0
[    14.568] 	LinBlueMaskSize: 0
[    14.568] 	LinBlueFieldPosition: 0
[    14.568] 	LinRsvdMaskSize: 0
[    14.568] 	LinRsvdFieldPosition: 0
[    14.568] 	MaxPixelClock: 400000000
[    14.571] Mode: 145 (1400x1050)
[    14.571] 	ModeAttributes: 0xbb
[    14.571] 	WinAAttributes: 0x7
[    14.571] 	WinBAttributes: 0x0
[    14.571] 	WinGranularity: 64
[    14.571] 	WinSize: 64
[    14.571] 	WinASegment: 0xa000
[    14.571] 	WinBSegment: 0x0
[    14.571] 	WinFuncPtr: 0xc00051ab
[    14.571] 	BytesPerScanline: 2816
[    14.571] 	XResolution: 1400
[    14.571] 	YResolution: 1050
[    14.571] 	XCharSize: 8
[    14.571] 	YCharSize: 16
[    14.572] 	NumberOfPlanes: 1
[    14.572] 	BitsPerPixel: 16
[    14.572] 	NumberOfBanks: 1
[    14.572] 	MemoryModel: 6
[    14.572] 	BankSize: 0
[    14.572] 	NumberOfImages: 4
[    14.572] 	RedMaskSize: 5
[    14.572] 	RedFieldPosition: 11
[    14.572] 	GreenMaskSize: 6
[    14.572] 	GreenFieldPosition: 5
[    14.572] 	BlueMaskSize: 5
[    14.572] 	BlueFieldPosition: 0
[    14.572] 	RsvdMaskSize: 0
[    14.572] 	RsvdFieldPosition: 0
[    14.572] 	DirectColorModeInfo: 0
[    14.572] 	PhysBasePtr: 0xd0000000
[    14.572] 	LinBytesPerScanLine: 2816
[    14.572] 	BnkNumberOfImagePages: 4
[    14.572] 	LinNumberOfImagePages: 4
[    14.572] 	LinRedMaskSize: 5
[    14.572] 	LinRedFieldPosition: 11
[    14.572] 	LinGreenMaskSize: 6
[    14.572] 	LinGreenFieldPosition: 5
[    14.572] 	LinBlueMaskSize: 5
[    14.572] 	LinBlueFieldPosition: 0
[    14.572] 	LinRsvdMaskSize: 0
[    14.572] 	LinRsvdFieldPosition: 0
[    14.572] 	MaxPixelClock: 400000000
[    14.574] *Mode: 146 (1400x1050)
[    14.574] 	ModeAttributes: 0xbb
[    14.574] 	WinAAttributes: 0x7
[    14.574] 	WinBAttributes: 0x0
[    14.574] 	WinGranularity: 64
[    14.574] 	WinSize: 64
[    14.574] 	WinASegment: 0xa000
[    14.574] 	WinBSegment: 0x0
[    14.574] 	WinFuncPtr: 0xc00051ab
[    14.574] 	BytesPerScanline: 5632
[    14.574] 	XResolution: 1400
[    14.574] 	YResolution: 1050
[    14.574] 	XCharSize: 8
[    14.574] 	YCharSize: 16
[    14.574] 	NumberOfPlanes: 1
[    14.574] 	BitsPerPixel: 32
[    14.574] 	NumberOfBanks: 1
[    14.574] 	MemoryModel: 6
[    14.574] 	BankSize: 0
[    14.574] 	NumberOfImages: 1
[    14.574] 	RedMaskSize: 8
[    14.574] 	RedFieldPosition: 16
[    14.574] 	GreenMaskSize: 8
[    14.574] 	GreenFieldPosition: 8
[    14.574] 	BlueMaskSize: 8
[    14.574] 	BlueFieldPosition: 0
[    14.574] 	RsvdMaskSize: 0
[    14.574] 	RsvdFieldPosition: 0
[    14.574] 	DirectColorModeInfo: 0
[    14.574] 	PhysBasePtr: 0xd0000000
[    14.574] 	LinBytesPerScanLine: 5632
[    14.574] 	BnkNumberOfImagePages: 1
[    14.574] 	LinNumberOfImagePages: 1
[    14.574] 	LinRedMaskSize: 8
[    14.574] 	LinRedFieldPosition: 16
[    14.574] 	LinGreenMaskSize: 8
[    14.574] 	LinGreenFieldPosition: 8
[    14.574] 	LinBlueMaskSize: 8
[    14.574] 	LinBlueFieldPosition: 0
[    14.574] 	LinRsvdMaskSize: 0
[    14.574] 	LinRsvdFieldPosition: 0
[    14.574] 	MaxPixelClock: 400000000
[    14.581] Mode: 173 (1600x1200)
[    14.581] 	ModeAttributes: 0xba
[    14.581] 	WinAAttributes: 0x7
[    14.581] 	WinBAttributes: 0x0
[    14.581] 	WinGranularity: 64
[    14.581] 	WinSize: 64
[    14.581] 	WinASegment: 0xa000
[    14.581] 	WinBSegment: 0x0
[    14.581] 	WinFuncPtr: 0xc00051ab
[    14.581] 	BytesPerScanline: 1600
[    14.581] 	XResolution: 1600
[    14.581] 	YResolution: 1200
[    14.581] 	XCharSize: 8
[    14.581] 	YCharSize: 16
[    14.581] 	NumberOfPlanes: 1
[    14.581] 	BitsPerPixel: 8
[    14.581] 	NumberOfBanks: 1
[    14.581] 	MemoryModel: 4
[    14.581] 	BankSize: 0
[    14.581] 	NumberOfImages: 7
[    14.581] 	RedMaskSize: 0
[    14.581] 	RedFieldPosition: 0
[    14.581] 	GreenMaskSize: 0
[    14.581] 	GreenFieldPosition: 0
[    14.581] 	BlueMaskSize: 0
[    14.581] 	BlueFieldPosition: 0
[    14.581] 	RsvdMaskSize: 0
[    14.581] 	RsvdFieldPosition: 0
[    14.581] 	DirectColorModeInfo: 0
[    14.581] 	PhysBasePtr: 0xd0000000
[    14.581] 	LinBytesPerScanLine: 1600
[    14.581] 	BnkNumberOfImagePages: 7
[    14.581] 	LinNumberOfImagePages: 7
[    14.581] 	LinRedMaskSize: 0
[    14.581] 	LinRedFieldPosition: 0
[    14.581] 	LinGreenMaskSize: 0
[    14.581] 	LinGreenFieldPosition: 0
[    14.581] 	LinBlueMaskSize: 0
[    14.581] 	LinBlueFieldPosition: 0
[    14.581] 	LinRsvdMaskSize: 0
[    14.581] 	LinRsvdFieldPosition: 0
[    14.581] 	MaxPixelClock: 400000000
[    14.583] Mode: 175 (1600x1200)
[    14.583] 	ModeAttributes: 0xba
[    14.583] 	WinAAttributes: 0x7
[    14.583] 	WinBAttributes: 0x0
[    14.583] 	WinGranularity: 64
[    14.583] 	WinSize: 64
[    14.583] 	WinASegment: 0xa000
[    14.583] 	WinBSegment: 0x0
[    14.583] 	WinFuncPtr: 0xc00051ab
[    14.583] 	BytesPerScanline: 3200
[    14.583] 	XResolution: 1600
[    14.583] 	YResolution: 1200
[    14.583] 	XCharSize: 8
[    14.583] 	YCharSize: 16
[    14.583] 	NumberOfPlanes: 1
[    14.583] 	BitsPerPixel: 16
[    14.583] 	NumberOfBanks: 1
[    14.583] 	MemoryModel: 6
[    14.583] 	BankSize: 0
[    14.583] 	NumberOfImages: 3
[    14.583] 	RedMaskSize: 5
[    14.583] 	RedFieldPosition: 11
[    14.583] 	GreenMaskSize: 6
[    14.583] 	GreenFieldPosition: 5
[    14.583] 	BlueMaskSize: 5
[    14.583] 	BlueFieldPosition: 0
[    14.583] 	RsvdMaskSize: 0
[    14.583] 	RsvdFieldPosition: 0
[    14.583] 	DirectColorModeInfo: 0
[    14.583] 	PhysBasePtr: 0xd0000000
[    14.583] 	LinBytesPerScanLine: 3200
[    14.583] 	BnkNumberOfImagePages: 3
[    14.583] 	LinNumberOfImagePages: 3
[    14.583] 	LinRedMaskSize: 5
[    14.583] 	LinRedFieldPosition: 11
[    14.583] 	LinGreenMaskSize: 6
[    14.583] 	LinGreenFieldPosition: 5
[    14.583] 	LinBlueMaskSize: 5
[    14.583] 	LinBlueFieldPosition: 0
[    14.583] 	LinRsvdMaskSize: 0
[    14.583] 	LinRsvdFieldPosition: 0
[    14.583] 	MaxPixelClock: 400000000
[    14.585] Mode: 176 (1600x1200)
[    14.585] 	ModeAttributes: 0xba
[    14.585] 	WinAAttributes: 0x7
[    14.585] 	WinBAttributes: 0x0
[    14.585] 	WinGranularity: 64
[    14.585] 	WinSize: 64
[    14.585] 	WinASegment: 0xa000
[    14.585] 	WinBSegment: 0x0
[    14.585] 	WinFuncPtr: 0xc00051ab
[    14.585] 	BytesPerScanline: 6400
[    14.585] 	XResolution: 1600
[    14.586] 	YResolution: 1200
[    14.586] 	XCharSize: 8
[    14.586] 	YCharSize: 16
[    14.586] 	NumberOfPlanes: 1
[    14.586] 	BitsPerPixel: 32
[    14.586] 	NumberOfBanks: 1
[    14.586] 	MemoryModel: 6
[    14.586] 	BankSize: 0
[    14.586] 	NumberOfImages: 1
[    14.586] 	RedMaskSize: 8
[    14.586] 	RedFieldPosition: 16
[    14.586] 	GreenMaskSize: 8
[    14.586] 	GreenFieldPosition: 8
[    14.586] 	BlueMaskSize: 8
[    14.586] 	BlueFieldPosition: 0
[    14.586] 	RsvdMaskSize: 0
[    14.586] 	RsvdFieldPosition: 0
[    14.586] 	DirectColorModeInfo: 0
[    14.586] 	PhysBasePtr: 0xd0000000
[    14.586] 	LinBytesPerScanLine: 6400
[    14.586] 	BnkNumberOfImagePages: 1
[    14.586] 	LinNumberOfImagePages: 1
[    14.586] 	LinRedMaskSize: 8
[    14.586] 	LinRedFieldPosition: 16
[    14.586] 	LinGreenMaskSize: 8
[    14.586] 	LinGreenFieldPosition: 8
[    14.586] 	LinBlueMaskSize: 8
[    14.586] 	LinBlueFieldPosition: 0
[    14.586] 	LinRsvdMaskSize: 0
[    14.586] 	LinRsvdFieldPosition: 0
[    14.586] 	MaxPixelClock: 400000000
[    14.588] Mode: 183 (1792x1344)
[    14.588] 	ModeAttributes: 0xba
[    14.588] 	WinAAttributes: 0x7
[    14.588] 	WinBAttributes: 0x0
[    14.588] 	WinGranularity: 64
[    14.588] 	WinSize: 64
[    14.588] 	WinASegment: 0xa000
[    14.588] 	WinBSegment: 0x0
[    14.588] 	WinFuncPtr: 0xc00051ab
[    14.588] 	BytesPerScanline: 1792
[    14.588] 	XResolution: 1792
[    14.588] 	YResolution: 1344
[    14.588] 	XCharSize: 8
[    14.588] 	YCharSize: 16
[    14.588] 	NumberOfPlanes: 1
[    14.588] 	BitsPerPixel: 8
[    14.588] 	NumberOfBanks: 1
[    14.588] 	MemoryModel: 4
[    14.588] 	BankSize: 0
[    14.588] 	NumberOfImages: 5
[    14.588] 	RedMaskSize: 0
[    14.588] 	RedFieldPosition: 0
[    14.588] 	GreenMaskSize: 0
[    14.588] 	GreenFieldPosition: 0
[    14.588] 	BlueMaskSize: 0
[    14.588] 	BlueFieldPosition: 0
[    14.588] 	RsvdMaskSize: 0
[    14.588] 	RsvdFieldPosition: 0
[    14.588] 	DirectColorModeInfo: 0
[    14.588] 	PhysBasePtr: 0xd0000000
[    14.588] 	LinBytesPerScanLine: 1792
[    14.588] 	BnkNumberOfImagePages: 5
[    14.588] 	LinNumberOfImagePages: 5
[    14.588] 	LinRedMaskSize: 0
[    14.588] 	LinRedFieldPosition: 0
[    14.588] 	LinGreenMaskSize: 0
[    14.588] 	LinGreenFieldPosition: 0
[    14.588] 	LinBlueMaskSize: 0
[    14.588] 	LinBlueFieldPosition: 0
[    14.588] 	LinRsvdMaskSize: 0
[    14.588] 	LinRsvdFieldPosition: 0
[    14.588] 	MaxPixelClock: 400000000
[    14.590] Mode: 185 (1792x1344)
[    14.590] 	ModeAttributes: 0xba
[    14.590] 	WinAAttributes: 0x7
[    14.590] 	WinBAttributes: 0x0
[    14.590] 	WinGranularity: 64
[    14.590] 	WinSize: 64
[    14.590] 	WinASegment: 0xa000
[    14.590] 	WinBSegment: 0x0
[    14.590] 	WinFuncPtr: 0xc00051ab
[    14.590] 	BytesPerScanline: 3584
[    14.590] 	XResolution: 1792
[    14.590] 	YResolution: 1344
[    14.590] 	XCharSize: 8
[    14.590] 	YCharSize: 16
[    14.590] 	NumberOfPlanes: 1
[    14.590] 	BitsPerPixel: 16
[    14.590] 	NumberOfBanks: 1
[    14.590] 	MemoryModel: 6
[    14.590] 	BankSize: 0
[    14.590] 	NumberOfImages: 2
[    14.590] 	RedMaskSize: 5
[    14.590] 	RedFieldPosition: 11
[    14.590] 	GreenMaskSize: 6
[    14.590] 	GreenFieldPosition: 5
[    14.590] 	BlueMaskSize: 5
[    14.590] 	BlueFieldPosition: 0
[    14.590] 	RsvdMaskSize: 0
[    14.590] 	RsvdFieldPosition: 0
[    14.590] 	DirectColorModeInfo: 0
[    14.590] 	PhysBasePtr: 0xd0000000
[    14.590] 	LinBytesPerScanLine: 3584
[    14.590] 	BnkNumberOfImagePages: 2
[    14.590] 	LinNumberOfImagePages: 2
[    14.590] 	LinRedMaskSize: 5
[    14.590] 	LinRedFieldPosition: 11
[    14.590] 	LinGreenMaskSize: 6
[    14.590] 	LinGreenFieldPosition: 5
[    14.590] 	LinBlueMaskSize: 5
[    14.590] 	LinBlueFieldPosition: 0
[    14.590] 	LinRsvdMaskSize: 0
[    14.590] 	LinRsvdFieldPosition: 0
[    14.590] 	MaxPixelClock: 400000000
[    14.592] Mode: 186 (1792x1344)
[    14.592] 	ModeAttributes: 0xba
[    14.592] 	WinAAttributes: 0x7
[    14.592] 	WinBAttributes: 0x0
[    14.592] 	WinGranularity: 64
[    14.592] 	WinSize: 64
[    14.592] 	WinASegment: 0xa000
[    14.592] 	WinBSegment: 0x0
[    14.592] 	WinFuncPtr: 0xc00051ab
[    14.592] 	BytesPerScanline: 7168
[    14.592] 	XResolution: 1792
[    14.592] 	YResolution: 1344
[    14.592] 	XCharSize: 8
[    14.592] 	YCharSize: 16
[    14.592] 	NumberOfPlanes: 1
[    14.592] 	BitsPerPixel: 32
[    14.592] 	NumberOfBanks: 1
[    14.592] 	MemoryModel: 6
[    14.592] 	BankSize: 0
[    14.592] 	NumberOfImages: 1
[    14.592] 	RedMaskSize: 8
[    14.592] 	RedFieldPosition: 16
[    14.592] 	GreenMaskSize: 8
[    14.592] 	GreenFieldPosition: 8
[    14.592] 	BlueMaskSize: 8
[    14.592] 	BlueFieldPosition: 0
[    14.592] 	RsvdMaskSize: 0
[    14.592] 	RsvdFieldPosition: 0
[    14.592] 	DirectColorModeInfo: 0
[    14.592] 	PhysBasePtr: 0xd0000000
[    14.592] 	LinBytesPerScanLine: 7168
[    14.593] 	BnkNumberOfImagePages: 1
[    14.593] 	LinNumberOfImagePages: 1
[    14.593] 	LinRedMaskSize: 8
[    14.593] 	LinRedFieldPosition: 16
[    14.593] 	LinGreenMaskSize: 8
[    14.593] 	LinGreenFieldPosition: 8
[    14.593] 	LinBlueMaskSize: 8
[    14.593] 	LinBlueFieldPosition: 0
[    14.593] 	LinRsvdMaskSize: 0
[    14.593] 	LinRsvdFieldPosition: 0
[    14.593] 	MaxPixelClock: 400000000
[    14.595] Mode: 1d3 (1856x1392)
[    14.595] 	ModeAttributes: 0xba
[    14.595] 	WinAAttributes: 0x7
[    14.595] 	WinBAttributes: 0x0
[    14.595] 	WinGranularity: 64
[    14.595] 	WinSize: 64
[    14.595] 	WinASegment: 0xa000
[    14.595] 	WinBSegment: 0x0
[    14.595] 	WinFuncPtr: 0xc00051ab
[    14.595] 	BytesPerScanline: 1856
[    14.595] 	XResolution: 1856
[    14.595] 	YResolution: 1392
[    14.595] 	XCharSize: 8
[    14.595] 	YCharSize: 16
[    14.595] 	NumberOfPlanes: 1
[    14.595] 	BitsPerPixel: 8
[    14.595] 	NumberOfBanks: 1
[    14.595] 	MemoryModel: 4
[    14.595] 	BankSize: 0
[    14.595] 	NumberOfImages: 5
[    14.595] 	RedMaskSize: 0
[    14.595] 	RedFieldPosition: 0
[    14.595] 	GreenMaskSize: 0
[    14.595] 	GreenFieldPosition: 0
[    14.595] 	BlueMaskSize: 0
[    14.595] 	BlueFieldPosition: 0
[    14.595] 	RsvdMaskSize: 0
[    14.595] 	RsvdFieldPosition: 0
[    14.595] 	DirectColorModeInfo: 0
[    14.595] 	PhysBasePtr: 0xd0000000
[    14.595] 	LinBytesPerScanLine: 1856
[    14.595] 	BnkNumberOfImagePages: 5
[    14.595] 	LinNumberOfImagePages: 5
[    14.595] 	LinRedMaskSize: 0
[    14.595] 	LinRedFieldPosition: 0
[    14.595] 	LinGreenMaskSize: 0
[    14.595] 	LinGreenFieldPosition: 0
[    14.595] 	LinBlueMaskSize: 0
[    14.595] 	LinBlueFieldPosition: 0
[    14.595] 	LinRsvdMaskSize: 0
[    14.595] 	LinRsvdFieldPosition: 0
[    14.595] 	MaxPixelClock: 400000000
[    14.597] Mode: 1d5 (1856x1392)
[    14.597] 	ModeAttributes: 0xba
[    14.597] 	WinAAttributes: 0x7
[    14.597] 	WinBAttributes: 0x0
[    14.597] 	WinGranularity: 64
[    14.597] 	WinSize: 64
[    14.597] 	WinASegment: 0xa000
[    14.597] 	WinBSegment: 0x0
[    14.597] 	WinFuncPtr: 0xc00051ab
[    14.597] 	BytesPerScanline: 3712
[    14.597] 	XResolution: 1856
[    14.597] 	YResolution: 1392
[    14.597] 	XCharSize: 8
[    14.597] 	YCharSize: 16
[    14.597] 	NumberOfPlanes: 1
[    14.597] 	BitsPerPixel: 16
[    14.597] 	NumberOfBanks: 1
[    14.597] 	MemoryModel: 6
[    14.597] 	BankSize: 0
[    14.597] 	NumberOfImages: 2
[    14.597] 	RedMaskSize: 5
[    14.597] 	RedFieldPosition: 11
[    14.597] 	GreenMaskSize: 6
[    14.597] 	GreenFieldPosition: 5
[    14.597] 	BlueMaskSize: 5
[    14.597] 	BlueFieldPosition: 0
[    14.597] 	RsvdMaskSize: 0
[    14.597] 	RsvdFieldPosition: 0
[    14.597] 	DirectColorModeInfo: 0
[    14.597] 	PhysBasePtr: 0xd0000000
[    14.597] 	LinBytesPerScanLine: 3712
[    14.597] 	BnkNumberOfImagePages: 2
[    14.597] 	LinNumberOfImagePages: 2
[    14.597] 	LinRedMaskSize: 5
[    14.597] 	LinRedFieldPosition: 11
[    14.597] 	LinGreenMaskSize: 6
[    14.597] 	LinGreenFieldPosition: 5
[    14.597] 	LinBlueMaskSize: 5
[    14.597] 	LinBlueFieldPosition: 0
[    14.597] 	LinRsvdMaskSize: 0
[    14.597] 	LinRsvdFieldPosition: 0
[    14.597] 	MaxPixelClock: 400000000
[    14.599] Mode: 1d6 (1856x1392)
[    14.599] 	ModeAttributes: 0xba
[    14.599] 	WinAAttributes: 0x7
[    14.599] 	WinBAttributes: 0x0
[    14.599] 	WinGranularity: 64
[    14.599] 	WinSize: 64
[    14.599] 	WinASegment: 0xa000
[    14.599] 	WinBSegment: 0x0
[    14.599] 	WinFuncPtr: 0xc00051ab
[    14.599] 	BytesPerScanline: 7424
[    14.599] 	XResolution: 1856
[    14.599] 	YResolution: 1392
[    14.599] 	XCharSize: 8
[    14.599] 	YCharSize: 16
[    14.599] 	NumberOfPlanes: 1
[    14.599] 	BitsPerPixel: 32
[    14.599] 	NumberOfBanks: 1
[    14.599] 	MemoryModel: 6
[    14.599] 	BankSize: 0
[    14.599] 	NumberOfImages: 1
[    14.599] 	RedMaskSize: 8
[    14.599] 	RedFieldPosition: 16
[    14.599] 	GreenMaskSize: 8
[    14.599] 	GreenFieldPosition: 8
[    14.599] 	BlueMaskSize: 8
[    14.599] 	BlueFieldPosition: 0
[    14.599] 	RsvdMaskSize: 0
[    14.599] 	RsvdFieldPosition: 0
[    14.599] 	DirectColorModeInfo: 0
[    14.599] 	PhysBasePtr: 0xd0000000
[    14.599] 	LinBytesPerScanLine: 7424
[    14.599] 	BnkNumberOfImagePages: 1
[    14.599] 	LinNumberOfImagePages: 1
[    14.599] 	LinRedMaskSize: 8
[    14.599] 	LinRedFieldPosition: 16
[    14.599] 	LinGreenMaskSize: 8
[    14.599] 	LinGreenFieldPosition: 8
[    14.599] 	LinBlueMaskSize: 8
[    14.599] 	LinBlueFieldPosition: 0
[    14.599] 	LinRsvdMaskSize: 0
[    14.599] 	LinRsvdFieldPosition: 0
[    14.599] 	MaxPixelClock: 400000000
[    14.601] Mode: 1e3 (1920x1440)
[    14.601] 	ModeAttributes: 0xba
[    14.601] 	WinAAttributes: 0x7
[    14.601] 	WinBAttributes: 0x0
[    14.601] 	WinGranularity: 64
[    14.601] 	WinSize: 64
[    14.601] 	WinASegment: 0xa000
[    14.601] 	WinBSegment: 0x0
[    14.601] 	WinFuncPtr: 0xc00051ab
[    14.601] 	BytesPerScanline: 1920
[    14.601] 	XResolution: 1920
[    14.601] 	YResolution: 1440
[    14.601] 	XCharSize: 8
[    14.601] 	YCharSize: 16
[    14.601] 	NumberOfPlanes: 1
[    14.601] 	BitsPerPixel: 8
[    14.601] 	NumberOfBanks: 1
[    14.601] 	MemoryModel: 4
[    14.601] 	BankSize: 0
[    14.601] 	NumberOfImages: 4
[    14.601] 	RedMaskSize: 0
[    14.601] 	RedFieldPosition: 0
[    14.601] 	GreenMaskSize: 0
[    14.601] 	GreenFieldPosition: 0
[    14.601] 	BlueMaskSize: 0
[    14.601] 	BlueFieldPosition: 0
[    14.601] 	RsvdMaskSize: 0
[    14.601] 	RsvdFieldPosition: 0
[    14.601] 	DirectColorModeInfo: 0
[    14.601] 	PhysBasePtr: 0xd0000000
[    14.601] 	LinBytesPerScanLine: 1920
[    14.601] 	BnkNumberOfImagePages: 4
[    14.601] 	LinNumberOfImagePages: 4
[    14.601] 	LinRedMaskSize: 0
[    14.601] 	LinRedFieldPosition: 0
[    14.601] 	LinGreenMaskSize: 0
[    14.601] 	LinGreenFieldPosition: 0
[    14.601] 	LinBlueMaskSize: 0
[    14.601] 	LinBlueFieldPosition: 0
[    14.601] 	LinRsvdMaskSize: 0
[    14.601] 	LinRsvdFieldPosition: 0
[    14.601] 	MaxPixelClock: 400000000
[    14.603] Mode: 1e5 (1920x1440)
[    14.603] 	ModeAttributes: 0xba
[    14.603] 	WinAAttributes: 0x7
[    14.603] 	WinBAttributes: 0x0
[    14.603] 	WinGranularity: 64
[    14.603] 	WinSize: 64
[    14.603] 	WinASegment: 0xa000
[    14.603] 	WinBSegment: 0x0
[    14.603] 	WinFuncPtr: 0xc00051ab
[    14.603] 	BytesPerScanline: 3840
[    14.604] 	XResolution: 1920
[    14.604] 	YResolution: 1440
[    14.604] 	XCharSize: 8
[    14.604] 	YCharSize: 16
[    14.604] 	NumberOfPlanes: 1
[    14.604] 	BitsPerPixel: 16
[    14.604] 	NumberOfBanks: 1
[    14.604] 	MemoryModel: 6
[    14.604] 	BankSize: 0
[    14.604] 	NumberOfImages: 2
[    14.604] 	RedMaskSize: 5
[    14.604] 	RedFieldPosition: 11
[    14.604] 	GreenMaskSize: 6
[    14.604] 	GreenFieldPosition: 5
[    14.604] 	BlueMaskSize: 5
[    14.604] 	BlueFieldPosition: 0
[    14.604] 	RsvdMaskSize: 0
[    14.604] 	RsvdFieldPosition: 0
[    14.604] 	DirectColorModeInfo: 0
[    14.604] 	PhysBasePtr: 0xd0000000
[    14.604] 	LinBytesPerScanLine: 3840
[    14.604] 	BnkNumberOfImagePages: 2
[    14.604] 	LinNumberOfImagePages: 2
[    14.604] 	LinRedMaskSize: 5
[    14.604] 	LinRedFieldPosition: 11
[    14.604] 	LinGreenMaskSize: 6
[    14.604] 	LinGreenFieldPosition: 5
[    14.604] 	LinBlueMaskSize: 5
[    14.604] 	LinBlueFieldPosition: 0
[    14.604] 	LinRsvdMaskSize: 0
[    14.604] 	LinRsvdFieldPosition: 0
[    14.604] 	MaxPixelClock: 400000000
[    14.606] Mode: 1e6 (1920x1440)
[    14.606] 	ModeAttributes: 0xba
[    14.606] 	WinAAttributes: 0x7
[    14.606] 	WinBAttributes: 0x0
[    14.606] 	WinGranularity: 64
[    14.606] 	WinSize: 64
[    14.606] 	WinASegment: 0xa000
[    14.606] 	WinBSegment: 0x0
[    14.606] 	WinFuncPtr: 0xc00051ab
[    14.606] 	BytesPerScanline: 7680
[    14.606] 	XResolution: 1920
[    14.606] 	YResolution: 1440
[    14.606] 	XCharSize: 8
[    14.606] 	YCharSize: 16
[    14.606] 	NumberOfPlanes: 1
[    14.606] 	BitsPerPixel: 32
[    14.606] 	NumberOfBanks: 1
[    14.606] 	MemoryModel: 6
[    14.606] 	BankSize: 0
[    14.606] 	NumberOfImages: 1
[    14.606] 	RedMaskSize: 8
[    14.606] 	RedFieldPosition: 16
[    14.606] 	GreenMaskSize: 8
[    14.606] 	GreenFieldPosition: 8
[    14.606] 	BlueMaskSize: 8
[    14.606] 	BlueFieldPosition: 0
[    14.606] 	RsvdMaskSize: 0
[    14.606] 	RsvdFieldPosition: 0
[    14.606] 	DirectColorModeInfo: 0
[    14.606] 	PhysBasePtr: 0xd0000000
[    14.606] 	LinBytesPerScanLine: 7680
[    14.606] 	BnkNumberOfImagePages: 1
[    14.606] 	LinNumberOfImagePages: 1
[    14.606] 	LinRedMaskSize: 8
[    14.606] 	LinRedFieldPosition: 16
[    14.606] 	LinGreenMaskSize: 8
[    14.606] 	LinGreenFieldPosition: 8
[    14.606] 	LinBlueMaskSize: 8
[    14.606] 	LinBlueFieldPosition: 0
[    14.606] 	LinRsvdMaskSize: 0
[    14.606] 	LinRsvdFieldPosition: 0
[    14.606] 	MaxPixelClock: 400000000
[    14.606] 
[    14.606] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[    14.606] (II) VESA(0): <default monitor>: Using hsync range of 24.00-94.00 kHz
[    14.606] (II) VESA(0): <default monitor>: Using vrefresh range of 48.00-76.00 Hz
[    14.606] (II) VESA(0): <default monitor>: Using maximum pixel clock of 175.00 MHz
[    14.606] (WW) VESA(0): Unable to estimate virtual size
[    14.606] (II) VESA(0): Not using built-in mode "1400x1050" (no mode of this name)
[    14.606] (II) VESA(0): Not using built-in mode "1152x864" (no mode of this name)
[    14.607] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[    14.607] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[    14.607] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    14.607] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    14.607] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[    14.607] (**) VESA(0): *Built-in mode "1280x1024"
[    14.607] (**) VESA(0): *Built-in mode "1280x960"
[    14.607] (**) VESA(0): *Built-in mode "1024x768"
[    14.607] (**) VESA(0): *Built-in mode "800x600"
[    14.607] (**) VESA(0): *Built-in mode "640x480"
[    14.607] (**) VESA(0): *Built-in mode "720x400"
[    14.607] (**) VESA(0): Display dimensions: (510, 290) mm
[    14.607] (**) VESA(0): DPI set to (63, 89)
[    14.607] (**) VESA(0): Using "Shadow Framebuffer"
[    14.607] (II) Loading sub module "shadow"
[    14.607] (II) LoadModule: "shadow"
[    14.607] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    14.608] (II) Module shadow: vendor="X.Org Foundation"
[    14.608] 	compiled for 1.10.0, module version = 1.1.0
[    14.608] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.608] (II) Loading sub module "fb"
[    14.608] (II) LoadModule: "fb"
[    14.608] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.608] (II) Module fb: vendor="X.Org Foundation"
[    14.608] 	compiled for 1.10.0, module version = 1.0.0
[    14.608] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.608] (II) UnloadModule: "radeon"
[    14.608] (II) Unloading radeon
[    14.608] (II) UnloadModule: "fbdev"
[    14.608] (II) Unloading fbdev
[    14.608] (II) UnloadModule: "fbdevhw"
[    14.608] (II) Unloading fbdevhw
[    14.608] (==) Depth 24 pixmap format is 32 bpp
[    14.608] (II) Loading sub module "int10"
[    14.608] (II) LoadModule: "int10"
[    14.608] (II) Loading /usr/lib/xorg/modules/libint10.so
[    14.608] (II) Module int10: vendor="X.Org Foundation"
[    14.608] 	compiled for 1.10.0, module version = 1.0.0
[    14.608] 	ABI class: X.Org Video Driver, version 10.0
[    14.608] (II) VESA(0): initializing int10
[    14.613] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    14.613] (II) VESA(0): VESA BIOS detected
[    14.613] (II) VESA(0): VESA VBE Version 3.0
[    14.613] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    14.613] (II) VESA(0): VESA VBE OEM: AMD ATOMBIOS
[    14.613] (II) VESA(0): VESA VBE OEM Software Rev: 13.8
[    14.613] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    14.613] (II) VESA(0): VESA VBE OEM Product: CAYMAN
[    14.613] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    14.615] (II) VESA(0): virtual address = 0x7f752afb5000,
	physical address = 0xd0000000, size = 16777216
[    14.629] (II) VESA(0): Setting up VESA Mode 0x124 (1280x1024)
[    14.630] (II) VESA(0): VBESetVBEMode failed, mode set without customized refresh.
[    15.080] (==) VESA(0): Default visual is TrueColor
[    15.080] (==) VESA(0): Backing store disabled
[    15.080] (==) VESA(0): DPMS enabled
[    15.080] (==) RandR enabled
[    15.080] (II) Initializing built-in extension Generic Event Extension
[    15.080] (II) Initializing built-in extension SHAPE
[    15.080] (II) Initializing built-in extension MIT-SHM
[    15.080] (II) Initializing built-in extension XInputExtension
[    15.080] (II) Initializing built-in extension XTEST
[    15.080] (II) Initializing built-in extension BIG-REQUESTS
[    15.080] (II) Initializing built-in extension SYNC
[    15.080] (II) Initializing built-in extension XKEYBOARD
[    15.080] (II) Initializing built-in extension XC-MISC
[    15.080] (II) Initializing built-in extension SECURITY
[    15.080] (II) Initializing built-in extension XINERAMA
[    15.080] (II) Initializing built-in extension XFIXES
[    15.080] (II) Initializing built-in extension RENDER
[    15.080] (II) Initializing built-in extension RANDR
[    15.080] (II) Initializing built-in extension COMPOSITE
[    15.080] (II) Initializing built-in extension DAMAGE
[    15.080] (II) Initializing built-in extension GESTURE
[    15.087] (II) AIGLX: Screen 0 is not DRI2 capable
[    15.087] (II) AIGLX: Screen 0 is not DRI capable
[    15.087] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    15.090] (II) AIGLX: Loaded and initialized swrast
[    15.090] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    15.112] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.122] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.122] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.122] (II) LoadModule: "evdev"
[    15.123] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.123] (II) Module evdev: vendor="X.Org Foundation"
[    15.123] 	compiled for 1.9.99.902, module version = 2.6.0
[    15.123] 	Module class: X.Org XInput Driver
[    15.123] 	ABI class: X.Org XInput driver, version 12.3
[    15.123] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.123] (**) Power Button: always reports core events
[    15.123] (**) Power Button: Device: "/dev/input/event1"
[    15.140] (--) Power Button: Found keys
[    15.140] (II) Power Button: Configuring as keyboard
[    15.140] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    15.140] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.140] (**) Option "xkb_rules" "evdev"
[    15.140] (**) Option "xkb_model" "pc105"
[    15.140] (**) Option "xkb_layout" "us"
[    15.142] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    15.142] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.142] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.143] (**) Power Button: always reports core events
[    15.143] (**) Power Button: Device: "/dev/input/event0"
[    15.143] (--) Power Button: Found keys
[    15.143] (II) Power Button: Configuring as keyboard
[    15.143] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    15.143] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.143] (**) Option "xkb_rules" "evdev"
[    15.143] (**) Option "xkb_model" "pc105"
[    15.143] (**) Option "xkb_layout" "us"
[    15.148] (II) config/udev: Adding input device UVC Camera (046d:0809) (/dev/input/event6)
[    15.148] (**) UVC Camera (046d:0809): Applying InputClass "evdev keyboard catchall"
[    15.148] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.148] (**) UVC Camera (046d:0809): always reports core events
[    15.148] (**) UVC Camera (046d:0809): Device: "/dev/input/event6"
[    15.150] (--) UVC Camera (046d:0809): Found keys
[    15.150] (II) UVC Camera (046d:0809): Configuring as keyboard
[    15.150] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input6/event6"
[    15.150] (II) XINPUT: Adding extended input device "UVC Camera (046d:0809)" (type: KEYBOARD)
[    15.150] (**) Option "xkb_rules" "evdev"
[    15.150] (**) Option "xkb_model" "pc105"
[    15.150] (**) Option "xkb_layout" "us"
[    15.152] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    15.152] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    15.152] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.152] (**) Logitech USB Receiver: always reports core events
[    15.152] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    15.152] (--) Logitech USB Receiver: Found 20 mouse buttons
[    15.152] (--) Logitech USB Receiver: Found scroll wheel(s)
[    15.152] (--) Logitech USB Receiver: Found relative axes
[    15.152] (--) Logitech USB Receiver: Found x and y relative axes
[    15.152] (II) Logitech USB Receiver: Configuring as mouse
[    15.152] (II) Logitech USB Receiver: Adding scrollwheel support
[    15.152] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    15.152] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.152] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/input/input2/event2"
[    15.152] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
[    15.152] (II) Logitech USB Receiver: initialized for relative axes.
[    15.152] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    15.152] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    15.152] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    15.152] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    15.153] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    15.153] (II) No input driver/identifier specified (ignoring)
[    15.153] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    15.153] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    15.153] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.153] (**) Logitech USB Receiver: always reports core events
[    15.153] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    15.160] (--) Logitech USB Receiver: Found 1 mouse buttons
[    15.160] (--) Logitech USB Receiver: Found scroll wheel(s)
[    15.160] (--) Logitech USB Receiver: Found relative axes
[    15.160] (--) Logitech USB Receiver: Found absolute axes
[    15.160] (II) evdev-grail: failed to open grail, no gesture support
[    15.160] (--) Logitech USB Receiver: Found keys
[    15.160] (II) Logitech USB Receiver: Configuring as mouse
[    15.160] (II) Logitech USB Receiver: Configuring as keyboard
[    15.160] (II) Logitech USB Receiver: Adding scrollwheel support
[    15.160] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    15.160] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.160] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.1/input/input3/event3"
[    15.160] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    15.160] (**) Option "xkb_rules" "evdev"
[    15.160] (**) Option "xkb_model" "pc105"
[    15.160] (**) Option "xkb_layout" "us"
[    15.160] (EE) Logitech USB Receiver: failed to initialize for relative axes.
[    15.160] (II) Logitech USB Receiver: initialized for absolute axes.
[    15.160] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    15.160] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    15.160] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    15.160] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    15.161] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    15.161] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    15.161] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.161] (**) Logitech USB Receiver: always reports core events
[    15.161] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    15.162] (--) Logitech USB Receiver: Found keys
[    15.162] (II) Logitech USB Receiver: Configuring as keyboard
[    15.162] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.0/input/input4/event4"
[    15.162] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    15.162] (**) Option "xkb_rules" "evdev"
[    15.162] (**) Option "xkb_model" "pc105"
[    15.162] (**) Option "xkb_layout" "us"
[    15.162] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    15.162] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    15.162] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    15.162] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.163] (**) Logitech USB Receiver: always reports core events
[    15.163] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    15.163] (--) Logitech USB Receiver: Found 20 mouse buttons
[    15.163] (--) Logitech USB Receiver: Found scroll wheel(s)
[    15.163] (--) Logitech USB Receiver: Found relative axes
[    15.163] (--) Logitech USB Receiver: Found x and y relative axes
[    15.163] (--) Logitech USB Receiver: Found absolute axes
[    15.163] (II) evdev-grail: failed to open grail, no gesture support
[    15.163] (--) Logitech USB Receiver: Found keys
[    15.163] (II) Logitech USB Receiver: Configuring as mouse
[    15.163] (II) Logitech USB Receiver: Configuring as keyboard
[    15.163] (II) Logitech USB Receiver: Adding scrollwheel support
[    15.163] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    15.163] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.163] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.1/input/input5/event5"
[    15.163] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    15.163] (**) Option "xkb_rules" "evdev"
[    15.163] (**) Option "xkb_model" "pc105"
[    15.163] (**) Option "xkb_layout" "us"
[    15.163] (II) Logitech USB Receiver: initialized for relative axes.
[    15.163] (WW) Logitech USB Receiver: ignoring absolute axes.
[    15.163] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    15.163] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    15.163] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    15.163] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    15.164] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[    15.164] (II) No input driver/identifier specified (ignoring)
```

---

### Post by lucazade on 2011-03-28
Reason of problem is simple... you should remove additional drivers for ATI because are still not compatible with xorg 1.10 and natty.

sudo jockey-gtk

disable fglrx additional drivers and reboot.

this way you'll use Ati opensource drivers (because at the moment you are using Vesa software drivers) and you'll able to use compiz.

---

### Post by rbrick49 on 2011-03-28
when I sudo sudo jockey-gtk
all i get is a screen comes up no additional drivers available
I am not that good with graphics
regards Ron

---

### Post by lucazade on 2011-03-28
> **rbrick49 said:**
> when I sudo sudo jockey-gtk
all i get is a screen comes up no additional drivers available
I am not that good with graphics
regards Ron

mmm...ok... they should have removed fglrx from repos.

post this file if exists

/etc/X11/xorg.conf

---

### Post by rbrick49 on 2011-03-28
ok mate here is a screenshot when I gedit /etc/x11/xorg

---

### Post by lucazade on 2011-03-28
there are a lot of xorg.* files but they are not in use so are not useful.
It looks like you ati card is not support by ATI opensource drivers but only by FGLRX, unfortunately fglrx drivers are not ready for natty and you're using VESA .

I think you should wait some weeks in order to take gain of you graphic card.
Anyone else have 6900 mobility?

---

### Post by rbrick49 on 2011-03-28
maybe I should download a new daily build and see what transpires
thanks for the input lucozade

---

### Post by tarunyad on 2011-04-15
```
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
** (<unknown>:1849): DEBUG: Unity accessibility initialization
** (<unknown>:1849): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x800

** (<unknown>:1849): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:1849): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:1849): DEBUG: PlaceEntry: Applications
** (<unknown>:1849): DEBUG: PlaceEntry: Commands
** (<unknown>:1849): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:1849): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:1849): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:1849): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:1849): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:1849): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
** (<unknown>:1849): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:1849): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:1849): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:1849): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:1849): DEBUG: IndicatorAdded: libme.so
** (<unknown>:1849): DEBUG: IndicatorAdded: libsession.so
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (<unknown>:1849): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=800
** (<unknown>:1849): DEBUG: Connected to proxy
** (<unknown>:1849): DEBUG: Connected to proxy
** (<unknown>:1849): DEBUG: Connected to proxy

(<unknown>:1849): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1849): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1849): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1849): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1849): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:1849): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
```

thts wht i got help plz .. :|

---

### Post by lucazade on 2011-04-15
> **tarunyad said:**
> ```
Adding plugins...

thts wht i got help plz .. :|

Are you not able to enable visual effects, like the original poster?

which graphic card do you have?
[CODE]lspci | grep VGA
```

Which drivers did you installed?

check Unity hardware requirements:
```
/usr/lib/nux/unity_support_test -p
```

paste here output

---

