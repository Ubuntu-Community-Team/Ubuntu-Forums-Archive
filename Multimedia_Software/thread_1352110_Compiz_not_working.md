---
title: "Compiz not working"
date: 2009-12-11
forum: Multimedia Software
---

### Post by sagi7 on 2009-12-11
Hello,

i am now trying around to get compiz to work for x days.
Googled a lot and tried hints in forums with no success.
So i start a new thread.

Compiz starts, but the system is slow near freezing and not really operable.
I am using Nvidia 195.22 driver on amd64 but tested several other versions included restricted drivers without success.

Here comes the output from glxinfo

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 
    GLX_NV_video_capture
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 9300 / nForce 730i/PCI/SSE2
OpenGL version string: 3.2.0 NVIDIA 195.22
OpenGL shading language version string: 1.50 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_compatibility, GL_ARB_copy_buffer, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_geometry_shader4, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_imaging, GL_ARB_map_buffer_range, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_seamless_cube_map, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_rg, GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_transform_feedback2, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_explicit_multisample, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_shader_buffer_load, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_transform_feedback, GL_NV_transform_feedback2, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

84 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x31 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x32 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x33 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x42 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x49 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x4a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x4c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x4e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x4f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x54 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x56 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x57 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x5f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x60 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x61 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x63 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x64 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x65 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x66 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x67 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x68 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x69 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x6a 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x6b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x6c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x6d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x6e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x6f 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x70 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x71 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x72 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon

