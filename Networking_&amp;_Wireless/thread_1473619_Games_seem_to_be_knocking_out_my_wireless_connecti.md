---
title: "Games seem to be knocking out my wireless connection"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by kaldor on 2010-05-05
First happened on Nexuiz. Installed Alien Arena and OpenArena and they have the same issue.

When I try to load the server list or press refresh, my wireless connection drops and the game says no response from the master list. This never happened on Hardy/Intrepid.

I am on Lucid.

It seems to only be on native Quake-based games, as other games such as Wesnoth and Quake-based games in WINE work fine. It's getting frustrating to be unable to play these games online.

Edit: Maybe this will help..

```
michael@laptop:~$ openarena
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ioq3+oa 1.35 linux-i386 Dec 18 2009
----- FS_Startup -----
Current search path:
/home/michael/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (1042 files)
/usr/share/games/openarena/baseoa

----------------------
4163 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.600
...setting mode 4: 800 600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
Available modes: '1280x800 720x450 840x525 800x512 680x384 960x540 320x240 400x300 512x384 576x432 640x480 700x525 800x600 1024x768 640x512'
GL_RENDERER: GeForce 8400M GS/PCI/SSE2
Initializing OpenGL extensions
...ignoring GL_EXT_texture_compression_s3tc
...ignoring GL_S3_s3tc
...using GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 8400M GS/PCI/SSE2
GL_VERSION: 2.1.2 NVIDIA 173.14.22
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_TEXTURE_UNITS_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
------ Initializing Sound ------
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Allocated 96 sources.
OpenAL default capture device is 'PulseAudio Capture'
OpenAL capture device opened.
OpenAL info:
  Vendor:     OpenAL Community
  Version:    1.1 ALSOFT 1.11.753
  Renderer:   OpenAL Soft
  AL Extensions: AL_EXTX_buffer_sub_data AL_EXT_EXPONENT_DISTANCE AL_EXT_FLOAT32 AL_EXT_IMA4 AL_EXT_LINEAR_DISTANCE AL_EXT_MCFORMATS AL_EXT_OFFSET AL_EXTX_sample_buffer_object AL_EXT_source_distance_model AL_LOKI_quadriphonic
  ALC Extensions: ALC_ENUMERATE_ALL_EXT ALC_ENUMERATION_EXT ALC_EXT_CAPTURE ALC_EXT_disconnect ALC_EXT_EFX ALC_EXTX_thread_local_context
  Device:     PulseAudio Software
Available Devices:
PulseAudio Software
ALSA Software
OSS Software
PortAudio Software
Sound initialization successful.
--------------------------------
Loading vm file vm/ui.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1349 jump table targets
VM file ui compiled to 644411 bytes of code
ui loaded in 1398048 bytes on the hunk
41 arenas parsed
24 bots parsed
--- Common Initialization Complete ---
IP: 127.0.0.1
IP6: ::1
IP6: 2002:c0a8:20a:1234:21f:3bff:fe20:689b
IP6: fe80::21f:3bff:fe20:689b%wlan0
Opening IP6 socket: [::]:27960
Opening IP socket: 0.0.0.0:27960
Sys_StringToSockaddr: Error resolving dpmaster.deathmask.net: No address associated with hostname
CL_GlobalServers_f: Error: could not resolve address of master dpmaster.deathmask.net
Requesting servers from master dpmaster.deathmask.net...
Sys_StringToSockaddr: Error resolving dpmaster.deathmask.net: No address associated with hostname
CL_GlobalServers_f: Error: could not resolve address of master dpmaster.deathmask.net
]\quit
----- CL_Shutdown -----
OpenAL capture device closed.
RE_Shutdown( 1 )
-----------------------

```

---

### Post by kaldor on 2010-05-05
*bump!*

I could really use some help on this :(

---

### Post by nsbanon on 2010-05-15
I need some help with this issue as well. When ever I try to go online in Urban Terror or Nexuiz it kicks me off my wireless connection.

---

### Post by altonbr on 2010-07-08
I have similar problems with OpenArena and posted the problem on their site: [http://openarena.ws/board/index.php?topic=3833.0](http://openarena.ws/board/index.php?topic=3833.0)

---

