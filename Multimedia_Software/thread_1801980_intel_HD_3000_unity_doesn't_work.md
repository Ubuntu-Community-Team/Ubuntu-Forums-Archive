---
title: "intel HD 3000: unity doesn't work"
date: 2011-07-11
forum: Multimedia Software
---

### Post by matthias24 on 2011-07-11
On Ubuntu 11.04 Unity doesn't work (actually no 3D app/game seems to work at all, that needs opengl). I've already installed the xorg-edgers ppa and have the newest 2.6.39 kernel.

Ubuntu Classic works fine, if I try to start Ubuntu with Unity: I only see the Desktop, but no Unity (on the left - nothing appears) and no bar at the top, ALT+F2 doesn't work too

Does Unity and 3D work at all with intel HD 3000 (sandy bridge, core i5 2500K, gigabyte H67A-UD3H-B3) or is it still work in progress?
Did I miss any packages?

package versions:
- Kernel 2.6.39-3.10
- xserver-xorg-video-intel: 2:2.15.0+git20110708.1e2cae0a-0ubuntu0sarvatt3~natty
- xserver-xorg: 1:7.6+4ubuntu3.1
- xserver-xorg-core: 2:1.10.2.901+git20110702+server-1.10-branch.79ef102c-0ubuntu0sarvatt~natty

Output of: sudo lshw -C video
```
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:fb800000-fbbfffff memory:e0000000-efffffff ioport:ff00(size=64)
```

output of: glxinfo:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Desktop 
OpenGL version string: 2.1 Mesa 7.12-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_copy_texture, GL_EXT_polygon_offset, GL_EXT_subtexture, 
    GL_EXT_texture_object, GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, 
    GL_EXT_texture, GL_EXT_texture3D, GL_IBM_rasterpos_clip, 
    GL_ARB_point_parameters, GL_EXT_draw_range_elements, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_separate_specular_color, GL_EXT_texture_edge_clamp, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_ARB_framebuffer_sRGB, 
    GL_ARB_multitexture, GL_EXT_framebuffer_sRGB, 
    GL_IBM_multimode_draw_arrays, GL_IBM_texture_mirrored_repeat, 
    GL_3DFX_texture_compression_FXT1, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_ARB_depth_texture, 
    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, GL_ATI_envmap_bumpmap, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_depth_clamp, 
    GL_NV_vertex_program1_1, GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_ARB_depth_clamp, 
    GL_ARB_fragment_program_shadow, GL_ARB_half_float_pixel, 
    GL_ARB_point_sprite, GL_ARB_shading_language_100, GL_ARB_sync, 
    GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_rectangle, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_ARB_framebuffer_object, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_packed_depth_stencil, GL_APPLE_object_purgeable, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_env_combine, 
    GL_EXT_texture_sRGB_decode, GL_EXT_timer_query, GL_OES_EGL_image, 
    GL_ARB_copy_buffer, GL_ARB_half_float_vertex, GL_ARB_map_buffer_range, 
    GL_ARB_texture_rg, GL_ARB_texture_swizzle, GL_ARB_vertex_array_bgra, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
    GL_ARB_ES2_compatibility, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_provoking_vertex, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_ARB_robustness

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x096 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x098 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x099 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x09d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x09e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0a2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0a4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ad 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ae 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0af 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x065  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x066  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x068  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x069  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x06a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x071 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x072 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x073 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x074 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x076 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x077  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x078  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x079 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x07a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x07b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x07c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x07d  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x080  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x081  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x082  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x083 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x084 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x086 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x087 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x088 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x089 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08f  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x090  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x091 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x092 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x093 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

