---
title: "XBMC Frodo Crashes on Startup on Ubuntu 12.10"
date: 2013-02-11
forum: Multimedia Software
---

### Post by gwinston99 on 2013-02-11
XBMC crashes w. seg fault on startup - crash log below -can only run 'sudo xbmc` - permission problem? Please help.


############## XBMC CRASH LOG ###############

################ SYSTEM INFO ################
 Date: Mon Feb 11 08:35:48 EST 2013
 XBMC Options: 
 Arch: i686
 Kernel: Linux 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:05:29 UTC 2013
 Release: 
    Distributor ID:	Ubuntu
    Description:	Ubuntu 12.10
    Release:	12.10
    Codename:	quantal
############## END SYSTEM INFO ##############

############### STACK TRACE #################
############# END STACK TRACE ###############

################# LOG FILE ##################

&#65279;23:23:34 T:3038508800  NOTICE: -----------------------------------------------------------------------
23:23:34 T:3038508800  NOTICE: Starting XBMC (12.0 Git:fb595f2), Platform: Linux (Ubuntu 12.10, 3.5.0-22-generic i686). Built on Jan 28 2013
23:23:34 T:3038508800  NOTICE: special://xbmc/ is mapped to: /usr/share/xbmc
23:23:34 T:3038508800  NOTICE: special://xbmcbin/ is mapped to: /usr/lib/xbmc
23:23:34 T:3038508800  NOTICE: special://masterprofile/ is mapped to: /home/gregg/.xbmc/userdata
23:23:34 T:3038508800  NOTICE: special://home/ is mapped to: /home/gregg/.xbmc
23:23:34 T:3038508800  NOTICE: special://temp/ is mapped to: /home/gregg/.xbmc/temp
23:23:34 T:3038508800  NOTICE: The executable running is: /usr/lib/xbmc/xbmc.bin
23:23:34 T:3038508800  NOTICE: Local hostname: ubuntu-HP
23:23:34 T:3038508800  NOTICE: Log File is located: /home/gregg/.xbmc/temp/xbmc.log
23:23:34 T:3038508800  NOTICE: -----------------------------------------------------------------------
23:23:34 T:3038508800   ERROR: CAESinkOSS::EnumerateDevicesEx - Failed to open mixer: /dev/mixer
23:23:34 T:3038508800  NOTICE: Enumerated ALSA devices:
23:23:34 T:3038508800  NOTICE:     Device 1
23:23:34 T:3038508800  NOTICE:         m_deviceName      : default
23:23:34 T:3038508800  NOTICE:         m_displayName     : Playback/recording through the PulseAudio sound server
23:23:34 T:3038508800  NOTICE:         m_displayNameExtra:
23:23:34 T:3038508800  NOTICE:         m_deviceType      : AE_DEVTYPE_PCM
23:23:34 T:3038508800  NOTICE:         m_channels        : FL,FR,BL,BR,FC,LFE,SL,SR,UNKNOWN1,UNKNOWN2,UNKNOWN3,UNKNOWN4,UNKNOWN5,UNKNOWN6,UNKNOWN7,UNKNOWN8
23:23:34 T:3038508800  NOTICE:         m_sampleRates     : 5512,8000,11025,16000,22050,32000,44100,48000,64000,88200,96000,176400,192000
23:23:34 T:3038508800  NOTICE:         m_dataFormats     : AE_FMT_FLOAT,AE_FMT_S32NE,AE_FMT_S16NE,AE_FMT_S16LE,AE_FMT_S16BE,AE_FMT_U8
23:23:34 T:3038508800  NOTICE:     Device 2
23:23:34 T:3038508800  NOTICE:         m_deviceName      : @:CARD=Intel,DEV=0
23:23:34 T:3038508800  NOTICE:         m_displayName     : HDA Intel
23:23:34 T:3038508800  NOTICE:         m_displayNameExtra: AD198x Analog
23:23:34 T:3038508800  NOTICE:         m_deviceType      : AE_DEVTYPE_PCM
23:23:34 T:3038508800  NOTICE:         m_channels        : FL,FR
23:23:34 T:3038508800  NOTICE:         m_sampleRates     : 8000,11025,16000,22050,32000,44100,48000
23:23:34 T:3038508800  NOTICE:         m_dataFormats     : AE_FMT_S32NE,AE_FMT_S16NE,AE_FMT_S16LE
23:23:34 T:3038508800  NOTICE: load settings...
23:23:35 T:3038508800  NOTICE: special://profile/ is mapped to: special://masterprofile/
23:23:35 T:3038508800  NOTICE: loading special://masterprofile/guisettings.xml
23:23:35 T:3038508800  NOTICE: Getting hardware information now...
23:23:35 T:3038508800  NOTICE: Loading player core factory settings from special://xbmc/system/playercorefactory.xml.
23:23:35 T:3038508800  NOTICE: Loaded playercorefactory configuration
23:23:35 T:3038508800  NOTICE: Loading player core factory settings from special://masterprofile/playercorefactory.xml.
23:23:35 T:3038508800  NOTICE: special://masterprofile/playercorefactory.xml does not exist. Skipping.
23:23:35 T:3038508800  NOTICE: No settings file to load (special://xbmc/system/advancedsettings.xml)
23:23:35 T:3038508800  NOTICE: No settings file to load (special://masterprofile/advancedsettings.xml)
23:23:35 T:3038508800  NOTICE: Default DVD Player: dvdplayer
23:23:35 T:3038508800  NOTICE: Default Video Player: dvdplayer
23:23:35 T:3038508800  NOTICE: Default Audio Player: paplayer
23:23:35 T:3038508800  NOTICE: Disabled debug logging due to GUI setting. Level 0.
23:23:35 T:3038508800  NOTICE: Log level changed to 0
23:23:35 T:3038508800  NOTICE: Loading media sources from special://masterprofile/sources.xml
23:23:35 T:2894068544  NOTICE: Thread CSoftAE start, auto delete: false
23:23:35 T:3038508800  NOTICE: Running database version Addons15
23:23:36 T:3034577728  NOTICE: Thread XBMC Peripherals start, auto delete: false
23:23:36 T:3038508800  NOTICE: Setup SDL
23:23:36 T:3038508800  NOTICE: Checking resolution 16
23:23:36 T:3038508800  NOTICE: Using visual 0x22
23:23:37 T:3038508800  NOTICE: GL_VENDOR = Intel Open Source Technology Center
23:23:37 T:3038508800  NOTICE: GL_RENDERER = Mesa DRI Intel(R) 965GM x86/MMX/SSE2
23:23:37 T:3038508800  NOTICE: GL_VERSION = 2.1 Mesa 9.0
23:23:37 T:3038508800  NOTICE: GL_SHADING_LANGUAGE_VERSION = 1.20
23:23:37 T:3038508800  NOTICE: GL_EXTENSIONS = GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_framebuffer_sRGB GL_ARB_multitexture GL_EXT_framebuffer_sRGB GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_compression_s3tc GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_NV_vertex_program GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_envmap_bumpmap GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_depth_clamp GL_NV_vertex_program1_1 GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_primitive_restart GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_color_buffer_float GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_texture_array GL_EXT_texture_integer GL_EXT_texture_sRGB_decode GL_OES_EGL_image GL_MESA_texture_array GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_ARB_ES2_compatibility GL_ARB_debug_output GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_texture_lod GL_ARB_texture_rgb10_a2ui GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_ARB_robustness GL_ARB_shader_bit_encoding GL_ARB_texture_storage GL_ARB_invalidate_subdata
23:23:37 T:3038508800   ERROR: GLX: Same window as before, refreshing context
23:23:37 T:3038508800  NOTICE: Running database version Addons15
23:23:37 T:3038508800  NOTICE: Running database version ViewModes4
23:23:37 T:3038508800  NOTICE: Running database version Textures13
23:23:37 T:3038508800  NOTICE: Running database version MyMusic32
23:23:37 T:3038508800  NOTICE: Running database version MyVideos75
23:23:37 T:3038508800  NOTICE: Running database version TV22
23:23:37 T:3038508800  NOTICE: Running database version Epg7
23:23:37 T:3038508800  NOTICE: start dvd mediatype detection
23:23:37 T:3038508800  NOTICE: initializing playlistplayer
23:23:37 T:3038508800  NOTICE: DONE initializing playlistplayer
23:23:37 T:3025324864  NOTICE: Thread CDetectDVDMedia start, auto delete: false
23:23:38 T:3038508800  NOTICE: initialize done
23:23:38 T:3038508800  NOTICE: Enabled Joystick: ST LIS3LV02DL Accelerometer
23:23:38 T:3038508800  NOTICE: Details: Total Axis: 3 Total Hats: 0 Total Buttons: 0
23:23:38 T:3038508800  NOTICE: Running the application...
23:23:38 T:2885675840  NOTICE: Thread Jobworker start, auto delete: true
23:23:38 T:3038508800  NOTICE: ES: Starting event server
23:23:38 T:2868890432  NOTICE: Thread CTCPServer start, auto delete: false
23:23:38 T:2877283136  NOTICE: Thread CEventServer start, auto delete: false
23:23:38 T:2877283136  NOTICE: ES: Starting UDP Event server on 0.0.0.0:9777
23:23:38 T:2877283136  NOTICE: UDP: Listening on port 9777
23:23:38 T:3038508800  NOTICE: starting zeroconf publishing
23:23:38 T:2852105024  NOTICE: Thread Jobworker start, auto delete: true
23:23:38 T:2989943616  NOTICE: Thread CRssReader start, auto delete: false
23:23:39 T:2817493824  NOTICE: Thread CFileCache start, auto delete: false
23:23:43 T:2817493824  NOTICE: Previous line repeats 1 times.
23:23:43 T:2817493824  NOTICE: Thread Background Loader start, auto delete: false
23:24:34 T:2817493824  NOTICE: Previous line repeats 8 times.
23:24:34 T:2817493824 WARNING: CreateLoader - Unsupported protocol(addons) in addons://disabled/folder.jpg
23:24:34 T:2817493824 WARNING: CreateLoader - Unsupported protocol(addons) in addons://enabled/folder.jpg
23:24:34 T:2817493824 WARNING: CreateLoader - Unsupported protocol(addons) in addons://repos/folder.jpg
23:24:34 T:2817493824 WARNING: CreateLoader - Unsupported protocol(addons) in addons://install/folder.jpg
23:24:34 T:2817493824 WARNING: CreateLoader - Unsupported protocol(addons) in addons://search/folder.jpg
23:24:38 T:2817493824  NOTICE: Thread Background Loader start, auto delete: false
23:24:44 T:3038508800  NOTICE: Previous line repeats 1 times.
23:24:44 T:3038508800   ERROR: GLX: Same window as before, refreshing context
23:24:48 T:2817493824   ERROR: Previous line repeats 1 times.
23:24:48 T:2817493824  NOTICE: Thread Background Loader start, auto delete: false
23:24:49 T:3038508800   ERROR: CheckDisplayEvents - no display event after 3 seconds
23:24:50 T:2817493824  NOTICE: Thread Background Loader start, auto delete: false
23:24:51 T:2885675840  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:24:51 T:2817493824  NOTICE: Thread Jobworker start, auto delete: true
23:24:52 T:2885675840  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:24:52 T:2885675840  NOTICE: Previous line repeats 1 times.
23:24:52 T:2885675840  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
23:24:54 T:2885675840  NOTICE: Previous line repeats 1 times.
23:24:54 T:2885675840  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:24:54 T:2826120000  NOTICE: Thread Jobworker start, auto delete: true
23:24:55 T:2885675840  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:24:58 T:2885675840  NOTICE: Previous line repeats 4 times.
23:24:58 T:2885675840  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
23:24:59 T:2826120000  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: Windows Media Video 9
23:24:59 T:2826120000  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
23:25:00 T:2826120000  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:25:01 T:2826120000  NOTICE: Previous line repeats 1 times.
23:25:01 T:2826120000  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
23:25:02 T:2826120000  NOTICE: Previous line repeats 1 times.
23:25:02 T:2826120000  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:25:03 T:2826120000  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
23:25:04 T:2817493824  NOTICE: Previous line repeats 1 times.
23:25:04 T:2817493824  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:25:04 T:2817493824  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
23:25:05 T:2817493824  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:25:06 T:2817493824  NOTICE: Previous line repeats 1 times.
23:25:06 T:2817493824  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
23:25:07 T:2817493824  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:25:08 T:3038508800  NOTICE: Previous line repeats 1 times.
23:25:08 T:3038508800  NOTICE: DVDPlayer: Opening: /home/gregg/Videos/200 motels.avi
23:25:08 T:3038508800 WARNING: CDVDMessageQueue(player)::Put MSGQ_NOT_INITIALIZED
23:25:08 T:2809101120  NOTICE: Thread CDVDPlayer start, auto delete: false
23:25:08 T:2809101120  NOTICE: Creating InputStream
23:25:08 T:2809101120  NOTICE: Creating Demuxer
23:25:08 T:2809101120  NOTICE: Opening video stream: 0 source: 256
23:25:08 T:2809101120  NOTICE: Creating video codec with codec id: 13
23:25:08 T:2809101120  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:25:08 T:2809101120  NOTICE: Creating video thread
23:25:08 T:2783349568  NOTICE: Thread CDVDPlayerVideo start, auto delete: false
23:25:08 T:2783349568  NOTICE: running thread: video_thread
23:25:08 T:2809101120  NOTICE: Opening audio stream: 1 source: 256
23:25:08 T:2809101120  NOTICE: Finding audio codec for: 86017
23:25:08 T:2809101120  NOTICE: Creating audio thread
23:25:08 T:2771266368  NOTICE: Thread CDVDPlayerAudio start, auto delete: false
23:25:08 T:2771266368  NOTICE: running thread: CDVDPlayerAudio::Process()
23:25:08 T:2771266368  NOTICE: Creating audio stream (codec id: 86017, channels: 2, sample rate: 48000, no pass-through)
23:25:08 T:2783349568  NOTICE:  fps: 29.970030, pwidth: 480, pheight: 360, dwidth: 480, dheight: 360
23:25:08 T:2783349568  NOTICE: Display resolution DESKTOP : 1280x800 @ 60.00 - Full Screen (16)
23:25:08 T:2817493824  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:25:08 T:3038508800  NOTICE: Using GL_TEXTURE_2D
23:25:08 T:3038508800  NOTICE: GL: Selecting Single Pass YUV 2 RGB shader
23:25:08 T:3038508800  NOTICE: GL: NPOT texture support detected
23:25:08 T:3038508800  NOTICE: GL: Using GL_ARB_pixel_buffer_object
23:30:35 T:3038508800  NOTICE: CDVDPlayer::CloseFile()
23:30:35 T:3038508800  NOTICE: DVDPlayer: waiting for threads to exit
23:30:35 T:2809101120  NOTICE: CDVDPlayer::OnExit()
23:30:35 T:2809101120  NOTICE: DVDPlayer: closing audio stream
23:30:35 T:2809101120  NOTICE: Closing audio stream
23:30:35 T:2809101120  NOTICE: Waiting for audio thread to exit
23:30:35 T:2771266368  NOTICE: thread end: CDVDPlayerAudio::OnExit()
23:30:35 T:2809101120  NOTICE: Closing audio device
23:30:36 T:2809101120  NOTICE: Deleting audio codec
23:30:36 T:2809101120  NOTICE: DVDPlayer: closing video stream
23:30:36 T:2809101120  NOTICE: Closing video stream
23:30:36 T:2809101120  NOTICE: waiting for video thread to exit
23:30:36 T:2783349568  NOTICE: thread end: video_thread
23:30:36 T:2809101120  NOTICE: deleting video codec
23:30:36 T:2809101120  NOTICE: CDVDPlayer::OnExit() deleting demuxer
23:30:36 T:2809101120  NOTICE: CDVDPlayer::OnExit() deleting input stream
23:30:36 T:3038508800  NOTICE: DVDPlayer: finished waiting
23:30:36 T:2809101120  NOTICE: Thread Background Loader start, auto delete: false
23:30:36 T:2783349568  NOTICE: Thread Jobworker start, auto delete: true
23:30:36 T:3038508800  NOTICE: CDVDPlayer::CloseFile()
23:30:36 T:3038508800 WARNING: CDVDMessageQueue(player)::Put MSGQ_NOT_INITIALIZED
23:30:36 T:3038508800  NOTICE: DVDPlayer: waiting for threads to exit
23:30:36 T:3038508800  NOTICE: DVDPlayer: finished waiting
23:30:36 T:2771266368  NOTICE: Thread Jobworker start, auto delete: true
23:30:37 T:2783349568  NOTICE: Previous line repeats 2 times.
23:30:37 T:2783349568  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:30:37 T:2817563456  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
23:30:38 T:2852105024  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:30:39 T:3038508800  NOTICE: DVDPlayer: Opening: /home/gregg/Videos/ARGO.avi
23:30:39 T:3038508800 WARNING: CDVDMessageQueue(player)::Put MSGQ_NOT_INITIALIZED
23:30:39 T:2809101120  NOTICE: Thread CDVDPlayer start, auto delete: false
23:30:39 T:2809101120  NOTICE: Creating InputStream
23:30:39 T:2809101120  NOTICE: Creating Demuxer
23:30:39 T:2809101120  NOTICE: Opening video stream: 0 source: 256
23:30:39 T:2809101120  NOTICE: Creating video codec with codec id: 13
23:30:39 T:2809101120  NOTICE: CDVDVideoCodecFFmpeg::Open() Using codec: MPEG-4 part 2
23:30:39 T:2809101120  NOTICE: Creating video thread
23:30:39 T:2800708416  NOTICE: Thread CDVDPlayerVideo start, auto delete: false
23:30:39 T:2809101120  NOTICE: Opening audio stream: 1 source: 256
23:30:39 T:2809101120  NOTICE: Finding audio codec for: 86017
23:30:39 T:2809101120  NOTICE: Creating audio thread
23:30:39 T:2800708416  NOTICE: running thread: video_thread
23:30:39 T:2792315712  NOTICE: Thread CDVDPlayerAudio start, auto delete: false
23:30:39 T:2792315712  NOTICE: running thread: CDVDPlayerAudio::Process()
23:30:39 T:2800708416  NOTICE:  fps: 29.970030, pwidth: 720, pheight: 404, dwidth: 720, dheight: 404
23:30:39 T:2792315712  NOTICE: Creating audio stream (codec id: 86017, channels: 2, sample rate: 48000, no pass-through)
23:30:39 T:2800708416 WARNING: CRenderManager::Configure - timeout waiting for previous frame
23:30:39 T:2800708416  NOTICE: Display resolution DESKTOP : 1280x800 @ 60.00 - Full Screen (16)
23:30:39 T:3038508800  NOTICE: Using GL_TEXTURE_2D
23:30:39 T:3038508800  NOTICE: GL: Selecting Single Pass YUV 2 RGB shader
23:30:39 T:3038508800  NOTICE: GL: NPOT texture support detected
23:30:39 T:3038508800  NOTICE: GL: Using GL_ARB_pixel_buffer_object
23:38:39 T:3038508800  NOTICE: CDVDPlayer::CloseFile()
23:38:39 T:3038508800  NOTICE: DVDPlayer: waiting for threads to exit
23:38:39 T:2809101120  NOTICE: CDVDPlayer::OnExit()
23:38:39 T:2809101120  NOTICE: DVDPlayer: closing audio stream
23:38:39 T:2809101120  NOTICE: Closing audio stream
23:38:39 T:2809101120  NOTICE: Waiting for audio thread to exit
23:38:39 T:2792315712  NOTICE: thread end: CDVDPlayerAudio::OnExit()
23:38:39 T:2809101120  NOTICE: Closing audio device
23:38:40 T:2809101120  NOTICE: Deleting audio codec
23:38:40 T:2809101120  NOTICE: DVDPlayer: closing video stream
23:38:40 T:2809101120  NOTICE: Closing video stream
23:38:40 T:2809101120  NOTICE: waiting for video thread to exit
23:38:40 T:2800708416  NOTICE: thread end: video_thread
23:38:40 T:2809101120  NOTICE: deleting video codec
23:38:40 T:2809101120  NOTICE: CDVDPlayer::OnExit() deleting demuxer
23:38:40 T:2809101120  NOTICE: CDVDPlayer::OnExit() deleting input stream
23:38:40 T:3038508800  NOTICE: DVDPlayer: finished waiting
23:38:40 T:2809101120  NOTICE: Thread Background Loader start, auto delete: false
23:38:40 T:2800708416  NOTICE: Thread Jobworker start, auto delete: true
23:38:40 T:3038508800  NOTICE: Previous line repeats 1 times.
23:38:40 T:3038508800  NOTICE: CDVDPlayer::CloseFile()
23:38:40 T:3038508800 WARNING: CDVDMessageQueue(player)::Put MSGQ_NOT_INITIALIZED
23:38:40 T:3038508800  NOTICE: DVDPlayer: waiting for threads to exit
23:38:40 T:3038508800  NOTICE: DVDPlayer: finished waiting
23:38:40 T:2852105024  NOTICE: Thread Jobworker start, auto delete: true
23:38:48 T:3038508800  NOTICE: Storing total System Uptime
23:38:48 T:3038508800  NOTICE: Saving settings
23:38:48 T:3038508800  NOTICE: stop all
23:38:48 T:3038508800  NOTICE: ES: Stopping event server
23:38:48 T:3038508800  NOTICE: stopping zeroconf publishing
23:38:49 T:2877283136  NOTICE: ES: UDP Event server stopped
23:38:49 T:3038508800  NOTICE: stop dvd detect media
23:38:49 T:3038508800  NOTICE: stop sap announcement listener
23:38:49 T:3038508800  NOTICE: clean cached files!
23:38:49 T:3038508800  NOTICE: unload skin
23:38:49 T:3038508800  NOTICE: stop python
23:38:49 T:3038508800  NOTICE: stopped
23:38:49 T:3038508800  NOTICE: destroy
23:38:49 T:3038508800  NOTICE: closing down remote control service
23:38:49 T:3038508800  NOTICE: unload sections
23:38:49 T:3038508800  NOTICE: destroy
23:38:49 T:3038508800 WARNING: Attempted to remove window 10013 from the window manager when it didn't exist
23:38:49 T:3038508800 WARNING: Attempted to remove window 10014 from the window manager when it didn't exist
23:38:49 T:3038508800 WARNING: Attempted to remove window 10015 from the window manager when it didn't exist
23:38:49 T:3038508800 WARNING: Attempted to remove window 10016 from the window manager when it didn't exist
23:38:49 T:3038508800 WARNING: Attempted to remove window 10017 from the window manager when it didn't exist
23:38:49 T:3038508800 WARNING: Attempted to remove window 10018 from the window manager when it didn't exist
23:38:49 T:3038508800 WARNING: Attempted to remove window 10019 from the window manager when it didn't exist
23:38:49 T:3038508800 WARNING: Attempted to remove window 10021 from the window manager when it didn't exist
23:38:49 T:3038508800 WARNING: Attempted to remove window 10107 from the window manager when it didn't exist
23:38:49 T:3038508800 WARNING: Attempted to remove window 10115 from the window manager when it didn't exist
23:38:49 T:3038508800 WARNING: Attempted to remove window 10104 from the window manager when it didn't exist
23:38:49 T:3038508800  NOTICE: closing down remote control service
23:38:49 T:3038508800  NOTICE: unload sections
23:38:49 T:3038508800  NOTICE: application stopped...


############### END LOG FILE ################

############ END XBMC CRASH LOG #############

---

### Post by amias on 2013-03-10
am getting the same behaviour , incidentally if i wait about 5 minutes it does load eventually and then works fine.

also if i move .xbmc out of the way completely it also works fine.

also this ppa - [https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver) has a newer intel graphics driver
which at least stops it locking X.

---

