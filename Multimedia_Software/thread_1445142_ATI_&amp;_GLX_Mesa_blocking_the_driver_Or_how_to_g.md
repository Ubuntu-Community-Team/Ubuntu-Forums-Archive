---
title: "ATI &amp; GLX: Mesa blocking the driver? Or how to get rid of Brian Paul"
date: 2010-04-02
forum: Multimedia Software
---

### Post by Azrael3000 on 2010-04-02
Hi!

Once again I'm trying to get Enemy Territory running on my system. However as usual my graphics card is being a bitch. First of all some system information:

```

$ uname -a
Linux abel 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

```

Furthermore we have
```

$ glxinfo
name of display: :0.0
display: :0  screen: 0
[b]direct rendering: Yes
server glx vendor string: Brian Paul
server glx version string: 1.4 Mesa 7.7[/b]
server glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
[b]client glx vendor string: Brian Paul
client glx version string: 1.4 Mesa 7.7[/b]
client glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
GLX version: 1.4
GLX extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
[b]OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.7[/b]
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_copy_buffer, GL_ARB_depth_texture, GL_ARB_depth_clamp, 
    GL_ARB_draw_buffers, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_map_buffer_range, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_120, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_sync, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_envmap_bumpmap, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_resize_buffers, GL_MESA_texture_array, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_depth_clamp, GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, GL_NV_point_sprite, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

64 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x22 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb3 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb4 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb5 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb6 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb7 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb8 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb9 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xba 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xbb 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xbc 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xbd 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xbe 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xbf 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc0 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc1 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc2 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc3 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc4 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc5 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc6 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc7 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc8 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc9 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xca 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcb 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcc 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcd 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xce 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcf 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd0 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd1 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd2 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd3 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd4 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd5 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd6 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd7 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd8 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd9 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xda 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdb 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdc 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdd 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xde 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdf 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe0 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe1 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe2 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe3 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe4 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe5 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe6 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe7 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe8 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe9 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xea 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xeb 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xec 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xed 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xee 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xef 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x52 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None

64 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x22  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb3  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb4  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb5  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb6  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb7  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb8  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xb9  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xba  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xbb  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xbc  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xbd  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xbe  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xbf  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc0  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc1  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc2  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc3  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc4  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc5  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc6  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc7  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc8  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xc9  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xca  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcb  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcc  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcd  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xce  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcf  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd0  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd1  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd2  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd3  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd4  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd5  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd6  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd7  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd8  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd9  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xda  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdb  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdc  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdd  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xde  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdf  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe0  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe1  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe2  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe3  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe4  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe5  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe6  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe7  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe8  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe9  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xea  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xeb  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xec  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xed  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xee  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xef  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x52  0 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None

```

I highlighted the parts that I think are important. As you can see direct rendering works. In glxgears I get
```

$ glxgears
3268 frames in 5.0 seconds
3288 frames in 5.0 seconds

```
So that should be fine too.