167 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x75  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x76  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x77  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x78  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x79  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x7a  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x7b  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x7c  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x7d  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x7e  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x7f  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x80  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x81  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x82  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x83  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x84  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x85  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x86  0 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x87  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x88  0 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x89  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x8a  0 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x8b  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x8c  0 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x8d  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x8e  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x8f  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x90  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x91  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x92  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x93  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x94  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x95  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x96  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x97  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x98  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x99  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x9a  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x9b  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x9c  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x9d  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x9e  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x9f  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xa0  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xa1  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xa2  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xa3  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xa4  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xa5  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xa6  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xa7  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xa8  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xa9  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xaa  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xab  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xac  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xad  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0xae  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xaf  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0xb0  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xb1  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xb2  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xb3  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xb4  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xb5  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb6  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb7  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb8  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb9  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xba  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xbb  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xbc  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xbd  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xbe  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xbf  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xc0  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xc1  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xc2  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xc3  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xc4  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xc5  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xc6  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xc7  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xc8  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xc9  0 sg  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0xca  0 sg  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0xcb  0 sg  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0xcc  0 sg  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0xcd  0 sg  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0xce  0 sg  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0xcf  0 sg  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0xd0  0 sg  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0xd1  0 sg  0  0  0 r  .  .  0  0  0  0  4 16  0 16 16 16 16  0 0 None
0xd2  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  0 16 16 16 16  0 0 None
0xd3  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  8 16 16 16 16  0 0 None
0xd4  0 sg  0 32  0 r  .  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0xd5  0 sg  0 32  0    .  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0xd6  0 sg  0 32  0 r  y  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0xd7  0 sg  0 32  0    y  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0xd8  0 sg  0 32  0 r  .  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0xd9  0 sg  0 32  0    .  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0xda  0 sg  0 32  0 r  y  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0xdb  0 sg  0 32  0    y  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0xdc  0 sg  0 64  0 r  .  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0xdd  0 sg  0 64  0    .  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0xde  0 sg  0 64  0 r  y  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0xdf  0 sg  0 64  0    y  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0xe0  0 sg  0 128  0 r  .  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0xe1  0 sg  0 128  0    .  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0xe2  0 sg  0 128  0 r  y  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0xe3  0 sg  0 128  0    y  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0xe4  0 sg  0 32  0 r  .  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0xe5  0 sg  0 32  0    .  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0xe6  0 sg  0 32  0 r  y  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0xe7  0 sg  0 32  0    y  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0xe8  0 sg  0 32  0 r  .  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0xe9  0 sg  0 32  0    .  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0xea  0 sg  0 32  0 r  y  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0xeb  0 sg  0 32  0    y  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0xec  0 sg  0 32  0 r  .  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0xed  0 sg  0 32  0    .  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0xee  0 sg  0 32  0 r  y  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0xef  0 sg  0 32  0    y  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0xf0  0 sg  0 32  0 r  .  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0xf1  0 sg  0 32  0    .  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0xf2  0 sg  0 32  0 r  y  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0xf3  0 sg  0 32  0    y  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0xf4  0 sg  0 64  0 r  .  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0xf5  0 sg  0 64  0    .  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0xf6  0 sg  0 64  0 r  y  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0xf7  0 sg  0 64  0    y  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0xf8  0 sg  0 64  0 r  .  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0xf9  0 sg  0 64  0    .  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0xfa  0 sg  0 64  0 r  y  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0xfb  0 sg  0 64  0    y  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0xfc  0 sg  0 128  0 r  .  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0xfd  0 sg  0 128  0    .  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0xfe  0 sg  0 128  0 r  y  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0xff  0 sg  0 128  0    y  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0x100  0 sg  0 128  0 r  .  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x101  0 sg  0 128  0    .  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x102  0 sg  0 128  0 r  y  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x103  0 sg  0 128  0    y  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x104  0 sg  0 16  0 r  .  . 16  0  0  0  4  0  0 16 16 16 16  0 0 None
0x105  0 sg  0 16  0    .  . 16  0  0  0  4  0  0 16 16 16 16  0 0 None
0x106  0 sg  0 16  0 r  y  . 16  0  0  0  4  0  0 16 16 16 16  0 0 None
0x107  0 sg  0 16  0    y  . 16  0  0  0  4  0  0 16 16 16 16  0 0 None
0x108  0 sg  0 64  0 r  .  . 32 32  0  0  4  0  0 16 16 16 16  0 0 None
0x109  0 sg  0 64  0    .  . 32 32  0  0  4  0  0 16 16 16 16  0 0 None
0x10a  0 sg  0 64  0 r  y  . 32 32  0  0  4  0  0 16 16 16 16  0 0 None
0x10b  0 sg  0 64  0    y  . 32 32  0  0  4  0  0 16 16 16 16  0 0 None
0x10c  0 sg  0 16  0 r  .  . 16  0  0  0  4 24  0 16 16 16 16  0 0 None
0x10d  0 sg  0 16  0    .  . 16  0  0  0  4 24  0 16 16 16 16  0 0 None
0x10e  0 sg  0 16  0 r  y  . 16  0  0  0  4 24  0 16 16 16 16  0 0 None
0x10f  0 sg  0 16  0    y  . 16  0  0  0  4 24  0 16 16 16 16  0 0 None
0x110  0 sg  0 16  0 r  .  . 16  0  0  0  4 24  8 16 16 16 16  0 0 None
0x111  0 sg  0 16  0    .  . 16  0  0  0  4 24  8 16 16 16 16  0 0 None
0x112  0 sg  0 16  0 r  y  . 16  0  0  0  4 24  8 16 16 16 16  0 0 None
0x113  0 sg  0 16  0    y  . 16  0  0  0  4 24  8 16 16 16 16  0 0 None
0x114  0 sg  0 64  0 r  .  . 32 32  0  0  4 24  0 16 16 16 16  0 0 None
0x115  0 sg  0 64  0    .  . 32 32  0  0  4 24  0 16 16 16 16  0 0 None
0x116  0 sg  0 64  0 r  y  . 32 32  0  0  4 24  0 16 16 16 16  0 0 None
0x117  0 sg  0 64  0    y  . 32 32  0  0  4 24  0 16 16 16 16  0 0 None
0x118  0 sg  0 64  0 r  .  . 32 32  0  0  4 24  8 16 16 16 16  0 0 None
0x119  0 sg  0 64  0    .  . 32 32  0  0  4 24  8 16 16 16 16  0 0 None
0x11a  0 sg  0 64  0 r  y  . 32 32  0  0  4 24  8 16 16 16 16  0 0 None
0x11b  0 sg  0 64  0    y  . 32 32  0  0  4 24  8 16 16 16 16  0 0 None

```

and my xorg.conf looks so:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Sun Nov 22 19:20:57 PST 2009

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder58)  Sun Nov 22 19:22:06 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       26.0 - 81.0
    VertRefresh     24.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9300 / nForce 730i"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

and the output from glxgears:
```

16026 frames in 5.0 seconds
16161 frames in 5.0 seconds
15928 frames in 5.0 seconds

```

and the output from compiz start
```

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1920x1080) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

