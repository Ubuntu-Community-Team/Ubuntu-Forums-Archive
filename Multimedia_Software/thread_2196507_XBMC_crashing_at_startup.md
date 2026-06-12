---
title: "XBMC crashing at startup"
date: 2013-12-29
forum: Multimedia Software
---

### Post by goodpunk6 on 2013-12-29
I uninstalled and reinstalled and now it crashes when I attempt to run it.  I'm a n00b and don't know what to do.  My crash log is here [https://dl.dropboxusercontent.com/u/15934911/xbmc_crashlog-20131229_215552.log](https://dl.dropboxusercontent.com/u/15934911/xbmc_crashlog-20131229_215552.log).  Please advise

---

### Post by nmyrick on 2014-03-20
> **goodpunk6 said:**
> I uninstalled and reinstalled and now it crashes when I attempt to run it.  I'm a n00b and don't know what to do.  My crash log is here [https://dl.dropboxusercontent.com/u/15934911/xbmc_crashlog-20131229_215552.log](https://dl.dropboxusercontent.com/u/15934911/xbmc_crashlog-20131229_215552.log).  Please advise 

Did you figure out what was causing this? Your log looks very similar to mine, and mine just started crashing last night for no apparent reason.  I had not reinstalled it or anything and I did not load any updates, just one day it was working and the next day it was not.  I tried reinstalling XBMC, but it still crashes.  Here is my log.

############## XBMC CRASH LOG ###############

################ SYSTEM INFO ################
 Date: Thu Mar 20 11:18:02 CDT 2014
 XBMC Options: 
 Arch: x86_64
 Kernel: Linux 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014
 Release: 
    LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:cxx-4.1-amd64:cxx-4.1-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:desktop-4.1-amd64:desktop-4.1-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:graphics-4.1-amd64:graphics-4.1-noarch:languages-3.2-amd64:languages-3.2-noarch:languages-4.0-amd64:languages-4.0-noarch:languages-4.1-amd64:languages-4.1-noarch:multimedia-3.2-amd64:multimedia-3.2-noarch:multimedia-4.0-amd64:multimedia-4.0-noarch:multimedia-4.1-amd64:multimedia-4.1-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:printing-4.1-amd64:printing-4.1-noarch:qt4-3.1-amd64:qt4-3.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
    Distributor ID:    Ubuntu
    Description:    Ubuntu 13.10
    Release:    13.10
    Codename:    saucy
############## END SYSTEM INFO ##############

############### STACK TRACE #################
############# END STACK TRACE ###############

################# LOG FILE ##################

&#65279;11:17:53 T:139813386069888  NOTICE: -----------------------------------------------------------------------
11:17:53 T:139813386069888  NOTICE: Starting XBMC (12.3 Git:9ed3e58), Platform: Linux (Ubuntu 13.10, 3.11.0-18-generic x86_64). Built on Dec 13 2013
11:17:53 T:139813386069888  NOTICE: special://xbmc/ is mapped to: /usr/share/xbmc
11:17:53 T:139813386069888  NOTICE: special://xbmcbin/ is mapped to: /usr/lib/xbmc
11:17:53 T:139813386069888  NOTICE: special://masterprofile/ is mapped to: /home/****/.xbmc/userdata
11:17:53 T:139813386069888  NOTICE: special://home/ is mapped to: /home/****/.xbmc
11:17:53 T:139813386069888  NOTICE: special://temp/ is mapped to: /home/****/.xbmc/temp
11:17:53 T:139813386069888  NOTICE: The executable running is: /usr/lib/xbmc/xbmc.bin
11:17:53 T:139813386069888  NOTICE: Local hostname: Aquarius2
11:17:53 T:139813386069888  NOTICE: Log File is located: /home/****/.xbmc/temp/xbmc.log
11:17:53 T:139813386069888  NOTICE: -----------------------------------------------------------------------
11:17:53 T:139813386069888   ERROR: CAESinkOSS::EnumerateDevicesEx - Failed to open mixer: /dev/mixer
11:17:53 T:139813386069888  NOTICE: Found 1 Lists of Devices
11:17:53 T:139813386069888  NOTICE: Enumerated ALSA devices:
11:17:53 T:139813386069888  NOTICE:     Device 1
11:17:53 T:139813386069888  NOTICE:         m_deviceName      : default
11:17:53 T:139813386069888  NOTICE:         m_displayName     : Playback/recording through the PulseAudio sound server
11:17:53 T:139813386069888  NOTICE:         m_displayNameExtra:
11:17:53 T:139813386069888  NOTICE:         m_deviceType      : AE_DEVTYPE_PCM
11:17:53 T:139813386069888  NOTICE:         m_channels        : FL,FR,BL,BR,FC,LFE,SL,SR,UNKNOWN1,UNKNOWN2,UNKNOWN3,UNKNOWN4,UNKNOWN5,UNKNOWN6,UNKNOWN7,UNKNOWN8
11:17:53 T:139813386069888  NOTICE:         m_sampleRates     : 5512,8000,11025,16000,22050,32000,44100,48000,64000,88200,96000,176400,192000
11:17:53 T:139813386069888  NOTICE:         m_dataFormats     : AE_FMT_FLOAT,AE_FMT_S32NE,AE_FMT_S16NE,AE_FMT_S16LE,AE_FMT_S16BE,AE_FMT_U8
11:17:53 T:139813386069888  NOTICE:     Device 2
11:17:53 T:139813386069888  NOTICE:         m_deviceName      : @:CARD=PCH,DEV=0
11:17:53 T:139813386069888  NOTICE:         m_displayName     : HDA Intel PCH
11:17:53 T:139813386069888  NOTICE:         m_displayNameExtra: ALC269VB Analog
11:17:53 T:139813386069888  NOTICE:         m_deviceType      : AE_DEVTYPE_PCM
11:17:53 T:139813386069888  NOTICE:         m_channels        : FL,FR
11:17:53 T:139813386069888  NOTICE:         m_sampleRates     : 44100,48000,96000,192000
11:17:53 T:139813386069888  NOTICE:         m_dataFormats     : AE_FMT_S32NE,AE_FMT_S16NE,AE_FMT_S16LE
11:17:53 T:139813386069888  NOTICE:     Device 3
11:17:53 T:139813386069888  NOTICE:         m_deviceName      : hdmi:CARD=PCH,DEV=0
11:17:53 T:139813386069888  NOTICE:         m_displayName     : HDA Intel PCH
11:17:53 T:139813386069888  NOTICE:         m_displayNameExtra: HDMI
11:17:53 T:139813386069888  NOTICE:         m_deviceType      : AE_DEVTYPE_HDMI
11:17:53 T:139813386069888  NOTICE:         m_channels        : FL,FR,BL,BR,FC,LFE,SL,SR
11:17:53 T:139813386069888  NOTICE:         m_sampleRates     : 32000,44100,48000,88200,96000,176400,192000
11:17:53 T:139813386069888  NOTICE:         m_dataFormats     : AE_FMT_S32NE,AE_FMT_S16NE,AE_FMT_S16LE
11:17:53 T:139813386069888  NOTICE: load settings...
11:17:53 T:139813386069888  NOTICE: special://profile/ is mapped to: special://masterprofile/
11:17:53 T:139813386069888  NOTICE: loading special://masterprofile/guisettings.xml
11:17:53 T:139813386069888  NOTICE: Getting hardware information now...
11:17:53 T:139813386069888  NOTICE: Loading player core factory settings from special://xbmc/system/playercorefactory.xml.
11:17:53 T:139813386069888  NOTICE: Loaded playercorefactory configuration
11:17:53 T:139813386069888  NOTICE: Loading player core factory settings from special://masterprofile/playercorefactory.xml.
11:17:53 T:139813386069888  NOTICE: special://masterprofile/playercorefactory.xml does not exist. Skipping.
11:17:53 T:139813386069888  NOTICE: No settings file to load (special://xbmc/system/advancedsettings.xml)
11:17:53 T:139813386069888  NOTICE: No settings file to load (special://masterprofile/advancedsettings.xml)
11:17:53 T:139813386069888  NOTICE: Default DVD Player: dvdplayer
11:17:53 T:139813386069888  NOTICE: Default Video Player: dvdplayer
11:17:53 T:139813386069888  NOTICE: Default Audio Player: paplayer
11:17:53 T:139813386069888  NOTICE: Disabled debug logging due to GUI setting. Level 0.
11:17:53 T:139813386069888  NOTICE: Log level changed to 0
11:17:53 T:139813386069888  NOTICE: Loading media sources from special://masterprofile/sources.xml
11:17:53 T:139813112407808  NOTICE: Thread CSoftAE start, auto delete: false
11:17:53 T:139813386069888  NOTICE: Running database version Addons15
11:17:57 T:139813094811392  NOTICE: Thread XBMC Peripherals start, auto delete: false
11:17:58 T:139813386069888  NOTICE: Previous line repeats 1 times.
11:17:58 T:139813386069888  NOTICE: Setup SDL
11:17:58 T:139813386069888  NOTICE: Checking resolution 15
11:17:58 T:139813386069888  NOTICE: Using visual 0x21
11:17:58 T:139813386069888  NOTICE: GL_VENDOR = Intel Open Source Technology Center
11:17:58 T:139813386069888  NOTICE: GL_RENDERER = Mesa DRI Intel(R) Sandybridge Mobile
11:17:58 T:139813386069888  NOTICE: GL_VERSION = 3.0 Mesa 9.2.1
11:17:58 T:139813386069888  NOTICE: GL_SHADING_LANGUAGE_VERSION = 1.30
11:17:58 T:139813386069888  NOTICE: GL_EXTENSIONS = GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_framebuffer_sRGB GL_ARB_multitexture GL_EXT_framebuffer_sRGB GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_compression_s3tc GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_envmap_bumpmap GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_depth_clamp GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_primitive_restart GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_color_buffer_float GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_texture_array GL_EXT_texture_integer GL_EXT_texture_sRGB_decode GL_EXT_timer_query GL_OES_EGL_image GL_MESA_texture_array GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_AMD_draw_buffers_blend GL_ARB_ES2_compatibility GL_ARB_blend_func_extended GL_ARB_debug_output GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_texture_lod GL_ARB_texture_cube_map_array GL_ARB_texture_multisample GL_ARB_texture_query_lod GL_ARB_texture_rgb10_a2ui GL_ARB_uniform_buffer_object GL_ARB_vertex_type_2_10_10_10_rev GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_ARB_get_program_binary GL_ARB_robustness GL_ARB_shader_bit_encoding GL_ARB_timer_query GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_internalformat_query GL_ARB_shading_language_420pack GL_ARB_shading_language_packing GL_ARB_texture_storage GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_transform_feedback GL_ARB_ES3_compatibility GL_ARB_invalidate_subdata GL_ARB_texture_storage_multisample
11:17:58 T:139813386069888  NOTICE: Running database version Addons15
11:17:58 T:139813386069888  NOTICE: Running database version ViewModes4
11:17:58 T:139813386069888  NOTICE: Running database version Textures13
11:17:58 T:139813386069888  NOTICE: Running database version MyMusic32
11:17:58 T:139813386069888  NOTICE: Running database version MyVideos75
11:17:58 T:139813386069888  NOTICE: Running database version TV22
11:17:58 T:139813386069888  NOTICE: Running database version Epg7
11:17:58 T:139813386069888  NOTICE: start dvd mediatype detection
11:17:58 T:139813386069888  NOTICE: initializing playlistplayer
11:17:58 T:139813386069888  NOTICE: DONE initializing playlistplayer
11:17:58 T:139813384652544  NOTICE: Thread CDetectDVDMedia start, auto delete: false
11:17:59 T:139812859000576  NOTICE: Thread XBPyThread start, auto delete: false
11:17:59 T:139813386069888  NOTICE: initialize done
11:17:59 T:139813386069888  NOTICE: Running the application...
11:17:59 T:139812808644352  NOTICE: Thread XBPyThread start, auto delete: false
11:17:59 T:139812825429760  NOTICE: Previous line repeats 5 times.
11:17:59 T:139812825429760  NOTICE: -->Python Interpreter Initialized<--
11:17:59 T:139812825429760  NOTICE: [TV4ME] Subscription service starting...
11:17:59 T:139812817037056  NOTICE: -->Python Interpreter Initialized<--
11:17:59 T:139812859000576  NOTICE: -->Python Interpreter Initialized<--
11:17:59 T:139812174649088  NOTICE: Thread Jobworker start, auto delete: true
11:18:00 T:139813386069888  NOTICE: ES: Starting event server
11:18:00 T:139812166256384  NOTICE: Thread CEventServer start, auto delete: false
11:18:00 T:139812166256384  NOTICE: ES: Starting UDP Event server on 0.0.0.0:9777
11:18:00 T:139812166256384  NOTICE: UDP: Listening on port 9777
11:18:00 T:139813386069888  NOTICE: starting zeroconf publishing
11:18:00 T:139812157863680  NOTICE: Thread CTCPServer start, auto delete: false
11:18:00 T:139812141078272  NOTICE: Thread Jobworker start, auto delete: true
11:18:00 T:139812850607872  NOTICE: -->Python Interpreter Initialized<--
11:18:00 T:139812808644352  NOTICE: -->Python Interpreter Initialized<--
11:18:00 T:139812132685568  NOTICE: Thread Jobworker start, auto delete: true
11:18:00 T:139812795385600  NOTICE: Previous line repeats 1 times.
11:18:00 T:139812795385600  NOTICE: Thread CRssReader start, auto delete: false
11:18:00 T:139812833822464  NOTICE: -->Python Interpreter Initialized<--
11:18:00 T:139812842215168  NOTICE: -->Python Interpreter Initialized<--
11:18:00 T:139812817037056  NOTICE: [MovieStorm] Subscription service starting...
11:18:00 T:139812859000576  NOTICE: Thread CFileCache start, auto delete: false
11:18:00 T:139812833822464  NOTICE: PrimeWire: Service: MySQL not enabled or not setup correctly
11:18:00 T:139812833822464  NOTICE: PrimeWire: Service: Loading sqlite3 as DB engine
11:18:00 T:139812833822464  NOTICE: PrimeWire: Service: Resetting...
11:18:00 T:139812850607872  NOTICE:  StorageServer Module loaded RUN
11:18:00 T:139812850607872  NOTICE: StorageClient-2.5.4 Starting server
11:18:00 T:139812850607872  NOTICE: StorageServer-2.5.4 Storage Server starting /home/****/.xbmc/temp/commoncache.db
11:18:00 T:139812833822464  NOTICE: PrimeWire: Service starting...


############### END LOG FILE ################

############ END XBMC CRASH LOG #############

---

### Post by frank18 on 2014-03-20
Update to 14.04

---

### Post by nmyrick on 2014-03-21
@frank18 - I plan on doing that, but I'm waiting for the official release.  I have figured out from the crash log that it is the PrimeWire add on trying to connect to the internet on startup that is causing the issue.  Currently my workaround is to disable my wireless connection, start XBMC, then enable the wireless again and it works perfectly fine.  I have also redirected PrimeWire to a different mirror and disabled meta data, but since XBMC was only crashing about 70% of the time, I have yet to determine if that fixed the issue.  Thanks for the tip though.

---

### Post by d.mayfair on 2014-03-21
I had lots of issues when I 1st used xbmc.
I found it was best to install 1 add on at a time and run it for a while to check everything still worked.

Also,for me,xbmchub caused instability so I no longer use that

---

### Post by Wheel on 2014-03-23
@nmyrick

Have you seen this?
[http://forum.xbmc.org/showthread.php?tid=189722&pid=1661176#pid1661176](http://forum.xbmc.org/showthread.php?tid=189722&pid=1661176#pid1661176)

Github problems.
Seems to be crashing most (all?) ubuntu based systems.

---

### Post by frank18 on 2014-03-23
> **nmyrick said:**
> @frank18 - I plan on doing that, but I'm waiting for the official release.  I have figured out from the crash log that it is the PrimeWire add on trying to connect to the internet on startup that is causing the issue.  Currently my workaround is to disable my wireless connection, start XBMC, then enable the wireless again and it works perfectly fine.  I have also redirected PrimeWire to a different mirror and disabled meta data, but since XBMC was only crashing about 70% of the time, I have yet to determine if that fixed the issue.  Thanks for the tip though.

 Well when i have a problem i  re-install Linux rather then to try to solve some problems that take long time to fix and for me it's so easy to re-install,i have 20 Distros in CD and what i like is to try them all, that's why i can affirm the best Distro for me is Ubuntu 14.04 beta 1 that's the one that's more efficient.

---