```

output of: dpkg -l |grep mesa
```
ii  libegl1-mesa                          7.12.0~git20110707.3069a7ea-0ubuntu0sarvatt2~natty                         free implementation of the EGL API -- runtime
ii  libegl1-mesa-drivers                  7.12.0~git20110707.3069a7ea-0ubuntu0sarvatt2~natty                         free implementation of the EGL API -- hardware drivers
ii  libgl1-mesa-dri                       7.12.0~git20110707.3069a7ea-0ubuntu0sarvatt2~natty                         free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx                       7.12.0~git20110707.3069a7ea-0ubuntu0sarvatt2~natty                         free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa                         7.12.0~git20110707.3069a7ea-0ubuntu0sarvatt2~natty                         free implementation of the GL API -- shared library
ii  libgles1-mesa                         7.12.0~git20110707.3069a7ea-0ubuntu0sarvatt2~natty                         free implementation of the OpenGL|ES 1.x API -- runtime
ii  libgles2-mesa                         7.12.0~git20110707.3069a7ea-0ubuntu0sarvatt2~natty                         free implementation of the OpenGL|ES 2.x API -- runtime
ii  libglu1-mesa                          7.12.0~git20110707.3069a7ea-0ubuntu0sarvatt2~natty                         Mesa OpenGL utility library (GLU)
ii  libglw1-mesa                          7.4-0ubuntu2                                                               A free implementation of the OpenGL API -- runtime
ii  libopenvg1-mesa                       7.12.0~git20110707.3069a7ea-0ubuntu0sarvatt2~natty                         free implementation of the OpenVG API -- runtime
ii  libosmesa6                            7.12.0~git20110707.3069a7ea-0ubuntu0sarvatt2~natty                         Mesa Off-screen rendering extension
ii  mesa-utils                            8.0.1+git20110129+d8f7d6b-0ubuntu2                                         Miscellaneous Mesa GL utilities
ii  mesa-utils-extra                      8.0.1+git20110129+d8f7d6b-0ubuntu2                                         Miscellaneous Mesa utilies (opengles, egl)