and after switching back to metacity
```
*** glibc detected *** /usr/bin/compiz.real: corrupted double-linked list: 0x00000000013cd4c0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f94fa8b9dd6]
/lib/libc.so.6[0x7f94fa8bb8a2]
/lib/libc.so.6(cfree+0x6c)[0x7f94fa8be70c]
/usr/lib/libGL.so.1[0x7f94fb0ccbe8]
======= Memory map: ========
00400000-0043c000 r-xp 00000000 08:01 326955                             /usr/bin/compiz.real
0063b000-0063c000 r--p 0003b000 08:01 326955                             /usr/bin/compiz.real
0063c000-0063d000 rw-p 0003c000 08:01 326955                             /usr/bin/compiz.real
00a2b000-03ac8000 rw-p 00000000 00:00 0                                  [heap]
7f94e991a000-7f94eb0d8000 rw-p 00000000 00:00 0 
7f94ec000000-7f94ec021000 rw-p 00000000 00:00 0 
7f94ec021000-7f94f0000000 ---p 00000000 00:00 0 
7f94f340e000-7f94f341a000 r-xp 00000000 08:01 183398                     /lib/libnss_files-2.10.1.so
7f94f341a000-7f94f3619000 ---p 0000c000 08:01 183398                     /lib/libnss_files-2.10.1.so
7f94f3619000-7f94f361a000 r--p 0000b000 08:01 183398                     /lib/libnss_files-2.10.1.so
7f94f361a000-7f94f361b000 rw-p 0000c000 08:01 183398                     /lib/libnss_files-2.10.1.so
7f94f361b000-7f94f3625000 r-xp 00000000 08:01 183400                     /lib/libnss_nis-2.10.1.so
7f94f3625000-7f94f3824000 ---p 0000a000 08:01 183400                     /lib/libnss_nis-2.10.1.so
7f94f3824000-7f94f3825000 r--p 00009000 08:01 183400                     /lib/libnss_nis-2.10.1.so
7f94f3825000-7f94f3826000 rw-p 0000a000 08:01 183400                     /lib/libnss_nis-2.10.1.so
7f94f3826000-7f94f383c000 r-xp 00000000 08:01 183395                     /lib/libnsl-2.10.1.so
7f94f383c000-7f94f3a3c000 ---p 00016000 08:01 183395                     /lib/libnsl-2.10.1.so
7f94f3a3c000-7f94f3a3d000 r--p 00016000 08:01 183395                     /lib/libnsl-2.10.1.so
7f94f3a3d000-7f94f3a3e000 rw-p 00017000 08:01 183395                     /lib/libnsl-2.10.1.so
7f94f3a3e000-7f94f3a40000 rw-p 00000000 00:00 0 
7f94f3a40000-7f94f3a47000 r-xp 00000000 08:01 183396                     /lib/libnss_compat-2.10.1.so
7f94f3a47000-7f94f3c47000 ---p 00007000 08:01 183396                     /lib/libnss_compat-2.10.1.so
7f94f3c47000-7f94f3c48000 r--p 00007000 08:01 183396                     /lib/libnss_compat-2.10.1.so
7f94f3c48000-7f94f3c49000 rw-p 00008000 08:01 183396                     /lib/libnss_compat-2.10.1.so
7f94f3c49000-7f94f3c76000 r-xp 00000000 08:01 179302                     /lib/libpcre.so.3.12.1
7f94f3c76000-7f94f3e75000 ---p 0002d000 08:01 179302                     /lib/libpcre.so.3.12.1
7f94f3e75000-7f94f3e76000 r--p 0002c000 08:01 179302                     /lib/libpcre.so.3.12.1
7f94f3e76000-7f94f3e77000 rw-p 0002d000 08:01 179302                     /lib/libpcre.so.3.12.1
7f94f3e77000-7f94f3ebb000 r-xp 00000000 08:01 326462                     /usr/lib/libgobject-2.0.so.0.2200.2
7f94f3ebb000-7f94f40bb000 ---p 00044000 08:01 326462                     /usr/lib/libgobject-2.0.so.0.2200.2
7f94f40bb000-7f94f40bc000 r--p 00044000 08:01 326462                     /usr/lib/libgobject-2.0.so.0.2200.2
7f94f40bc000-7f94f40bd000 rw-p 00045000 08:01 326462                     /usr/lib/libgobject-2.0.so.0.2200.2
7f94f40bd000-7f94f40be000 rw-p 00000000 00:00 0 
7f94f40be000-7f94f40c5000 r-xp 00000000 08:01 183405                     /lib/librt-2.10.1.so
7f94f40c5000-7f94f42c4000 ---p 00007000 08:01 183405                     /lib/librt-2.10.1.so
7f94f42c4000-7f94f42c5000 r--p 00006000 08:01 183405                     /lib/librt-2.10.1.so
7f94f42c5000-7f94f42c6000 rw-p 00007000 08:01 183405                     /lib/librt-2.10.1.so
7f94f42c6000-7f94f4303000 r-xp 00000000 08:01 179198                     /lib/libdbus-1.so.3.4.0
7f94f4303000-7f94f4503000 ---p 0003d000 08:01 179198                     /lib/libdbus-1.so.3.4.0
7f94f4503000-7f94f4504000 r--p 0003d000 08:01 179198                     /lib/libdbus-1.so.3.4.0
7f94f4504000-7f94f4505000 rw-p 0003e000 08:01 179198                     /lib/libdbus-1.so.3.4.0
7f94f4505000-7f94f4525000 r-xp 00000000 08:01 327384                     /usr/lib/libdbus-glib-1.so.2.1.0
7f94f4525000-7f94f4725000 ---p 00020000 08:01 327384                     /usr/lib/libdbus-glib-1.so.2.1.0
7f94f4725000-7f94f4726000 r--p 00020000 08:01 327384                     /usr/lib/libdbus-glib-1.so.2.1.0
7f94f4726000-7f94f4727000 rw-p 00021000 08:01 327384                     /usr/lib/libdbus-glib-1.so.2.1.0
7f94f4727000-7f94f472b000 r-xp 00000000 08:01 327946                     /usr/lib/libgthread-2.0.so.0.2200.2
7f94f472b000-7f94f492a000 ---p 00004000 08:01 327946                     /usr/lib/libgthread-2.0.so.0.2200.2
7f94f492a000-7f94f492b000 r--p 00003000 08:01 327946                     /usr/lib/libgthread-2.0.so.0.2200.2
7f94f492b000-7f94f492c000 rw-p 00004000 08:01 327946                     /usr/lib/libgthread-2.0.so.0.2200.2
7f94f492c000-7f94f4988000 r-xp 00000000 08:01 327218                     /usr/lib/libORBit-2.so.0.1.0
7f94f4988000-7f94f4b88000 ---p 0005c000 08:01 327218                     /usr/lib/libORBit-2.so.0.1.0
7f94f4b88000-7f94f4b97000 r--p 0005c000 08:01 327218                     /usr/lib/libORBit-2.so.0.1.0
7f94f4b97000-7f94f4b9a000 rw-p 0006b000 08:01 327218                     /usr/lib/libORBit-2.so.0.1.0
7f94f4b9a000-7f94f4b9d000 r-xp 00000000 08:01 327923                     /usr/lib/libgmodule-2.0.so.0.2200.2
7f94f4b9d000-7f94f4d9c000 ---p 00003000 08:01 327923                     /usr/lib/libgmodule-2.0.so.0.2200.2
7f94f4d9c000-7f94f4d9d000 r--p 00002000 08:01 327923                     /usr/lib/libgmodule-2.0.so.0.2200.2
7f94f4d9d000-7f94f4d9e000 rw-p 00003000 08:01 327923                     /usr/lib/libgmodule-2.0.so.0.2200.2
7f94f4d9e000-7f94f4e63000 r-xp 00000000 08:01 180513                     /lib/libglib-2.0.so.0.2200.2
7f94f4e63000-7f94f5062000 ---p 000c5000 08:01 180513                     /lib/libglib-2.0.so.0.2200.2
7f94f5062000-7f94f5063000 r--p 000c4000 08:01 180513                     /lib/libglib-2.0.so.0.2200.2
7f94f5063000-7f94f5064000 rw-p 000c5000 08:01 180513                     /lib/libglib-2.0.so.0.2200.2
7f94f5064000-7f94f5065000 rw-p 00000000 00:00 0 
7f94f5065000-7f94f509d000 r-xp 00000000 08:01 326085                     /usr/lib/libgconf-2.so.4.1.5
7f94f509d000-7f94f529d000 ---p 00038000 08:01 326085                     /usr/lib/libgconf-2.so.4.1.5
7f94f529d000-7f94f529f000 r--p 00038000 08:01 326085                     /usr/lib/libgconf-2.so.4.1.5Aborted

```

i was running the compiz check script with success.

Nothing interesting in Xorg.0.log

best regards

sagi

---

