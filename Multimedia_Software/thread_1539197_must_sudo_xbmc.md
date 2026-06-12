---
title: "must sudo xbmc"
date: 2010-07-26
forum: Multimedia Software
---

### Post by JohnnyC35 on 2010-07-26
I have a very odd issue. I tried running xbmc and it gave me an error about not having opengl loaded. I have the updated 256 nvidia drivers. when I ran "glxinfo | grep -i direct" I got:
> 
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

and when i typed "sudo glxinfo | grep -i direct" I got:
> 
direct rendering: Yes
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 


so  tried sudo xbmc, and it runs. ... :confused:

is there a way to not have to sudo xbmc everytime?

I just tried running xbmc in the terminal without sudo and it gave an error:
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).

I checked and I am part of the video group. I set it so that others can read/write it. Then I got this error:
NVIDIA: could not open the device file /dev/nvidia0 (Permission denied).

So I read/write nvidia0 and got:
> 
/usr/bin/xbmc: line 88: 32590 Segmentation fault      (core dumped) /usr/share/xbmc/xbmc.bin "$@"
Crash report available at /home/john/xbmc_crashlog-20100726_092946.log


xbmc's crash log =
> 
############## XBMC CRASH LOG ###############

################ SYSTEM INFO ################
 Date: Mon Jul 26 09:29:46 EDT 2010
 XBMC Options: 
 Arch: i686
 Kernel: Linux 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010
 Release: 
    Distributor ID:    Ubuntu
    Description:    Ubuntu 10.04.1 LTS
    Release:    10.04
    Codename:    lucid
############## END SYSTEM INFO ##############

############### STACK TRACE #################
=====>  Core file: /home/john/core
        ========================================= 
############# END STACK TRACE ###############

################# LOG FILE ##################

