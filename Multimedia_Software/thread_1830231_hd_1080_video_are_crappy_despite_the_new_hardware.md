---
title: "hd 1080 video are crappy despite the new hardware"
date: 2011-08-21
forum: Multimedia Software
---

### Post by ilcontegis on 2011-08-21
Dear all

I could finally make my new desktop pc (asus p8p67 motherboard, core i5 2500, 8gb ram and a nvidia gtx570).
Up to now I had an old ati and I could watch only up to 720p. But at least I could watch it smoothly.
The new video card does not work so well.
I installed the nvidia proprietary drivers (I use ubuntu 11.04 64bit) and vlc and mplayer do not play well my videos in 720 and 1080. Especially when fast scenes are occurring I can see like some horizontal lines. The reproduction is not smooth and that's really annoying.
Also xbmc has the same issue.
I tried to install the following (I saw it from a post in this forum)
```
libvdpau1 nvidia-185-libvdpau
```
but then vlc was same, mplayer was over slow and xbmc also (in xbmc I almost could not move the mouse)
I then delete the above described packages and I instaled the following one (as I read from another topic)
```
vdpau-va-driver
```
Same issue.

Follows glxinfo
```
teo@teo:~$ glxinfo 
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
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
    GLX_NV_video_capture, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 570/PCI/SSE2
OpenGL version string: 4.1.0 NVIDIA 270.41.06
OpenGL shading language version string: 4.10 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_blend_func_extended, GL_ARB_color_buffer_float, 
    GL_ARB_compatibility, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_indirect, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_ES2_compatibility, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, GL_ARB_gpu_shader5, 
    GL_ARB_gpu_shader_fp64, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_imaging, GL_ARB_instanced_arrays, GL_ARB_map_buffer_range, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_provoking_vertex, 
    GL_ARB_robustness, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_objects, 
    GL_ARB_shader_precision, GL_ARB_shader_subroutine, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_include, 
    GL_ARB_shadow, GL_ARB_sync, GL_ARB_tessellation_shader, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_buffer_object_rgb32, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_bptc, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_cube_map_array, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_swizzle, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_64bit, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
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
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_format_BGRA8888, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_texture_type_2_10_10_10_REV, 
    GL_EXT_timer_query, GL_EXT_transform_feedback2, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_EXT_vertex_attrib_64bit, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_alpha_test, GL_NV_blend_minmax, 
    GL_NV_blend_square, GL_NV_complex_primitives, GL_NV_conditional_render, 
    GL_NV_copy_depth_to_color, GL_NV_copy_image, GL_NV_depth_buffer_float, 
    GL_NV_depth_clamp, GL_NV_explicit_multisample, 
    GL_NV_fbo_color_attachments, GL_NV_fence, GL_NV_float_buffer, 
    GL_NV_fog_distance, GL_NV_fragdepth, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_geometry_shader4, 
    GL_NV_gpu_program4, GL_NV_gpu_program4_1, GL_NV_gpu_program5, 
    GL_NV_gpu_program_fp64, GL_NV_gpu_shader5, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_shader_buffer_load, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_lod_clamp, 
    GL_NV_texture_multisample, GL_NV_texture_rectangle, GL_NV_texture_shader, 
    GL_NV_texture_shader2, GL_NV_texture_shader3, GL_NV_transform_feedback, 
    GL_NV_transform_feedback2, GL_NV_vdpau_interop, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_attrib_integer_64bit, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_OES_depth24, 
    GL_OES_depth32, GL_OES_depth_texture, GL_OES_element_index_uint, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
    GL_OES_packed_depth_stencil, GL_OES_rgb8_rgba8, 
    GL_OES_standard_derivatives, GL_OES_texture_3D, GL_OES_texture_float, 
    GL_OES_texture_float_linear, GL_OES_texture_half_float, 
    GL_OES_texture_half_float_linear, GL_OES_texture_npot, 
    GL_OES_vertex_array_object, GL_OES_vertex_half_float, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

```

Also check this please
```
teo@teo:~$ mplayer -vo vdpau -ao alsa file.avi
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing file.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
AVI: ODML: Building ODML index (2 superindexchunks).
VIDEO:  [XVID]  1920x816  12bpp  23.976 fps  6745.6 kbps (823.4 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [vdpau] 1920x816 => 1920x816 Planar YV12 
A:  13.6 V:   2.1 A-V: 11.542 ct: -0.023  51/ 51 24% 656%  1.9% 50 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:  24.9 V:   3.8 A-V: 21.182 ct: -0.024  91/ 91 14% 665%  1.9% 90 0 
Exiting... (Quit)

```

I do not know what to try else.
I am very disappointed, I really hope you can help me to solve this issue.
Thank you for your time
Regards

---

### Post by 1clue on 2011-08-21
Not an expert here, but my GT200 powers two 1080p monitors and I don't get the problem.  Presumably your hardware is better.

What is your video source?  Are you playing an HD DVD or are you loading something through the network?  If you're trying to watch online video then I suspect you'll have quality problems at least part of the time.

If you're watching from a source on your hard disk everything should be good.

I'm not using the proprietary driver, because the darned thing won't turn on.  Have no idea how to do it, I've followed the instructions but the thing shows as "installed but not used."  So maybe try using the nv driver?

---

### Post by ilcontegis on 2011-08-21
@1clue

I am playing files from my hard disk.:(

---

### Post by drawkcab on 2011-08-21
purge and reinstall ffmpeg

i have this hypothesis that kernel updates have something to do with this tearing

---

### Post by ilcontegis on 2011-08-21
> **drawkcab said:**
> purge and reinstall ffmpeg

i have this hypothesis that kernel updates have something to do with this tearing
Thank you for the answer.
I did what you suggested. now mplayer works as smoothly as vlc, however I still have the issue reported in the first post: when scenes with rapid movements occur I see horizontal lines on the screen. I can still watch the movie but it is not perfect and as good as it should be with the pc I built.
Do you have any other idea?
Shall I try a clean install? I just put away mb, ram, cpu and gpu and changed to the new ones. Maybe my poor ubuntu is a bit messed up.

---

### Post by WasMeHere on 2011-09-11
I think it could be solved via software similar to what I have experienced trying to sqeeze 1080/50p through my hardware. Anyway, I use VLC and activate
1. GPU acceleration,
2. minimize video quality post-processing level and
3. skip all H.264 in-loop deblocking
according to the attached screen-dump.

If that is not enough, you can run VLC with the following options
```
alias vlcmts='vlc --rt-priority --rate 0.9'
``` either from a terminal (alias can be set in .bashrc) or as a user-defined command for the appropriate file type in Nautilus:
*Properties - Open with - Add -*
```
/usr/bin/vlc --rt-priority --rate 0.9
```

Good luck
Olle

[I]Edit 1: I run an hp xw8400 workstation with zeon processors and nvidia graphics card with dual boot, 'ubuntu studio real-time' and 'windows xp'. **Now I have managed to get 'perfect' playback of 1080/50p video with VLC in xp**, while I still have to run it at rate 0.9 (90% of original speed) in studio. I have also tried several other linux distros, but none (except xp) has surpassed studio (using VLC).

By the way, my video camera itself can play 1080/50p, but the proprietary software that came with my camera cannot play it back without reduced frame rate in the xw8400. I guess that software does not use the GPU, but it did probe for and suggest installation of the latest version of direct x.

Edit 2: **Now I have managed to get 'almost perfect' playback of 1080/50p video with mplayer in Ubuntu Studio** thanks to a tip originally posted by **shirilover** in 2008.
```
mplayer -lavdopts fast:threads=3 <filename>
```
[/I]

---

