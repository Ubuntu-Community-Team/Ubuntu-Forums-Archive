---
title: "StepMania CVS 4.0 No VIdeo"
date: 2010-07-25
forum: Multimedia Software
---

### Post by ODECiF on 2010-07-25
Hello everyone! I have now spent 3 whole nights and searched through the entire world trying to find out what is wrong.

I have installed StepMania CVS 4.0 CVS. Everything went fine (just a minor patch that was added) and I can see the menu, I can navigate through the menus, I can set settings, I can play a track/song, the audiosync is correct, BUT! I have no background video! I also do not have any video (for the tracks/songs) in the menu! Now, I have found about three or four forums where this issue has been added, but they were closed since 2008 and has been dead since then.

I run Ubuntu 10.04 LTS (Lucid Lynx) and I currently run StepMania from the terminal, using:

```
cd /usr/local/bin/stepmania cvs/
sudo ./stepmania
```

And here's the output when i run it:

```
root@bcns-desktop:/usr/local/bin/stepmania cvs# ./stepmania
StepMania CVS 4.0 CVS
Compiled Sun Jul 25 03:25:59 CEST 2010 (build 2)
Log starting 2010-07-25 15:50:07
Loading window: gtk
OS: Linux ver 020632
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.11.1
Threads library: NPTL 2.11.1
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.21.
ALSA Driver: 0: HDA Intel [Intel], device 0: AD198x Analog [AD198x Analog], 1/1 subdevices avail
ALSA Driver: 0: HDA Intel [Intel], device 1: AD198x Digital [AD198x Digital], 1/1 subdevices avail
ALSA: Mixing at 44100hz
Sound driver: ALSA-sw
Lights driver: SystemMessage
Lights driver: Export
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../idVendor": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../idProduct": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../serial": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../product": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Error opening "/sys/block/sr0/device/../manufacturer": No such file or directory
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: RageFileDriverDirectHelpers.cpp:274: Got file 'blkid.tab' in '/etc' from list, but can't stat? (No such file or directory)
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: RageFileDriverDirectHelpers.cpp:274: Got file 'motd' in '/etc' from list, but can't stat? (No such file or directory)
/////////////////////////////////////////

(stepmania:4551): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
Video renderers: 'opengl'
Display: :0.0 (screen 0)
Direct rendering: no
X server vendor: The X.Org Foundation [1.7.6.0]
Server GLX vendor: NVIDIA Corporation [1.4]
Client GLX vendor: NVIDIA Corporation [1.4]
OpenGL shading language: 1.50 NVIDIA via Cg compiler
Paletted textures disabled: GL_EXT_paletted_texture missing.
OGL Vendor: NVIDIA Corporation
OGL Renderer: GeForce 9800 GT/PCI/SSE2
OGL Version: 3.2.0 NVIDIA 195.36.24
OGL Max texture size: 8192
OGL Texture units: 4
GLU Version: 1.3
OGL Extensions:
  GL_ARB: color_buffer_float, compatibility, copy_buffer, depth_buffer_float, depth_clamp, depth_texture, 
    draw_buffers, draw_elements_base_vertex, draw_instanced, fragment_coord_conventions, fragment_program, 
    fragment_program_shadow, fragment_shader, framebuffer_object, framebuffer_sRGB, geometry_shader4, 
    half_float_pixel, half_float_vertex, imaging, map_buffer_range, multisample, multitexture, occlusion_query, 
    pixel_buffer_object, point_parameters, point_sprite, provoking_vertex, seamless_cube_map, shader_objects, 
    shading_language_100, shadow, sync, texture_border_clamp, texture_buffer_object, texture_compression, 
    texture_compression_rgtc, texture_cube_map, texture_env_add, texture_env_combine, texture_env_crossbar, 
    texture_env_dot3, texture_float, texture_mirrored_repeat, texture_multisample, texture_non_power_of_two, 
    texture_rectangle, texture_rg, transpose_matrix, uniform_buffer_object, vertex_array_bgra, 
    vertex_array_object, vertex_buffer_object, vertex_program, vertex_shader, window_pos
  GL_ATI: draw_buffers, texture_float, texture_mirror_once
  GL_EXTX_framebuffer_mixed_formats
  GL_EXT: Cg_shader, abgr, bgra, bindable_uniform, blend_color, blend_equation_separate, blend_func_separate, 
    blend_minmax, blend_subtract, compiled_vertex_array, depth_bounds_test, direct_state_access, draw_buffers2, 
    draw_instanced, draw_range_elements, fog_coord, framebuffer_blit, framebuffer_multisample, framebuffer_object, 
    framebuffer_sRGB, geometry_shader4, gpu_program_parameters, gpu_shader4, multi_draw_arrays, 
    packed_depth_stencil, packed_float, packed_pixels, pixel_buffer_object, point_parameters, provoking_vertex, 
    rescale_normal, secondary_color, separate_shader_objects, separate_specular_color, shadow_funcs, 
    stencil_two_side, stencil_wrap, texture3D, texture_array, texture_buffer_object, texture_compression_latc, 
    texture_compression_rgtc, texture_compression_s3tc, texture_cube_map, texture_edge_clamp, texture_env_add, 
    texture_env_combine, texture_env_dot3, texture_filter_anisotropic, texture_integer, texture_lod, 
    texture_lod_bias, texture_mirror_clamp, texture_object, texture_sRGB, texture_shared_exponent, 
    texture_swizzle, timer_query, vertex_array, vertex_array_bgra
  GL_IBM: rasterpos_clip, texture_mirrored_repeat
  GL_KTX_buffer_region
  GL_NVX: conditional_render, gpu_memory_info
  GL_NV: blend_square, conditional_render, copy_depth_to_color, copy_image, depth_buffer_float, depth_clamp, 
    explicit_multisample, fence, float_buffer, fog_distance, fragment_program, fragment_program2, 
    fragment_program_option, framebuffer_multisample_coverage, geometry_shader4, gpu_program4, half_float, 
    light_max_exponent, multisample_coverage, multisample_filter_hint, occlusion_query, packed_depth_stencil, 
    parameter_buffer_object, parameter_buffer_object2, pixel_data_range, point_sprite, primitive_restart, 
    register_combiners, register_combiners2, shader_buffer_load, texgen_reflection, texture_barrier, 
    texture_compression_vtc, texture_env_combine4, texture_expand_normal, texture_rectangle, texture_shader, 
    texture_shader2, texture_shader3, transform_feedback, vertex_array_range, vertex_array_range2, 
    vertex_buffer_unified_memory, vertex_program, vertex_program1_1, vertex_program2, vertex_program2_option, 
    vertex_program3
  GL_S3_s3tc
  GL_SGIS: generate_mipmap, texture_lod
  GL_SGIX: depth_texture, shadow
  GL_SUN_slice_accum
OpenGL Windowed 800x600 32 color 32 texture 50Hz Vsync SmoothLines
/////////////////////////////////////////
WARNING: Banner cache for '/Songs/Jubo's Simfiles/Black Lagoon OP/Black Lagoon OP Banner.avi' wasn't loaded
/////////////////////////////////////////
Mixing 510.752491 ahead in 13248 Mix() calls
Mixing underruns: 8
Players joined: none
Language: en
Current renderer: OpenGL
Theme: default

```

Everyone please! I am playing a lot of songs with videos attached to them, and It's not the same without it (a black background is quite boring when you know what's supposed to be there).

---

