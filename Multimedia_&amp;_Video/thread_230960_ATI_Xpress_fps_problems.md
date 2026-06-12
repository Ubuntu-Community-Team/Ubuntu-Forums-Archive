---
title: "ATI Xpress fps problems"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by Th3_j3st3r on 2006-08-06
So now I have finally gotten my ati drivers loaded and working. I just recently gotten Cedega for my gaming and after installing warcraft 3 its slow AND no sound. Well mainly I would like to fix the fps then worry later about sound. So please check out my info and maybe provide me with some direction here. Ive been trying to solve this for a week now, its so frustrating.:confused: 

Specs:
Ati Radeon Xpress 200m
Ubuntu dapper 
kernel 2.6.15-26-686

#dmesg | grep fglrx
```

[17179609.372000] [fglrx] Maximum main memory to use for locked dma buffers: 313 MBytes.
[17179609.372000] [fglrx] module loaded - fglrx 8.27.10 [Jul 27 2006] on minor 0
[17179612.368000] [fglrx] total      GART = 134217728
[17179612.368000] [fglrx] free       GART = 118226944
[17179612.368000] [fglrx] max single GART = 118226944
[17179612.368000] [fglrx] total      LFB  = 128839680
[17179612.368000] [fglrx] free       LFB  = 122548224
[17179612.368000] [fglrx] max single LFB  = 122548224
[17179612.368000] [fglrx] total      Inv  = 0
[17179612.368000] [fglrx] free       Inv  = 0
[17179612.368000] [fglrx] max single Inv  = 0
[17179612.368000] [fglrx] total      TIM  = 0

```

#glxinfo
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5946 (8.27.10)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3,
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess


```

#fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5946 (8.27.10)

#glxgears -printfps
605 frames in 5.0 seconds = 120.836 FPS
607 frames in 5.0 seconds = 121.393 FPS
617 frames in 5.0 seconds = 123.293 FPS
616 frames in 5.0 seconds = 123.195 FPS

---

### Post by Th3_j3st3r on 2006-08-06
Here is my xorg.conf

---