```

output of: dpkg -i |grep xorg
```
ii  i965-va-driver                        1.0.12-1~xorgedgers                                                        Video Acceleration (VA) API for Linux -- i965 VA driver
ii  libva-glx1                            1.0.12-1~xorgedgers                                                        Video Acceleration (VA) API for Linux -- GLX runtime
ii  libva-x11-1                           1.0.12-1~xorgedgers                                                        Video Acceleration (VA) API for Linux -- X11 runtime
ii  libva1                                1.0.12-1~xorgedgers                                                        Video Acceleration (VA) API for Linux -- runtime
ii  python-xkit                           0.4.2.2                                                                    library for the manipulation of the xorg.conf
ii  vainfo                                1.0.12-1~xorgedgers                                                        Video Acceleration (VA) API for Linux -- info program
ii  xorg                                  1:7.6+4ubuntu3.1                                                           X.Org X Window System
ii  xorg-docs-core                        1:1.5.99.901-1ubuntu1                                                      Core documentation for the X.org X Window System
ii  xserver-xorg                          1:7.6+4ubuntu3.1                                                           the X.Org X server
ii  xserver-xorg-core                     2:1.10.2.901+git20110702+server-1.10-branch.79ef102c-0ubuntu0sarvatt~natty Xorg X server - core server
ii  xserver-xorg-input-all                1:7.6+4ubuntu3.1                                                           the X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev              1:2.6.0+git20110408.68a6a18f-0ubuntu0sarvatt                               X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse              1:1.7.0+git20110628.b12fa0d5-0ubuntu0sarvatt~natty                         X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics          1.3.99+git20110116.0e27ce3a-0ubuntu12.1                                    Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse            1:12.7.0+git20110624.fd140bfb-0ubuntu0sarvatt~natty                        X.Org X server -- VMMouse input driver to use with VMWare
ii  xserver-xorg-input-wacom              1:0.10.11-0ubuntu4                                                         X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                1:7.6+4ubuntu3.1                                                           the X.Org X server -- output driver metapackage
ii  xserver-xorg-video-apm                1:1.2.3+git20110526.6f8a776f-0ubuntu0sarvatt~natty                         X.Org X server -- APM display driver
ii  xserver-xorg-video-ark                1:0.7.3+git20110526.9d3769be-0ubuntu0sarvatt~natty                         X.Org X server -- ark display driver
ii  xserver-xorg-video-ati                1:6.14.99+git20110623.9bb31158-0ubuntu0sarvatt~natty                       X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-chips              1:1.2.4+git20110526.e4bd8648-0ubuntu0sarvatt~natty                         X.Org X server -- Chips display driver
ii  xserver-xorg-video-cirrus             1:1.3.2+git20110526.e4f80ffd-0ubuntu0sarvatt~natty                         X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev              1:0.4.2+git20110526.a8721393-0ubuntu0sarvatt~natty                         X.Org X server -- fbdev display driver
ii  xserver-xorg-video-i128               1:1.3.4+git20110526.b9e0edbd-0ubuntu0sarvatt~natty                         X.Org X server -- i128 display driver
ii  xserver-xorg-video-intel              2:2.15.0+git20110708.1e2cae0a-0ubuntu0sarvatt3~natty                       X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64             6.9.0+git20110526.ef55d1f1-0ubuntu0sarvatt~natty                           X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                1:1.4.13.dfsg-3ubuntu0sarvatt                                              X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic           1:1.2.5+git20110526.a9d69f6d-0ubuntu0sarvatt~natty                         X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nouveau            1:0.0.16+git20110623.ab89aa02-0ubuntu0sarvatt~natty                        X.Org X server -- Nouveau display driver (experimental)
ii  xserver-xorg-video-nv                 1:2.1.17-3ubuntu7                                                          X.Org X server -- NV display driver
ii  xserver-xorg-video-openchrome         1:0.2.904+svn916-1ubuntu0sarvatt                                           X.Org X server -- VIA display driver
ii  xserver-xorg-video-qxl                0.0.12-1ubuntu4                                                            X.Org X server -- QXL display driver
ii  xserver-xorg-video-r128               6.8.1+git20110526.3de85360-0ubuntu0sarvatt~natty                           X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon             1:6.14.99+git20110623.9bb31158-0ubuntu0sarvatt~natty                       X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-rendition          1:4.2.4+git20110526.541d1193-0ubuntu0sarvatt~natty                         X.Org X server -- Rendition display driver
ii  xserver-xorg-video-s3                 1:0.6.3+git20110526.381ace93-0ubuntu0sarvatt~natty                         X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge            1:1.10.4+git20110526.a568407e-0ubuntu0sarvatt~natty                        X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-video-savage             1:2.3.2+git20110526.d177ae0b-0ubuntu0sarvatt~natty                         X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion      1:1.7.5+git20110526.087226bf-0ubuntu0sarvatt~natty                         X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                1:0.10.3+git20110608.94f23a56-0ubuntu0sarvatt~natty                        X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb             1:0.9.4+git20110608.241dd519-0ubuntu0sarvatt~natty                         X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx               1:1.4.3+git20110526.0c4ffbec-0ubuntu0sarvatt~natty                         X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident            1:1.3.4+git20110526.de79bbea-0ubuntu0sarvatt~natty                         X.Org X server -- Trident display driver
ii  xserver-xorg-video-tseng              1:1.2.4+git20110613.542e65de-0ubuntu0sarvatt~natty                         X.Org X server -- Tseng display driver
ii  xserver-xorg-video-vesa               1:2.3.0+git20110526.0b02c685-0ubuntu0sarvatt~natty                         X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware             1:11.0.3+git20110526.0142bb8d-0ubuntu0sarvatt~natty                        X.Org X server -- VMware display driver
ii  xserver-xorg-video-voodoo             1:1.2.4+git20110526.614ccdf6-0ubuntu0sarvatt~natty                         X.Org X server -- Voodoo display driver

```

---

### Post by iGadget2 on 2011-08-20
I seem to have the same problem on my brand new i5 2500. Any news on this matter?

---

### Post by BicyclerBoy on 2011-08-20
You can not delete your ubuntu forum account..even the admins will not do it except for very convincing reasons.

There is a unity support blacklist file somewhere..(could be hard-coded)
The std repos sandybridge drivers were/are useless so your video h/w could still be blacklisted.

This reveals if blacklisted...
/usr/lib/nux/unity_support_test -p

gksudo gedit /etc/environment
add the below line to file, save & exit..
UNITY_FORCE_START=1

Unity 3d works very well on the 1st gen atom netbooks (845GME GMA900).

---

