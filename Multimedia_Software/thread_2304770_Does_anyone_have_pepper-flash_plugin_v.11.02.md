---
title: "Does anyone have pepper-flash plugin v.11.02?"
date: 2015-11-29
forum: Multimedia Software
---

### Post by steve234 on 2015-11-29
Evening,

I'm nearly at a point where I can use Chromium (v.45) for all of my browsing needs - however the current pepper-flash version in the Ubuntu repo for 14.04 is flash 19:

```
 $ sudo update-pepperflashplugin-nonfree --statusFlash Player version installed on this system  : 19.0.0.245
Flash Player version available on upstream site: 19.0.0.245

``` 

Flash 19 works like cr*p on my system. The framerate is awful - like under 1 fps awful. In all other browsers flash 11.2 is working brilliantly.

I see that there was once a flash 11.2 version of pepper but I can't find that version online. Does anyone have it? or alternatively know of a way I can get Chromium to use Flash 11.2?

---

### Post by steve234 on 2015-11-30
Update - I've tried the flash plugin from Google Chrome 27 (version 11.7) using ```
--ppapi-flash-path
``` and ```
--ppapi-flash-version
``` flags.

It loads videos and shows as the correct version in the browser fine but the plugin itself doesn't work well - I think I need the binary of google  chrome 20 - 23 to get v 11.2 of pepperflash.

---

### Post by Yellow Pasque on 2015-11-30
I would look for a solution to make Flash 19.x run better rather than trying to extract an old version out of Chrome. Any 11.x Flash you get out of Chrome will be full of security holes since it did not receive the updates that the Firefox/NPAPI 11.2.x branch did.

Can you copy/paste the output of chrome://gpu here (please use code tags)?

---

### Post by steve234 on 2015-11-30
That was what my old thread essentially boiled down to - but that one stagnated - I marked it solved as I worked out how to roll back to 11.2. 

I'd love to get Flash 19 working properly but it seemed to be a system wide issue accross all browsers. 11.2 on the other hand plays videos brilliantly. 

Output from Chrome://gpu as requested:

```
 [COLOR=#000000][FONT=sans-serif][h=3]Graphics Feature Status[/h]
[LIST]
[*]Canvas: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Flash: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Flash Stage3D Baseline profile: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Compositing: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Multiple Raster Threads: [COLOR=#008000]Force enabled[/COLOR]
[*]Rasterization: [COLOR=#808000]Software only. Hardware acceleration disabled[/COLOR]
[*]Video Decode: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Video Encode: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]WebGL: [COLOR=#008000]Hardware accelerated[/COLOR]
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]Driver Bug Workarounds[/h]
[LIST]
[*]clear_uniforms_before_first_program_use
[*]count_all_in_varyings_packing
[*]disable_post_sub_buffers_for_onscreen_surfaces
[*]scalarize_vec_and_mat_constructor_args
[*]use_virtualized_gl_contexts
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]Problems Detected[/h]
[LIST]
[*]Accelerated 2d canvas is unstable in Linux at the moment
*Disabled Features: [COLOR=#FF0000]accelerated_2d_canvas[/COLOR]*
[*][I]Accelerated video decode is unavailable on Linux: [137247]("http://crbug.com/137247")
*Disabled Features: [COLOR=#FF0000]accelerated_video_decode[/COLOR]*[/I]
[*]*[I]EXT_occlusion_query appears to be buggy with Intel GPUs on Linux*[/I]
[*][I][I]Clear uniforms before first program use on all platforms: [124764]("http://crbug.com/124764"), [349137]("http://crbug.com/349137")
*Applied Workarounds: [COLOR=#808000]clear_uniforms_before_first_program_use[/COLOR]*[/I][/I]
[*][I][I][I]Mesa drivers in Linux handle varyings without static use incorrectly: [333885]("http://crbug.com/333885")
*Applied Workarounds: [COLOR=#808000]count_all_in_varyings_packing[/COLOR]*[/I][/I][/I]
[*][I][I][I]Disable partial swaps on linux drivers: [339493]("http://crbug.com/339493")
*Applied Workarounds: [COLOR=#808000]disable_post_sub_buffers_for_onscreen_surfaces[/COLOR]*[/I][/I][/I]
[*][I][I][I]Always rewrite vec/mat constructors to be consistent: [398694]("http://crbug.com/398694")
*Applied Workarounds: [COLOR=#808000]scalarize_vec_and_mat_constructor_args[/COLOR]*[/I][/I][/I]
[*][I][I][I]MakeCurrent is slow on Linux
*Applied Workarounds: [COLOR=#808000]use_virtualized_gl_contexts[/COLOR]*[/I][/I][/I]
[*][I][I][I]Accelerated rasterization has been disabled, either via about:flags or command line.
*Disabled Features: [COLOR=#FF0000]rasterization[/COLOR]*[/I][/I][/I]
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]*[I][I]Version Information*[/I][/I][/h][TABLE="width: 991"]
[TR]
[TD]**Data exported**[/TD]
[TD]30/11/2015, 15:31:27[/TD]
[/TR]
[TR]
[TD]**Chrome version**[/TD]
[TD]Chrome/45.0.2454.101[/TD]
[/TR]
[TR]
[TD]**Operating system**[/TD]
[TD]Linux 3.19.0-31-generic[/TD]
[/TR]
[TR]
[TD]**Software rendering list version**[/TD]
[TD]10.9[/TD]
[/TR]
[TR]
[TD]**Driver bug list version**[/TD]
[TD]8.19[/TD]
[/TR]
[TR]
[TD]**ANGLE commit id**[/TD]
[TD]unknown hash[/TD]
[/TR]
[TR]
[TD]**2D graphics backend**[/TD]
[TD]Skia[/TD]
[/TR]
[TR]
[TD]**Command Line Args**[/TD]
[TD]--enable-pinch --flag-switches-begin --enable-experimental-canvas-features --enable-fast-unload --max-tiles-for-interest-area=512 --num-raster-threads=4 --flag-switches-end[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]*[I][I]Driver Information*[/I][/I][/h][TABLE="width: 991"]
[TR]
[TD]**Initialization time**[/TD]
[TD]1844[/TD]
[/TR]
[TR]
[TD]**Sandboxed**[/TD]
[TD]true[/TD]
[/TR]
[TR]
[TD]**GPU0**[/TD]
[TD]VENDOR = 0x8086, DEVICE= 0xa011[/TD]
[/TR]
[TR]
[TD]**Optimus**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**AMD switchable**[/TD]
[TD]false[/TD]
[/TR]
[TR]
[TD]**Driver vendor**[/TD]
[TD]Mesa[/TD]
[/TR]
[TR]
[TD]**Driver version**[/TD]
[TD]10.5.9[/TD]
[/TR]
[TR]
[TD]**Driver date**[/TD]
[TD]
[/TD]
[/TR]
[TR]
[TD]**Pixel shader version**[/TD]
[TD]1.20[/TD]
[/TR]
[TR]
[TD]**Vertex shader version**[/TD]
[TD]1.20[/TD]
[/TR]
[TR]
[TD]**Max. MSAA samples**[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]**Machine model name**[/TD]
[TD]
[/TD]
[/TR]
[TR]
[TD]**Machine model version**[/TD]
[TD]
[/TD]
[/TR]
[TR]
[TD]**GL_VENDOR**[/TD]
[TD]Intel Open Source Technology Center[/TD]
[/TR]
[TR]
[TD]**GL_RENDERER**[/TD]
[TD]Mesa DRI Intel(R) IGD x86/MMX/SSE2[/TD]
[/TR]
[TR]
[TD]**GL_VERSION**[/TD]
[TD]1.4 Mesa 10.5.9[/TD]
[/TR]
[TR]
[TD]**GL_EXTENSIONS**[/TD]
[TD]GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_rectangle GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_gpu_program_parameters GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_map_buffer_range GL_ARB_ES2_compatibility GL_ARB_debug_output GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_EXT_provoking_vertex GL_ARB_get_program_binary GL_ARB_robustness GL_ARB_separate_shader_objects GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_compressed_texture_pixel_storage GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_texture_storage GL_AMD_shader_trinary_minmax GL_ARB_clear_buffer_object GL_ARB_explicit_uniform_location GL_ARB_invalidate_subdata GL_ARB_vertex_attrib_binding GL_KHR_debug GL_ARB_multi_bind GL_KHR_context_flush_control[/TD]
[/TR]
[TR]
[TD]**Disabled Extensions**[/TD]
[TD]GL_ARB_occlusion_query GL_ARB_occlusion_query2[/TD]
[/TR]
[TR]
[TD]**Window system binding vendor**[/TD]
[TD]SGI[/TD]
[/TR]
[TR]
[TD]**Window system binding version**[/TD]
[TD]1.4[/TD]
[/TR]
[TR]
[TD]**Window system binding extensions**[/TD]
[TD]GLX_ARB_create_context GLX_ARB_create_context_profile GLX_ARB_fbconfig_float GLX_ARB_framebuffer_sRGB GLX_ARB_multisample GLX_EXT_create_context_es2_profile GLX_EXT_framebuffer_sRGB GLX_EXT_import_context GLX_EXT_texture_from_pixmap GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_OML_swap_method GLX_SGI_swap_control GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGIX_visual_select_group GLX_INTEL_swap_event[/TD]
[/TR]
[TR]
[TD]**Window manager**[/TD]
[TD]Openbox[/TD]
[/TR]
[TR]
[TD]**GDMSESSION**[/TD]
[TD]openbox[/TD]
[/TR]
[TR]
[TD]**Compositing manager**[/TD]
[TD]No[/TD]
[/TR]
[TR]
[TD]**Direct rendering**[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]**Reset notification strategy**[/TD]
[TD]0x8261[/TD]
[/TR]
[TR]
[TD]**GPU process crash count**[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
 
```

---

### Post by Yellow Pasque on 2015-11-30
> Accelerated video decode is unavailable on Linux: [https://code.google.com/p/chromium/issues/detail?id=137247](https://code.google.com/p/chromium/issues/detail?id=137247)
^I'm guessing that's causing the issue. It looks like you have an Atom CPU and it can't handle playback alone. Maybe you can try starting chromium like so to force GPU assist:
```
chromium --ignore-gpu-blacklist --enable-vaapi
```

If it doesn't help, make sure your va-api is working correctly. vainfo should give you a list of supported profiles:
```
sudo apt-get install vainfo
vainfo
```

Other than that, I think I'm out of suggestions.

---

### Post by steve234 on 2015-11-30
The forced GPU assist gave me sound, and the occasional frame for video:

vainfo just threw errors - I thought it was because it needed SU rights, but that wasn't the case:

```
$ vainfo
libva info: VA-API version 0.35.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/i386-linux-gnu/dri/i915_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

$ sudo vainfo
error: XDG_RUNTIME_DIR not set in the environment.
libva info: VA-API version 0.35.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/i386-linux-gnu/dri/i915_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

 
```

---

