---
title: "howto: get acceleration with free ati drivers on dapper"
date: 2006-06-16
forum: Multimedia &amp; Video
---

### Post by dani666 on 2006-06-16
I got a lot of errors when I tried to get acceleration with fglrx. My ati is a radeon 9200 PRO, and it haves problems with free drivers too, to get acceleration you have to install the newest kernel, because the Ubuntu kernel haves problems with the radeon driver (Xorg 7). To do it:

1.- Remove the fglrx
2.- Reinstall xserver-xorg from synaptic
3.- Compile your kernel

Don't add anything to /etc/X11/xorg.conf, because it's already configured by the reinstallation

Planet Penguin Racer and something else like that, works fine.
It's what I get when I run "glxgears -info"
________________________________

GL_RENDERER   = Mesa DRI R200 20060602 AGP 4x TCL
GL_VERSION    = 1.3 Mesa 6.5.1
GL_VENDOR     = Tungsten Graphics, Inc.
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_fragment_shader GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
7860 frames in 5.0 seconds = 1571.962 FPS
7875 frames in 5.0 seconds = 1574.894 FPS
7878 frames in 5.0 seconds = 1575.565 FPS

________________________________

PS. I'm sorry about my english

---

### Post by tseliot on 2006-06-16
> 3.- Compile your kernel

Do you mean from Vanilla sources?

---