09:15:53 T:3057190784 M:2453626880  NOTICE: -----------------------------------------------------------------------
09:15:53 T:3057190784 M:2453626880  NOTICE: Starting XBMC, Platform: GNU/Linux.  Built on May 23 2010 (SVN:26018)
09:15:53 T:3057190784 M:2453626880  NOTICE: special://xbmc/ is mapped to: /usr/share/xbmc
09:15:53 T:3057190784 M:2453626880  NOTICE: special://masterprofile/ is mapped to: /home/john/.xbmc/userdata
09:15:53 T:3057190784 M:2453626880  NOTICE: special://home/ is mapped to: /home/john/.xbmc
09:15:53 T:3057190784 M:2453626880  NOTICE: special://temp/ is mapped to: /home/john/.xbmc/temp
09:15:53 T:3057190784 M:2453626880  NOTICE: The executable running is: /usr/lib/xbmc/xbmc.bin
09:15:53 T:3057190784 M:2453626880  NOTICE: Log File is located: /home/john/.xbmc/temp/xbmc.log
09:15:53 T:3057190784 M:2453626880  NOTICE: -----------------------------------------------------------------------
09:15:53 T:3057190784 M:2453880832  NOTICE: Setup SDL
09:15:53 T:3057190784 M:2453495808  NOTICE: load settings...
09:15:53 T:3057190784 M:2453495808  NOTICE: special://profile/ is mapped to: special://masterprofile/
09:15:53 T:3057190784 M:2453495808  NOTICE: loading special://masterprofile/guisettings.xml
09:15:53 T:3057190784 M:2453495808   ERROR: Unable to load special://masterprofile/guisettings.xml, creating new special://masterprofile/guisettings.xml with default values
09:15:53 T:3057190784 M:2453721088  NOTICE: Getting hardware information now...
09:15:53 T:3057190784 M:2453721088  NOTICE: Checking resolution 12
09:15:53 T:3057190784 M:2453721088  NOTICE: Loading player core factory settings from special://xbmc/system/playercorefactory.xml.
09:15:53 T:3057190784 M:2453721088  NOTICE: Loaded playercorefactory configuration
09:15:53 T:3057190784 M:2453721088  NOTICE: Loading player core factory settings from special://masterprofile/playercorefactory.xml.
09:15:53 T:3057190784 M:2453721088  NOTICE: special://masterprofile/playercorefactory.xml does not exist. Skipping.
09:15:53 T:3057190784 M:2453721088  NOTICE: No advancedsettings.xml to load (special://masterprofile/advancedsettings.xml)
09:15:53 T:3057190784 M:2453721088  NOTICE: Default DVD Player: dvdplayer
09:15:53 T:3057190784 M:2453721088  NOTICE: Default Video Player: dvdplayer
09:15:53 T:3057190784 M:2453721088  NOTICE: Default Audio Player: paplayer
09:15:53 T:3057190784 M:2453721088  NOTICE: special://masterprofile/sources.xml
09:15:53 T:3057190784 M:2449530880  NOTICE: Using fbConfig[0]
09:15:54 T:3057190784 M:2447990784  NOTICE: GL_VENDOR = NVIDIA Corporation
09:15:54 T:3057190784 M:2447990784  NOTICE: GL_RENDERER = ION/PCI/SSE2
09:15:54 T:3057190784 M:2447990784  NOTICE: GL_VERSION = 3.3.0 NVIDIA 256.35
09:15:54 T:3057190784 M:2447990784  NOTICE: GL_EXTENSIONS = GL_ARB_blend_func_extended GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_bit_encoding GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_swizzle GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback2 GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_copy_image GL_NV_depth_buffer_float GL_NV_depth_clamp GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_parameter_buffer_object2 GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_shader_buffer_load GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_multisample GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_transform_feedback2 GL_NV_vdpau_interop GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_buffer_unified_memory GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NVX_gpu_memory_info GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
09:15:54 T:3057190784 M:2447990784   ERROR: GLX: Same window as before, refreshing context
09:15:54 T:3057190784 M:2446438400  NOTICE: UDisks: Added /media/Ex1_1.5
09:15:54 T:3057190784 M:2446438400  NOTICE: UDisks: Added /boot
09:15:54 T:3057190784 M:2446438400  NOTICE: UDisks: Added /home
09:15:54 T:3057190784 M:2446438400  NOTICE: UDisks: Added /storage
09:15:54 T:3057190784 M:2446438400  NOTICE: UDisks: Added /media/Ex2_1.5
09:15:54 T:3057190784 M:2446561280  NOTICE: start dvd mediatype detection
09:15:54 T:3057190784 M:2446561280  NOTICE: initializing playlistplayer
09:15:54 T:3057190784 M:2446561280  NOTICE: DONE initializing playlistplayer
09:15:54 T:3057190784 M:2446561280  NOTICE: load default skin:[Confluence]
09:15:55 T:3057190784 M:2440388608   ERROR: DBus: Error org.freedesktop.DBus.Error.ServiceUnknown - The name org.freedesktop.UPower was not provided by any .service files
09:15:55 T:3057190784 M:2440388608   ERROR: DBus: Error org.freedesktop.DBus.Error.ServiceUnknown - The name org.freedesktop.UPower was not provided by any .service files
09:15:55 T:3057190784 M:2440388608  NOTICE: initialize done
09:15:55 T:3057190784 M:2440388608  NOTICE: Running the application...
09:15:55 T:3057190784 M:2440388608  NOTICE: ES: Starting event server
09:15:55 T:3057190784 M:2440388608  NOTICE: DS: Starting dbus server
09:15:55 T:3026209648 M:2440388608  NOTICE: ES: Starting UDP Event server on 127.0.0.1:9777
09:15:55 T:3026209648 M:2440118272  NOTICE: UDP: Listening on port 9777
09:15:55 T:3057190784 M:2439602176   ERROR:  DS: Failed to connect to the D-Bus session daemon: Empty address ''
09:15:55 T:3057190784 M:2439602176  NOTICE: starting zeroconf publishing
09:16:00 T:3057190784 M:2421383168  NOTICE: Storing total System Uptime
09:16:00 T:3057190784 M:2421383168  NOTICE: Saving settings
09:16:00 T:3057190784 M:2421608448  NOTICE: stop all
09:16:00 T:3057190784 M:2421608448  NOTICE: ES: Stopping event server
09:16:00 T:3057190784 M:2421608448  NOTICE: stopping zeroconf publishing
09:16:01 T:3026209648 M:2421698560  NOTICE: ES: UDP Event server stopped
09:16:01 T:3057190784 M:2421698560  NOTICE: stop dvd detect media
09:16:01 T:3057190784 M:2421698560  NOTICE: stop sap announcement listener
09:16:01 T:3057190784 M:2421698560  NOTICE: clean cached files!
09:16:01 T:3057190784 M:2421698560  NOTICE: unload skin
09:16:01 T:3057190784 M:2430595072  NOTICE: stop python
09:16:01 T:3057190784 M:2430595072  NOTICE: stopped
09:16:01 T:3057190784 M:2430595072  NOTICE: destroy
09:16:01 T:3057190784 M:2430468096  NOTICE: unload sections


############### END LOG FILE ################

############ END XBMC CRASH LOG #############


I'm now going to reset those 2 files permissions back and maybe someone will know more. Thank in advance :)

---

### Post by nerdy_kid on 2010-07-26
dont know how to solve it for you, but do know that sudoing gui apps screws up permissions....maybe thats what caused it.  should always use gksu/kdesudo instead.

---

### Post by JohnnyC35 on 2010-07-26
I tried sudo after trying it without sudo. I didn't realize that sud/gksudo act differently. I will have to watch that.

---

