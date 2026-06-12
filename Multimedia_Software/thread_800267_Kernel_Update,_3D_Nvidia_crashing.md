---
title: "Kernel Update, 3D Nvidia crashing"
date: 2008-05-19
forum: Multimedia Software
---

### Post by malfist on 2008-05-19
Decided to repost here because it made more sense now that the problem has been located. [Link](http://ubuntuforums.org/showthread.php?t=799258)

Since I updated yesterday (including a kernel update I believe), it is near impossible to play a 3D game. (OpenGL)

The screen gets a lot of lines that are blurs all over it and then everything freezes, no exit, no control. The music still plays but that's it. I can use the "Magic Keys" to reboot but I can't switch TTY or restart X.

I'm using nvidia-glx-new or whatever that package is. I didn't use nvidia's installer or envy. My video card is GeForce 6800.

Both Tremulous and WoW crash like this.

Any suggestions are appreciated.

---

### Post by malfist on 2008-05-19
May not be the kernel, I restart into the old kernel and it did the same. It crashes/locks-up a lot faster in tremulous than in WoW. Going to reinstall drivers with envy.

---

### Post by malfist on 2008-05-19
That didn't fix anything.

GLX gears:
```

jerome@jerome-desktop:~$ glxgears 
17937 frames in 5.0 seconds = 3587.303 FPS
18555 frames in 5.0 seconds = 3710.829 FPS
18645 frames in 5.0 seconds = 3728.905 FPS
18637 frames in 5.0 seconds = 3727.249 FPS
18649 frames in 5.0 seconds = 3729.644 FPS

```

glxinfo (with the last table removed)
```

jerome@jerome-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6800 XE/AGP/SSE/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 169.12
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

```

glxheads
```

jerome@jerome-desktop:~$ glxheads
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0
  Display:     0x805e380
  Window:      0x2a00002
  Context:     0x806c424
  GL_VERSION:  2.1.2 NVIDIA 169.12
  GL_VENDOR:   NVIDIA Corporation
  GL_RENDERER: GeForce 6800 XE/AGP/SSE/3DNOW!

```

---

### Post by malfist on 2008-05-19
I find this
```

nvLock: client timed out, taking the lock

```
In my Xorg.0.log file. Does that mean anything?

---

### Post by malfist on 2008-05-19
restored to several old xorg.conf files and none worked any better.

I'm out of things to try, any **any** would be appreciated.

---

### Post by malfist on 2008-05-19
This shows up in my syslog after a lock out:
```

May 19 21:44:06 jerome-desktop -- MARK --
May 19 22:03:36 jerome-desktop kernel: [ 2437.738763] NVRM: Xid (0002:00): 13, 0002 beef3097 00004097 00000204 012c0003 00000100
May 19 22:03:36 jerome-desktop kernel: [ 2441.728926] NVRM: Xid (0002:00): 6, PE001f 1818 00000000 00000000 00000000 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.731962] NVRM: Xid (0002:00): 7, Ch 00000000 M 00000408 D 00ffffff intr 00010000
May 19 22:03:36 jerome-desktop kernel: [ 2441.734994] NVRM: Xid (0002:00): 7, Ch 00000001 M 00000000 D 00000000 intr 00010000
May 19 22:03:36 jerome-desktop kernel: [ 2441.738040] NVRM: Xid (0002:00): 4, Ch 0000001f SC 00000007 M 00000700 Data 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.741074] NVRM: Xid (0002:00): 6, PE001f 0700 00000000 00000000 00000000 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.750087] NVRM: Xid (0002:00): 4, Ch 0000001f SC 00000000 M 00000000 Data 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.753182] NVRM: Xid (0002:00): 7, Ch 0000001e M 00000000 D 00000000 intr 00011000
May 19 22:03:48 jerome-desktop kernel: [ 2454.310344] SysRq : Keyboard mode set to system default
May 19 21:44:06 jerome-desktop -- MARK --
May 19 22:03:36 jerome-desktop kernel: [ 2437.738763] NVRM: Xid (0002:00): 13, 0002 beef3097 00004097 00000204 012c0003 00000100
May 19 22:03:36 jerome-desktop kernel: [ 2441.728926] NVRM: Xid (0002:00): 6, PE001f 1818 00000000 00000000 00000000 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.731962] NVRM: Xid (0002:00): 7, Ch 00000000 M 00000408 D 00ffffff intr 00010000
May 19 22:03:36 jerome-desktop kernel: [ 2441.734994] NVRM: Xid (0002:00): 7, Ch 00000001 M 00000000 D 00000000 intr 00010000
May 19 22:03:36 jerome-desktop kernel: [ 2441.738040] NVRM: Xid (0002:00): 4, Ch 0000001f SC 00000007 M 00000700 Data 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.741074] NVRM: Xid (0002:00): 6, PE001f 0700 00000000 00000000 00000000 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.750087] NVRM: Xid (0002:00): 4, Ch 0000001f SC 00000000 M 00000000 Data 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.753182] NVRM: Xid (0002:00): 7, Ch 0000001e M 00000000 D 00000000 intr 00011000
May 19 22:03:48 jerome-desktop kernel: [ 2454.310344] SysRq : Keyboard mode set to system default

```

---