However in the ET guide it says that the vendor has to be SGI and not Brian Paul. I actually found a thread with approximately the same problem (direct draw didn't work additionally) and it was claimed that by running xfix the problem was gone. Unfortunately xfix is no longer available in Karmic.

Here is some more output from /usr/lib
```

/usr/lib$ ll | grep GL
lrwxrwxrwx  1 root root    11 2009-12-30 20:37 libEGL.so -> libEGL.so.1
lrwxrwxrwx  1 root root    13 2009-12-30 20:37 libEGL.so.1 -> libEGL.so.1.0
-rwxr-xr-x  1 root root  209K 2009-12-30 20:37 libEGL.so.1.0
lrwxrwxrwx  1 root root    10 2009-12-30 20:37 libGL.so -> libGL.so.1
lrwxrwxrwx  1 root root    19 2010-04-01 19:15 libGL.so.1 -> libGL.so.1.5.070700
-rw-r--r--  1 root root  395K 2009-10-14 00:08 libGL.so.1.2
-rwxr-xr-x  1 root root   13M 2009-12-30 20:37 libGL.so.1.5.070700
-rw-r--r--  1 root root  700K 2009-10-14 00:08 libGLU.a
lrwxrwxrwx  1 root root    11 2009-12-30 20:37 libGLU.so -> libGLU.so.1
lrwxrwxrwx  1 root root    20 2009-12-30 20:37 libGLU.so.1 -> libGLU.so.1.3.070700
-rw-r--r--  1 root root  446K 2009-10-14 00:08 libGLU.so.1.3.070600
-rwxr-xr-x  1 root root  1.7M 2009-12-30 20:37 libGLU.so.1.3.070700
lrwxrwxrwx  1 root root    11 2009-12-30 20:37 libGLw.so -> libGLw.so.1
lrwxrwxrwx  1 root root    15 2009-12-30 20:37 libGLw.so.1 -> libGLw.so.1.0.0
-rwxr-xr-x  1 root root   37K 2009-12-30 20:37 libGLw.so.1.0.0

/usr/lib$ ll | grep dri
drwxr-xr-x  2 root root  4.0K 2010-04-01 19:15 dri
-rw-r--r--  1 root root   38K 2010-03-02 16:10 libcupsdriver.so.1

/usr/lib$ ll | grep drm
lrwxrwxrwx  1 root root    21 2009-10-30 11:52 libdrm_intel.so.1 -> libdrm_intel.so.1.0.0
-rw-r--r--  1 root root   34K 2009-10-08 19:01 libdrm_intel.so.1.0.0
lrwxrwxrwx  1 root root    22 2009-10-30 11:52 libdrm_radeon.so.1 -> libdrm_radeon.so.1.0.0
-rw-r--r--  1 root root   14K 2009-10-08 19:01 libdrm_radeon.so.1.0.0
lrwxrwxrwx  1 root root    15 2009-10-30 11:52 libdrm.so.2 -> libdrm.so.2.4.0
-rw-r--r--  1 root root   34K 2009-10-08 19:01 libdrm.so.2.4.0

```

I did reinstall Mesa yesterday so I thought some files might have been overwritten. So I also reinstalled xserver-xorg-video-radeon and xserver-xorg-video-ati without success.

Any help is greatly appreciated,

Arno

---

### Post by Azrael3000 on 2010-04-02
Some more information I gathered during the day. 

I forgot to mention that I enabled KBM, here's the output:

```

$ dmesg | grep drm
[    2.204294] [drm] Initialized drm 1.1.0 20060810
[    2.225337] [drm] radeon default to kernel modesetting DISABLED.
[    2.225665] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[   22.654730] [drm] Module unloaded
[   22.722721] [drm] Initialized drm 1.1.0 20060810
[   22.780763] [drm] radeon kernel modesetting enabled.
[   22.782926] [drm] radeon: Initializing kernel modesetting.
[   22.782986] [drm] register mmio base: 0xC8100000
[   22.782988] [drm] register mmio size: 65536
[   22.783326] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   22.783332] [drm] Clocks initialized !
[   22.783338] [drm] Generation 2 PCI interface, using max accessible memory
[   22.787993] [drm] Detected VRAM RAM=128M, BAR=128M
[   22.787997] [drm] RAM width 128bits DDR
[   22.788234] [drm] radeon: 2 quad pipes, 1 z pipes initialized.
[   22.788243] [drm] radeon: VRAM 128M
[   22.788245] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   22.788247] [drm] radeon: GTT 512M
[   22.788249] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   22.793426] [drm] radeon: irq initialized.
[   22.794356] [drm] radeon: 128M of VRAM memory ready
[   22.794358] [drm] radeon: 512M of GTT memory ready.
[   22.794361] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   22.794742] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   22.794756] [drm] radeon: cp idle (0x10000C03)
[   22.794760] [drm] Loading R400 Microcode
[   22.794963] [drm] radeon: ring at 0x0000000020000000
[   22.794985] [drm] ring test succeeded in 1 usecs
[   22.795160] [drm] radeon: ib pool ready.
[   22.795222] [drm] ib test succeeded in 0 usecs
[   22.795426] [drm] Radeon Display Connectors
[   22.795428] [drm] Connector 0:
[   22.795430] [drm]   VGA
[   22.795433] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   22.795435] [drm]   Encoders:
[   22.795436] [drm]     CRT1: INTERNAL_DAC1
[   22.795438] [drm] Connector 1:
[   22.795440] [drm]   LVDS
[   22.795442] [drm]   DDC: 0x1a8 0x1a8 0x1ac 0x1ac 0x1b0 0x1b0 0x1b4 0x1b4
[   22.795444] [drm]   Encoders:
[   22.795446] [drm]     LCD1: INTERNAL_LVDS
[   22.795447] [drm] Connector 2:
[   22.795449] [drm]   DVI-I
[   22.795451] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   22.795453] [drm]   Encoders:
[   22.795455] [drm]     DFP1: INTERNAL_TMDS1
[   22.915914] [drm] fb mappable at 0xD00C0000
[   22.915916] [drm] vram apper at 0xD0000000
[   22.915918] [drm] size 7056000
[   22.915919] [drm] fb depth is 24
[   22.915921] [drm]    pitch is 6720
[   22.916010] fb0: radeondrmfb frame buffer device
[   22.916014] [drm] radeon: kernel modesetting successfully initialized.
[   22.916046] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   23.317828] [drm] LVDS-6: set mode 1680x1050 e

```

Note that I used a fix (editing gdm.conf) mentioned in
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413)

As someone suggested I ran tuxracer since it runs only fast if hardware acceleration is turned on. I only got framerates < 2 so apparently it's not working.

---

