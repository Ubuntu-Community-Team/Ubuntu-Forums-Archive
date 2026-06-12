---
title: "MythTV and XBMC = Errors"
date: 2009-11-24
forum: Multimedia Software
---

### Post by slipdipper on 2009-11-24
I've had MythTV and XBMC working pretty seamlessly in the past and with my recent upgrade from juanty to karmic i cant seem to get the two to work anymore. 

Specifically it has to do with watching live television. Since i don't do anything else with xbmc, thats all i can see thats broken. 

The Guide is populated with all the channels but the "Live Channels" area is not. This kind of sounds like the issue described here ([http://xbmc.org/wiki/?title=MythTV#Live_TV_Doesn.27t_Play](http://xbmc.org/wiki/?title=MythTV#Live_TV_Doesn.27t_Play)) but i've tried everything from removing the input sources and re-searching for channels to droping the entire mythtv database, removing mythtv, mysql, and xbmc. nothing seems to fix the problem.

im using xbmc from the same host as the mythtv backend. heres some output from my mythbackend.log:

```

2009-11-24 15:29:33.529 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-24 15:29:33.537 Using runtime prefix = /usr
2009-11-24 15:29:33.558 Using configuration directory = /home/mythtv/.mythtv
2009-11-24 15:29:33.569 Empty LocalHostName.
2009-11-24 15:29:33.575 Using localhost value of mythtv-backend-server
2009-11-24 15:29:33.576 Testing network connectivity to '192.168.1.2'
2009-11-24 15:29:33.599 New DB connection, total: 1
2009-11-24 15:29:33.603 Connected to database 'mythconverg' at host: 192.168.1.2
2009-11-24 15:29:33.605 Closing DB connection named 'DBManager0'
2009-11-24 15:29:33.606 Connected to database 'mythconverg' at host: 192.168.1.2
2009-11-24 15:29:33.630 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-24 15:29:33.632 MythBackend: Starting up as the master server.
2009-11-24 15:29:33.637 New DB connection, total: 2
2009-11-24 15:29:33.828 Connected to database 'mythconverg' at host: 192.168.1.2
2009-11-24 15:29:34.208 New DB connection, total: 3
2009-11-24 15:29:34.210 Connected to database 'mythconverg' at host: 192.168.1.2
2009-11-24 15:29:34.340 New DB scheduler connection
2009-11-24 15:29:34.347 Connected to database 'mythconverg' at host: 192.168.1.2
2009-11-24 15:29:34.363 Enabling Upnpmedia rebuild thread.
2009-11-24 15:29:35.414 Main::Registering HttpStatus Extension
2009-11-24 15:29:35.416 Enabled verbose msgs:  important general
2009-11-24 15:29:35.418 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-24 15:29:37.351 Reschedule requested for id -1.
2009-11-24 15:29:37.378 Scheduled 0 items in 0.0 = 0.00 match + 0.02 place
2009-11-24 15:29:37.381 Seem to be woken up by USER
2009-11-24 15:29:44.365 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2009-11-24 15:29:59.012 MainServer::ANN Monitor
2009-11-24 15:29:59.014 adding: mythtv-backend-server as a client (events: 0)
2009-11-24 15:29:59.017 MainServer::ANN Monitor
2009-11-24 15:29:59.018 adding: mythtv-backend-server as a client (events: 1)
2009-11-24 15:29:59.019 Reschedule requested for id -1.
2009-11-24 15:29:59.043 Scheduled 0 items in 0.0 = 0.00 match + 0.02 place
2009-11-24 15:30:34.456 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Can not measure Signal Strength
                        eno: Invalid argument (22)
2009-11-24 15:30:34.461 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Can not measure S/N
                        eno: Invalid argument (22)
2009-11-24 15:30:35.114 Program #3 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(25) extension(0x17a3)
      version(4) current(1) section(0) last_section(0)
         tsid: 6051
 programCount: 4
  program number     0 has PID 0x1ffc   data  0x 0 0x 0 0xff 0xfc
  program number     2 has PID 0x  47   data  0x 0 0x 2 0xe0 0x47
  program number     4 has PID 0x  57   data  0x 0 0x 4 0xe0 0x57
  program number     1 has PID 0x  67   data  0x 0 0x 1 0xe0 0x67

2009-11-24 15:30:35.618 ProcessPAT: Program not found in PAT.
                        Rescan your transports.
2009-11-24 15:30:35.619 Desired program #3 not found in PAT.
                        Can Not create single program PAT.
2009-11-24 15:30:39.509 MainServer::HandleVersion - Client speaks protocol version 8 but we speak 50!
2009-11-24 15:30:39.511 MainServer, Warning: Unknown socket closing MythSocket(0x89bef08)
2009-11-24 15:30:39.512 MainServer::ANN Playback
2009-11-24 15:30:39.513 adding: mythtv-backend-server as a client (events: 0)
2009-11-24 15:30:39.516 MainServer::HandleVersion - Client speaks protocol version 8 but we speak 50!
2009-11-24 15:30:39.517 MainServer, Warning: Unknown socket closing MythSocket(0x89babd0)
2009-11-24 15:30:39.517 MainServer::ANN Playback
2009-11-24 15:30:39.519 adding: mythtv-backend-server as a client (events: 0)
2009-11-24 15:30:40.909 MainServer::HandleVersion - Client speaks protocol version 8 but we speak 50!
2009-11-24 15:30:40.910 MainServer, Warning: Unknown socket closing MythSocket(0x89b9e10)
2009-11-24 15:30:40.911 MainServer::ANN Playback
2009-11-24 15:30:40.912 adding: mythtv-backend-server as a client (events: 0)
2009-11-24 15:30:54.352 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-24 15:31:20.309 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-24 15:31:20.312 Using runtime prefix = /usr
2009-11-24 15:31:20.313 Using configuration directory = /home/mythtv/.mythtv
2009-11-24 15:31:20.314 Empty LocalHostName.
2009-11-24 15:31:20.314 Using localhost value of mythtv-backend-server
2009-11-24 15:31:20.316 Testing network connectivity to '192.168.1.2'
2009-11-24 15:31:20.323 New DB connection, total: 1
2009-11-24 15:31:20.400 Connected to database 'mythconverg' at host: 192.168.1.2
2009-11-24 15:31:20.401 Closing DB connection named 'DBManager0'
2009-11-24 15:31:20.402 Connected to database 'mythconverg' at host: 192.168.1.2
2009-11-24 15:31:20.405 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-24 15:31:20.406 MythBackend: Starting up as the master server.
2009-11-24 15:31:20.409 New DB connection, total: 2
2009-11-24 15:31:20.410 Connected to database 'mythconverg' at host: 192.168.1.2
2009-11-24 15:31:20.707 New DB connection, total: 3
2009-11-24 15:31:20.708 Connected to database 'mythconverg' at host: 192.168.1.2
2009-11-24 15:31:20.727 New DB scheduler connection
2009-11-24 15:31:20.729 Connected to database 'mythconverg' at host: 192.168.1.2
2009-11-24 15:31:20.748 Enabling Upnpmedia rebuild thread.
2009-11-24 15:31:21.789 Main::Registering HttpStatus Extension
2009-11-24 15:31:21.790 Enabled verbose msgs:  important general
2009-11-24 15:31:21.792 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-24 15:31:22.023 MainServer::ANN Monitor
2009-11-24 15:31:22.025 adding: mythtv-backend-server as a client (events: 0)
2009-11-24 15:31:22.026 MainServer::ANN Monitor
2009-11-24 15:31:22.027 adding: mythtv-backend-server as a client (events: 1)
2009-11-24 15:31:23.734 Reschedule requested for id -1.
2009-11-24 15:31:23.761 Scheduled 0 items in 0.0 = 0.00 match + 0.02 place
2009-11-24 15:31:23.765 Seem to be woken up by USER
2009-11-24 15:31:30.750 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2009-11-24 15:31:47.192 MainServer::HandleVersion - Client speaks protocol version 8 but we speak 50!
2009-11-24 15:31:47.193 MainServer, Warning: Unknown socket closing MythSocket(0x8d74118)
2009-11-24 15:31:47.194 MainServer::ANN Playback
2009-11-24 15:31:47.195 adding: mythtv-backend-server as a client (events: 0)
2009-11-24 15:31:47.198 MainServer::HandleVersion - Client speaks protocol version 8 but we speak 50!
2009-11-24 15:31:47.199 MainServer, Warning: Unknown socket closing MythSocket(0x8d73b80)
2009-11-24 15:31:47.199 MainServer::ANN Playback
2009-11-24 15:31:47.200 adding: mythtv-backend-server as a client (events: 0)
2009-11-24 15:32:20.839 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Can not measure Signal Strength
                        eno: Invalid argument (22)
2009-11-24 15:32:20.843 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Can not measure S/N
                        eno: Invalid argument (22)
2009-11-24 15:32:21.313 Program #3 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(25) extension(0x17a3)
      version(4) current(1) section(0) last_section(0)
         tsid: 6051
 programCount: 4
  program number     0 has PID 0x1ffc   data  0x 0 0x 0 0xff 0xfc
  program number     2 has PID 0x  47   data  0x 0 0x 2 0xe0 0x47
  program number     4 has PID 0x  57   data  0x 0 0x 4 0xe0 0x57
  program number     1 has PID 0x  67   data  0x 0 0x 1 0xe0 0x67

2009-11-24 15:32:21.766 ProcessPAT: Program not found in PAT.
                        Rescan your transports.
2009-11-24 15:32:21.766 Desired program #3 not found in PAT.
                        Can Not create single program PAT.
2009-11-24 15:32:40.735 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-24 15:43:04.168 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Can not measure Signal Strength
                        eno: Invalid argument (22)
2009-11-24 15:43:04.171 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Can not measure S/N
                        eno: Invalid argument (22)
2009-11-24 15:44:43.564 MainServer::HandleVersion - Client speaks protocol version 8 but we speak 50!
2009-11-24 15:44:43.567 MainServer, Warning: Unknown socket closing MythSocket(0x8d9bed0)
2009-11-24 15:44:43.567 MainServer::ANN Playback
2009-11-24 15:44:43.568 adding: mythtv-backend-server as a client (events: 0)
2009-11-24 15:44:43.570 MainServer::HandleVersion - Client speaks protocol version 8 but we speak 50!
2009-11-24 15:44:43.571 MainServer, Warning: Unknown socket closing MythSocket(0x8d54200)
2009-11-24 15:44:43.572 MainServer::ANN Playback
2009-11-24 15:44:43.573 adding: mythtv-backend-server as a client (events: 0)
2009-11-24 15:47:40.778 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-24 15:48:25.837 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Can not measure Signal Strength
                        eno: Invalid argument (22)
2009-11-24 15:48:25.841 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Can not measure S/N
                        eno: Invalid argument (22)
2009-11-24 15:48:26.243 Program #16 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(65) extension(0x178a)
      version(5) current(1) section(0) last_section(0)
         tsid: 6026
 programCount: 14
  program number     0 has PID 0x1ffc   data  0x 0 0x 0 0xff 0xfc
  program number     1 has PID 0x  47   data  0x 0 0x 1 0xe0 0x47
  program number     3 has PID 0x  57   data  0x 0 0x 3 0xe0 0x57
  program number     4 has PID 0x  67   data  0x 0 0x 4 0xe0 0x67
  program number     5 has PID 0x  77   data  0x 0 0x 5 0xe0 0x77
  program number     6 has PID 0x  87   data  0x 0 0x 6 0xe0 0x87
  program number     7 has PID 0x  97   data  0x 0 0x 7 0xe0 0x97
  program number     9 has PID 0x  a7   data  0x 0 0x 9 0xe0 0xa7
  program number     2 has PID 0x  b7   data  0x 0 0x 2 0xe0 0xb7
  program number     8 has PID 0x  c7   data  0x 0 0x 8 0xe0 0xc7
  program number    10 has PID 0x  d7   data  0x 0 0x a 0xe0 0xd7
  program number    11 has PID 0x  e7   data  0x 0 0x b 0xe0 0xe7
  program number    12 has PID 0x  f7   data  0x 0 0x c 0xe0 0xf7
  program number    13 has PID 0x 107   data  0x 0 0x d 0xe1 0x 7

2009-11-24 15:48:26.696 ProcessPAT: Program not found in PAT.
                        Rescan your transports.
2009-11-24 15:48:26.697 Desired program #16 not found in PAT.
                        Can Not create single program PAT.



```

and heres the xbmc log:


```

15:31:39 T:3079415696 M:2546823168  NOTICE: -----------------------------------------------------------------------
15:31:39 T:3079415696 M:2546823168  NOTICE: Starting XBMC, Platform: GNU/Linux.  Built on May 25 2009 (SVN:20654)
15:31:39 T:3079415696 M:2546823168  NOTICE: special://xbmc/ is mapped to: /usr/share/xbmc
15:31:39 T:3079415696 M:2546823168  NOTICE: special://masterprofile/ is mapped to: /home/user/.xbmc/userdata
15:31:39 T:3079415696 M:2546823168  NOTICE: special://home/ is mapped to: /home/user/.xbmc
15:31:39 T:3079415696 M:2546823168  NOTICE: special://temp/ is mapped to: /home/user/.xbmc/temp
15:31:39 T:3079415696 M:2546823168  NOTICE: The executable running is: /usr/share/xbmc/xbmc.bin
15:31:39 T:3079415696 M:2546823168  NOTICE: Log File is located: /home/user/.xbmc/temp/xbmc.log
15:31:39 T:3079415696 M:2546823168  NOTICE: -----------------------------------------------------------------------
15:31:39 T:3079415696 M:2546315264  NOTICE: Setup SDL
15:31:39 T:3079415696 M:2545446912    INFO: Available videomodes (xrandr):
15:31:39 T:3079415696 M:2545446912    INFO: Number of connected outputs: 1
15:31:39 T:3079415696 M:2545446912    INFO: Output 'default' has 13 modes
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x146 Name:1200x675 Refresh:50.000000 Width:1200 Height:675
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x147 Name:800x600 Refresh:51.000000 Width:800 Height:600
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x148 Name:800x600 Refresh:52.000000 Width:800 Height:600
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x149 Name:680x384 Refresh:53.000000 Width:680 Height:384
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x14a Name:680x384 Refresh:54.000000 Width:680 Height:384
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x14b Name:640x480 Refresh:55.000000 Width:640 Height:480
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x14c Name:512x384 Refresh:56.000000 Width:512 Height:384
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x14d Name:320x240 Refresh:57.000000 Width:320 Height:240
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x169 Name:480i/60 Refresh:30.000000 Width:640 Height:480
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x16a Name:480p/60 Refresh:60.000000 Width:640 Height:480
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x16b Name:720p/60 Refresh:60.000000 Width:1280 Height:720
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x16c Name:1080i/60 Refresh:30.000000 Width:1920 Height:1080
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912    INFO: ID:0x16d Name:1080p/60 Refresh:60.000000 Width:1920 Height:1080
15:31:39 T:3079415696 M:2545446912    INFO: Pixel Ratio: 1.000000
15:31:39 T:3079415696 M:2545446912   DEBUG: CLowLevelKeyboard::Initialize - XKb symbols pc_us_inet(evdev)
15:31:39 T:3079415696 M:2545446912    INFO: LIRC Initialize: connect failed: No such file or directory
15:31:39 T:3079415696 M:2545446912    INFO: Drives are mapped
15:31:39 T:3079415696 M:2545446912  NOTICE: load settings...
15:31:39 T:3079415696 M:2545446912  NOTICE: special://profile/ is mapped to: special://masterprofile/
15:31:39 T:3079415696 M:2545446912  NOTICE: loading special://masterprofile/guisettings.xml
15:31:39 T:3079415696 M:2545446912  NOTICE: Getting hardware information now...
15:31:39 T:3079415696 M:2545446912    INFO: Using analog output
15:31:39 T:3079415696 M:2545446912    INFO: AC3 pass through is enabled
15:31:39 T:3079415696 M:2545446912    INFO: DTS pass through is enabled
15:31:39 T:3079415696 M:2545446912  NOTICE: Checking resolution 10
15:31:39 T:3079415696 M:2545446912  NOTICE: Setting autoresolution mode 3
15:31:39 T:3079415696 M:2545446912  NOTICE: No advancedsettings.xml to load (special://masterprofile/advancedsettings.xml)
15:31:39 T:3079415696 M:2545446912  NOTICE: Default DVD Player: dvdplayer
15:31:39 T:3079415696 M:2545446912  NOTICE: Default Video Player: dvdplayer
15:31:39 T:3079415696 M:2545446912  NOTICE: Default Audio Player: paplayer
15:31:39 T:3079415696 M:2545446912  NOTICE: special://masterprofile/sources.xml
15:31:39 T:3079415696 M:2545446912    INFO: XRANDR: /usr/share/xbmc/xbmc-xrandr --output default --mode 0x146
15:31:39 T:3079415696 M:2545528832   DEBUG: Constructing surface 720x480, shared=(nil), fullscreen=0
15:31:39 T:3079415696 M:2545528832    INFO: GLX Info: NOT Using destination window
15:31:39 T:3079415696 M:2545750016  NOTICE: Using fbConfig[0]
15:31:39 T:3079415696 M:2545750016    INFO: GLX Info: Using parent window
15:31:39 T:3079415696 M:2545643520    INFO: GLX Info: Creating unshared context
15:31:39 T:3079415696 M:2540916736  NOTICE: GL_VENDOR = NVIDIA Corporation
15:31:39 T:3079415696 M:2540916736  NOTICE: GL_RENDERER = GeForce GTX 280/PCI/SSE2
15:31:39 T:3079415696 M:2540916736  NOTICE: GL_VERSION = 3.1.0 NVIDIA 190.18
15:31:39 T:3079415696 M:2540916736  NOTICE: GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_instanced GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_framebuffer_object GL_ARB_geometry_shader4 GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_copy_image GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_parameter_buffer_object2 GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_transform_feedback2 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NV_vertex_buffer_unified_memory GL_NV_shader_buffer_load GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
15:31:39 T:3079415696 M:2540916736    INFO: GL: Maximum texture width: 8192
15:31:39 T:3079415696 M:2540916736    INFO: load language info file: special://xbmc/language/English/langinfo.xml
15:31:39 T:3079415696 M:2540916736 WARNING: Trying to access old style dir: D:\media\media\Textures.xpr
15:31:39 T:3079415696 M:2539139072   DEBUG: Load special://xbmc/media/Splash.png: 16.7ms
15:31:39 T:3079415696 M:2540408832    INFO: load language file:special://xbmc/language/English/strings.xml
15:31:39 T:3079415696 M:2540408832    INFO: load keymapping
15:31:39 T:3079415696 M:2540408832    INFO: Loading special://xbmc/system/Keymap.xml
15:31:39 T:3079415696 M:2540408832   DEBUG: CButtonTranslator::Load - no userdata keymap found, skipping
15:31:39 T:3079415696 M:2540408832    INFO: Loading special://xbmc/system/Lircmap.xml
15:31:39 T:3079415696 M:2540408832    INFO: Loading special://masterprofile/Lircmap.xml
15:31:39 T:3079415696 M:2540408832    INFO: Checking skin version of: Rapier
15:31:39 T:3079415696 M:2540408832    INFO: The above skin isn't suitable - checking the version of the default: PM3.HD
15:31:39 T:3079415696 M:2540408832    INFO: Skin version is: 2.1
15:31:39 T:3079415696 M:2540408832    INFO:  GUI format 720x480 480p 16:9
15:31:39 T:3079415696 M:2540408832    INFO: install unhandled exception filter
15:31:39 T:3079415696 M:2540408832    INFO: creating subdirectories
15:31:39 T:3079415696 M:2540408832    INFO: userdata folder: special://masterprofile/
15:31:39 T:3079415696 M:2540408832    INFO:   recording folder:
15:31:39 T:3079415696 M:2540408832    INFO:   screenshots folder:
15:31:39 T:3079415696 M:2540408832    INFO:   thumbnails folder:special://masterprofile/Thumbnails
15:31:39 T:3079415696 M:2540408832  NOTICE: start dvd mediatype detection
15:31:39 T:34270064 M:2540408832   DEBUG: Running thread 34270064
15:31:39 T:34270064 M:2540408832   DEBUG: thread start, auto delete: 0
15:31:39 T:34270064 M:2540408832   DEBUG: Compiled with libcdio Version 0.80
15:31:39 T:3079415696 M:2540408832  NOTICE: initializing playlistplayer
15:31:39 T:3079415696 M:2540408832  NOTICE: DONE initializing playlistplayer
15:31:39 T:3079415696 M:2540408832  NOTICE: load default skin:[Rapier]
15:31:39 T:3079415696 M:2540408832    INFO:   load skin from:special://home/skin/Rapier
15:31:39 T:3079415696 M:2540408832    INFO:   delete old skin...
15:31:39 T:3079415696 M:2540408832   DEBUG: ------------------- GUI_MSG_WINDOW_DEINIT
15:31:39 T:3079415696 M:2540408832   DEBUG: Sort by: Size
15:31:39 T:3079415696 M:2540408832   DEBUG: -------------------
15:31:39 T:3079415696 M:2540408832   DEBUG: ------------------- GUI_MSG_WINDOW_DEINIT
15:31:39 T:3079415696 M:2540408832   DEBUG:
15:31:39 T:3079415696 M:2540408832   DEBUG: -------------------
15:31:39 T:3079415696 M:2540408832    INFO: Default 4:3 resolution directory is special://home/skin/Rapier/720p
15:31:39 T:3079415696 M:2540408832    INFO: Default 16:9 resolution directory is special://home/skin/Rapier/720p
15:31:39 T:3079415696 M:2540408832    INFO: Skin version is: 2.11
15:31:39 T:3079415696 M:2540408832    INFO: Loading skin includes from /home/user/.xbmc/skin/Rapier/720p/includes.xml
15:31:39 T:3079415696 M:2538885120 WARNING: CreateFile, successfuly opened </home/user/.xbmc/skin/Rapier/720p/includes_MediaFlags.xml> instead of </home/user/.xbmc/skin/Rapier/720p/Includes_MediaFlags.xml>
15:31:39 T:3079415696 M:2538631168    INFO:   load fonts for skin...
15:31:39 T:3079415696 M:2538631168    INFO: Loading fonts from special://home/skin/Rapier/720p/Font.xml
15:31:39 T:3079415696 M:2538377216    INFO:   load new skin...
15:31:39 T:3079415696 M:2538377216    INFO: Skin version is: 2.11
15:31:39 T:3079415696 M:2538377216    INFO: Loading skin file: Home.xml
15:31:39 T:3079415696 M:2538123264   DEBUG: Load Home.xml: 16.43ms
15:31:39 T:3079415696 M:2538123264    INFO: Loading user windows, path special://home/skin/Rapier/720p
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_ViewModes.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_SystemSubMenu.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_SystemInfo.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_SortMethods.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_SkinSettings.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_Search.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_LibraryOptions.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_GeneralSubMenu.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_Credits.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading user windows, path special://home/skin/Rapier/720p
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_ViewModes.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_SystemSubMenu.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_SystemInfo.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_SortMethods.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_SkinSettings.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_Search.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_LibraryOptions.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_GeneralSubMenu.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_Credits.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading user windows, path special://home/skin/Rapier/720p
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_ViewModes.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_SystemSubMenu.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_SystemInfo.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_SortMethods.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_SkinSettings.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_Search.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_LibraryOptions.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_GeneralSubMenu.xml
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: special://home/skin/Rapier/720p/custom_Credits.xml
15:31:39 T:3079415696 M:2537869312   DEBUG: Load Skin XML: 49.26ms
15:31:39 T:3079415696 M:2537869312    INFO:   initialize new skin...
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: Pointer.xml
15:31:39 T:3079415696 M:2537869312   DEBUG: Load Pointer.xml: 0.50ms
15:31:39 T:3079415696 M:2537869312   DEBUG: Load pointer.png: 0.1ms (bundled)
15:31:39 T:3079415696 M:2537869312   DEBUG: Load pointer-drag.png: 0.0ms (bundled)
15:31:39 T:3079415696 M:2537869312   DEBUG: Load pointer-click.png: 0.0ms (bundled)
15:31:39 T:3079415696 M:2537869312   DEBUG: Alloc resources: 1.94ms (0.58 ms skin load, 0.96 ms preload)
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: DialogVolumeBar.xml
15:31:39 T:3079415696 M:2537869312   DEBUG: Load DialogVolumeBar.xml: 0.61ms
15:31:39 T:3079415696 M:2537869312   DEBUG: Alloc resources: 0.70ms (0.70 ms skin load, 0.00 ms preload)
15:31:39 T:3079415696 M:2537869312    INFO: Loading skin file: DialogSeekBar.xml
15:31:39 T:3079415696 M:2537869312   ERROR: Window Translator: Can't find window sliderdialog
15:31:39 T:3079415696 M:2537869312   ERROR: Error evaluating boolean expression Window.IsActive(SliderDialog) | Window.IsActive(3011) | Player.ShowCodec
15:31:39 T:3079415696 M:2537615360   DEBUG: Load DialogSeekBar.xml: 13.55ms
15:31:39 T:3079415696 M:2537615360   DEBUG: Load scrollbar-background.png: 0.0ms (bundled)
15:31:39 T:3079415696 M:2537615360   DEBUG: Load scrollbar-slider-horz-nofocus.png: 0.0ms (bundled)
15:31:39 T:3079415696 M:2537615360   DEBUG: Alloc resources: 14.13ms (13.77 ms skin load, 0.11 ms preload)
15:31:39 T:3079415696 M:2537615360    INFO: Loading skin file: DialogKaiToast.xml
15:31:39 T:3079415696 M:2537615360   DEBUG: Load DialogKaiToast.xml: 0.61ms
15:31:39 T:3079415696 M:2537615360   DEBUG: Alloc resources: 0.70ms (0.70 ms skin load, 0.00 ms preload)
15:31:39 T:3079415696 M:2537615360    INFO: Loading skin file: DialogMuteBug.xml
15:31:39 T:3079415696 M:2537615360   DEBUG: Load DialogMuteBug.xml: 0.53ms
15:31:39 T:3079415696 M:2537615360   DEBUG: Alloc resources: 0.61ms (0.61 ms skin load, 0.00 ms preload)
15:31:39 T:3079415696 M:2537582592    INFO: Loading special://home/skin/Rapier/sounds/sounds.xml
15:31:39 T:3079415696 M:2537582592    INFO:   skin loaded...
15:31:39 T:3079415696 M:2537582592   DEBUG: SECTION:LoadDLL(/usr/lib/libcurl.so)
15:31:39 T:3079415696 M:2537582592   DEBUG: Loading: /usr/lib/libcurl.so
15:31:39 T:3079415696 M:2537582592   DEBUG: Activating window ID: 12999
15:31:39 T:3079415696 M:2537582592   DEBUG: Checking if window ID 12999 is locked.
15:31:39 T:3079415696 M:2535550976   DEBUG: ------------------- GUI_MSG_WINDOW_INIT
15:31:39 T:3079415696 M:2535550976   DEBUG:
15:31:39 T:3079415696 M:2535550976   DEBUG: -------------------
15:31:39 T:3079415696 M:2535550976    INFO: Loading skin file: Startup.xml
15:31:39 T:3079415696 M:2535550976   DEBUG: Load Startup.xml: 0.50ms
15:31:39 T:3079415696 M:2535550976   DEBUG: Alloc resources: 0.61ms (0.59 ms skin load, 0.02 ms preload)
15:31:39 T:81107824 M:2535550976   DEBUG: Running thread 81107824
15:31:39 T:81107824 M:2535550976   DEBUG: thread start, auto delete: 1
15:31:39 T:3079415696 M:2535550976    INFO: removing tempfiles
15:31:39 T:81107824 M:2535550976    INFO: easy_aquire - Created session to http://www.google.com
15:31:39 T:3079415696 M:2535550976  NOTICE: Updating video library on startup
15:31:39 T:3079415696 M:2535550976   DEBUG: ------------------- GUI_MSG_WINDOW_INIT
15:31:39 T:3079415696 M:2535550976   DEBUG:
15:31:39 T:3079415696 M:2535550976   DEBUG: -------------------
15:31:39 T:3079415696 M:2535550976    INFO: Loading skin file: DialogVideoScan.xml
15:31:39 T:3079415696 M:2535804928   DEBUG: Load DialogVideoScan.xml: 1.05ms
15:31:39 T:3079415696 M:2536058880   DEBUG: Alloc resources: 1.16ms (1.15 ms skin load, 0.00 ms preload)
15:31:39 T:3079415696 M:2536058880   ERROR: Control 402 in window 10133 has been asked to focus, but it can't
15:31:39 T:89500528 M:2536058880   DEBUG: Running thread 89500528
15:31:39 T:89500528 M:2535804928   DEBUG: thread start, auto delete: 0
15:31:39 T:89500528 M:2535297024   DEBUG: Process - Starting scan
15:31:39 T:3079415696 M:2535297024    INFO: HAL: Starting initializing
15:31:39 T:97893232 M:2535297024   DEBUG: Running thread 97893232
15:31:39 T:97893232 M:2535297024   DEBUG: thread start, auto delete: 0
15:31:39 T:97893232 M:2535297024   DEBUG: Thread 97893232 terminating
15:31:39 T:3079415696 M:2535043072   DEBUG: HAL: Clearing old global device list, if any
15:31:39 T:3079415696 M:2535043072  NOTICE: HAL: Generating global device list
15:31:39 T:3079415696 M:2535043072   DEBUG: HAL: Added - disk | UUID 0fc5ea0c-8352-465f-8266-aa0ecadd087b | FileSystem reiserfs | Mounted on / | HotPlugged NO  | Type 1 |Approved NO
15:31:39 T:3079415696 M:2535043072  NOTICE: LFS: Added - disk | Volume (reiserfs)
15:31:39 T:3079415696 M:2534789120   DEBUG: HAL: Added - disk | FileSystem nvidia_raid_member | HotPlugged NO  | Type 1 |Approved NO
15:31:39 T:3079415696 M:2534789120  NOTICE: LFS: Added - disk | Volume (nvidia_raid_member)
15:31:39 T:3079415696 M:2534535168   DEBUG: HAL: Added - disk | FileSystem nvidia_raid_member | HotPlugged NO  | Type 1 |Approved NO
15:31:39 T:3079415696 M:2534535168  NOTICE: LFS: Updated - disk | Volume (nvidia_raid_member)
15:31:39 T:3079415696 M:2534535168   DEBUG: HAL: Added - disk | UUID fdcb6554-5ec5-4b35-aa4a-f464f59b043f | FileSystem swap | HotPlugged NO  | Type 1 |Approved NO
15:31:39 T:3079415696 M:2534535168  NOTICE: LFS: Added - disk | Volume (swap)
15:31:39 T:3079415696 M:2535804928   DEBUG: HAL: Added - disk | UUID 88BA5192BA517E1E | FileSystem ntfs-3g | HotPlugged NO  | Type 1 |Approved YES
15:31:39 T:3079415696 M:2535804928  NOTICE: LFS: Added - disk | Volume (ntfs)
15:31:39 T:89500528 M:2535804928   DEBUG: Process - Finished scan
15:31:39 T:89500528 M:2535804928  NOTICE: My Videos: Scanning for video info using worker thread, operation took 00:00
15:31:39 T:89500528 M:2535804928    INFO: Video scan was stopped or finished ... restoring FindRemoteThumbs
15:31:39 T:89500528 M:2535804928   DEBUG: Thread 89500528 terminating
15:31:39 T:3079415696 M:2535804928    INFO: HAL: Generated global device list, found 139
15:31:39 T:3079415696 M:2535804928    INFO: HAL: Sucessfully initialized
15:31:39 T:3079415696 M:2535804928  NOTICE: initialize done
15:31:39 T:3079415696 M:2535804928  NOTICE: Running the application...
15:31:39 T:3079415696 M:2535804928   DEBUG: OnMessage : Translating ReplaceWindow(Home)
15:31:39 T:3079415696 M:2535804928   DEBUG: OnMessage : To ReplaceWindow(Home)
15:31:39 T:3079415696 M:2535804928   DEBUG: Activating window ID: 10000
15:31:39 T:3079415696 M:2535804928   DEBUG: Checking if window ID 10000 is locked.
15:31:39 T:3079415696 M:2535804928   DEBUG: ------------------- GUI_MSG_WINDOW_DEINIT
15:31:39 T:3079415696 M:2535804928   DEBUG:
15:31:39 T:3079415696 M:2535804928   DEBUG: -------------------
15:31:39 T:3079415696 M:2535804928   DEBUG: ------------------- GUI_MSG_WINDOW_INIT
15:31:39 T:3079415696 M:2535804928   DEBUG: Home
15:31:39 T:3079415696 M:2535804928   DEBUG: -------------------
15:31:39 T:3079415696 M:2535804928   DEBUG: Load arrow-scroll-left-focus2.png: 0.1ms (bundled)
15:31:39 T:3079415696 M:2535804928   DEBUG: Load arrow-scroll-left-nofocus2.png: 0.0ms (bundled)
15:31:39 T:3079415696 M:2535804928   DEBUG: Load top-bar-eject-focus.png: 0.0ms (bundled)
15:31:39 T:3079415696 M:2535804928   DEBUG: Load top-bar-eject-nofocus.png: 0.0ms (bundled)
15:31:39 T:3079415696 M:2535804928   DEBUG: Load top-bar-power-focus.png: 0.0ms (bundled)
15:31:39 T:3079415696 M:2535804928   DEBUG: Load top-bar-power-nofocus.png: 0.0ms (bundled)
15:31:39 T:3079415696 M:2535804928   DEBUG: SECTION:LoadDLL(special://xbmc/system/ImageLib-i486-linux.so)
15:31:39 T:3079415696 M:2535804928   DEBUG: Loading: /usr/share/xbmc/system/ImageLib-i486-linux.so
15:31:39 T:3079415696 M:2535804928    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-home-focus.png Error: (2)
15:31:39 T:3079415696 M:2535804928   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-home-focus.png
15:31:39 T:3079415696 M:2535804928   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-home-focus.png
15:31:39 T:3079415696 M:2535804928    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-home-nofocus.png Error: (2)
15:31:39 T:3079415696 M:2535804928   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-home-nofocus.png
15:31:39 T:3079415696 M:2535804928   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-home-nofocus.png
15:31:39 T:3079415696 M:2535804928    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:31:39 T:3079415696 M:2535804928   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:31:39 T:3079415696 M:2535804928   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:31:39 T:3079415696 M:2535804928    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:31:39 T:3079415696 M:2535804928   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:31:39 T:3079415696 M:2535804928   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:31:39 T:3079415696 M:2535804928   DEBUG: Alloc resources: 3.33ms (0.01 ms skin load, 0.09 ms preload)
15:31:39 T:3079415696 M:2535804928   DEBUG: NetworkMessage - Starting network services
15:31:39 T:3079415696 M:2535804928  NOTICE: Webserver: Starting...
15:31:39 T:3079415696 M:2535804928   DEBUG: xbmcHttpShim starts
15:31:39 T:97893232 M:2535804928   DEBUG: Running thread 97893232
15:31:39 T:97893232 M:2535804928   DEBUG: thread start, auto delete: 0
15:31:39 T:97893232 M:2535804928    INFO: WebServer: Server starting using /usr/share/xbmc/web on 192.168.1.2:8080
15:31:39 T:97893232 M:2535804928   DEBUG: DB: Registering database table <users>
15:31:39 T:97893232 M:2535804928   DEBUG: DB: Registering database table <groups>
15:31:39 T:97893232 M:2535804928   DEBUG: DB: Registering database table <access>
15:31:39 T:97893232 M:2535804928   DEBUG: UM: Loading User Configuration from file <umconfig.txt>
15:31:39 T:97893232 M:2535804928   DEBUG: DB: About to read data file </usr/share/xbmc/web/umconfig.txt>
15:31:39 T:97893232 M:2535804928   DEBUG: DB: Failed to stat persistent data file.
15:31:39 T:97893232 M:2535804928   DEBUG: webs: Listening for HTTP requests at address 192.168.1.2:8080
15:31:39 T:97893232 M:2535804928  NOTICE: Webserver: Started
15:31:39 T:3079415696 M:2535804928   DEBUG: UM: Adding group <sys_xbox>
15:31:39 T:3079415696 M:2535804928   DEBUG: DB: Adding a row to table <groups>
15:31:39 T:3079415696 M:2535804928   DEBUG: UM: Adding User <xbmc>
15:31:39 T:3079415696 M:2535804928   DEBUG: DB: Adding a row to table <users>
15:31:39 T:3079415696 M:2535804928   DEBUG: UM: Adding Access Limit for </>
15:31:39 T:3079415696 M:2535804928   DEBUG: DB: Adding a row to table <access>
15:31:39 T:3079415696 M:2535804928   DEBUG: UM: Writing User Configuration to file <umconfig.txt>
15:31:39 T:3079415696 M:2535804928   DEBUG: DB: About to save database to file
15:31:39 T:3079415696 M:2535804928   DEBUG: WARNING: Failed to open file /usr/share/xbmc/web/data.tmp
15:31:39 T:3079415696 M:2535804928   DEBUG: CZeroconfAvahi::clientCallback: client is up and running
15:31:39 T:3079415696 M:2535804928  NOTICE: ES: Starting event server
15:31:39 T:2997160816 M:2535804928   DEBUG: Running thread 2997160816
15:31:39 T:2997160816 M:2535804928   DEBUG: thread start, auto delete: 0
15:31:39 T:3079415696 M:2535804928  NOTICE: DS: Starting dbus server
15:31:39 T:2997160816 M:2535804928  NOTICE: ES: Starting UDP Event server on 127.0.0.1:9777
15:31:39 T:2997160816 M:2535804928  NOTICE: UDP: Listening on port 9777
15:31:39 T:2988768112 M:2535804928   DEBUG: Running thread 2988768112
15:31:39 T:2988768112 M:2535804928   DEBUG: thread start, auto delete: 0
15:31:39 T:2988768112 M:2535804928  NOTICE: DS: Starting DBUS server in Run Application aka thread
15:31:39 T:3079415696 M:2535804928  NOTICE: starting zeroconf publishing
15:31:39 T:3079415696 M:2535804928   DEBUG: CZeroconfAvahi::doPublishService identifier: servers.eventserver type: _xbmc-events._udp name:XBMC Event Server port:9777
15:31:39 T:3079415696 M:2535804928   DEBUG: CZeroconfAvahi::addService() named: XBMC Event Server type: _xbmc-events._udp port:9777
15:31:39 T:3079415696 M:2535804928   DEBUG: CZeroconfAvahi::doPublishService identifier: servers.webapi type: _xbmc-web._tcp name:XBMC HTTP API port:8080
15:31:39 T:3079415696 M:2535804928   DEBUG: CZeroconfAvahi::addService() named: XBMC HTTP API type: _xbmc-web._tcp port:8080
15:31:39 T:3079415696 M:2535804928   DEBUG: CZeroconfAvahi::doPublishService identifier: servers.webserver type: _http._tcp name:XBMC Web Server port:8080
15:31:39 T:3079415696 M:2535804928   DEBUG: CZeroconfAvahi::addService() named: XBMC Web Server type: _http._tcp port:8080
15:31:39 T:2980375408 M:2535804928   DEBUG: Running thread 2980375408
15:31:39 T:2980375408 M:2535804928   DEBUG: thread start, auto delete: 0
15:31:39 T:2980375408 M:2535804928   DEBUG: Audioscrobbler worker thread starting
15:31:39 T:3079415696 M:2535043072   DEBUG: Load home-pictures-icon.png: 3.1ms (bundled)
15:31:39 T:3079415696 M:2535043072   DEBUG: Load bottom-bar-top.png: 0.0ms (bundled)
15:31:39 T:3079415696 M:2534281216   DEBUG: Load bottom-bar-background.png: 2.3ms (bundled)
15:31:39 T:3079415696 M:2534281216   DEBUG: Load programs-text-blurred.png: 0.3ms (bundled)
15:31:39 T:3079415696 M:2534281216   DEBUG: Load music-text-blurred.png: 0.2ms (bundled)
15:31:39 T:3079415696 M:2534281216   DEBUG: Load pictures-text-focus.png: 0.4ms (bundled)
15:31:39 T:3079415696 M:2532757504   DEBUG: Load bottom-bar-overlay.png: 10.0ms (bundled)
15:31:39 T:3079415696 M:2532757504    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-background.png Error: (2)
15:31:39 T:3079415696 M:2532757504   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-background.png
15:31:39 T:3079415696 M:2532757504   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-background.png
15:31:39 T:3079415696 M:2532757504    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:31:39 T:3079415696 M:2532757504   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:31:39 T:3079415696 M:2532757504   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:31:39 T:3079415696 M:2532757504    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-separator-nofocus.png Error: (2)
15:31:39 T:3079415696 M:2532757504   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-separator-nofocus.png
15:31:39 T:3079415696 M:2532757504   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-separator-nofocus.png
15:31:39 T:3079415696 M:2532757504    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:31:39 T:3079415696 M:2532757504   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:31:39 T:3079415696 M:2532757504   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:31:39 T:3079415696 M:2532757504   DEBUG: ------------------- GUI_MSG_WINDOW_DEINIT
15:31:39 T:3079415696 M:2532757504   DEBUG:
15:31:39 T:3079415696 M:2532757504   DEBUG: -------------------
15:31:39 T:81107824 M:2532757504   DEBUG: FileCurl::Close(0x4d57fac) http://www.google.com/
15:31:39 T:81107824 M:2532757504   DEBUG: Thread 81107824 terminating (autodelete)
15:31:39 T:3079415696 M:2532757504   DEBUG: Load pictures-text-blurred.png: 0.3ms (bundled)
15:31:40 T:3079415696 M:2533138432   DEBUG: Load control-area-background.png: 0.0ms (bundled)
15:31:40 T:2969561968 M:2532376576   DEBUG: Running thread 2969561968
15:31:40 T:2969561968 M:2532376576   DEBUG: thread start, auto delete: 0
15:31:40 T:2969561968 M:2532376576   DEBUG: FileCurl::Open(0xb0ffd01c) http://feeds.feedburner.com/xbmc
15:31:40 T:2969561968 M:2532376576    INFO: easy_aquire - Created session to http://feeds.feedburner.com
15:31:40 T:2969561968 M:2532376576   DEBUG: FileCurl::Close(0xb0ffd01c) http://feeds.feedburner.com/xbmc
15:31:40 T:2969561968 M:2532376576   DEBUG: Got rss feed: http://feeds.feedburner.com/xbmc
15:31:40 T:2969561968 M:2532376576   DEBUG: RSS feed encoding: ISO-8859-1
15:31:40 T:2969561968 M:2532376576   DEBUG: Parsed rss feed: http://feeds.feedburner.com/xbmc
15:31:40 T:2969561968 M:2532376576   DEBUG: Thread 2969561968 terminating
15:31:40 T:127929200 M:2532503552   DEBUG: CZeroconfAvahi::groupCallback: Service successfully established
15:31:40 T:127929200 M:2532503552   DEBUG: CZeroconfAvahi::groupCallback: Service successfully established
15:31:40 T:127929200 M:2532503552   DEBUG: CZeroconfAvahi::groupCallback: Service successfully established
15:31:42 T:3079415696 M:2532818944   DEBUG: SDLKeyboard: scancode: 114, sym: 275, unicode: 0, modifier: 0
15:31:42 T:3079415696 M:2532818944   DEBUG: OnKey: 61479 pressed, action is 2
15:31:42 T:3079415696 M:2532818944   DEBUG: SDLKeyboard: scancode: 114, sym: 275, unicode: 0, modifier: 0
15:31:42 T:3079415696 M:2532818944   DEBUG: OnKey: 61479 pressed, action is 2
15:31:42 T:3079415696 M:2532818944   DEBUG: Load home-music-icon.png: 2.8ms (bundled)
15:31:42 T:3079415696 M:2532818944   DEBUG: Load music-text-focus.png: 0.2ms (bundled)
15:31:42 T:3079415696 M:2532818944   DEBUG: Load videos-text-blurred.png: 0.2ms (bundled)
15:31:42 T:3079415696 M:2532818944   DEBUG: SDLKeyboard: scancode: 114, sym: 275, unicode: 0, modifier: 0
15:31:42 T:3079415696 M:2532818944   DEBUG: OnKey: 61479 pressed, action is 2
15:31:42 T:3079415696 M:2532818944   DEBUG: Load home-videos-icon.png: 2.6ms (bundled)
15:31:42 T:3079415696 M:2532818944   DEBUG: Load videos-text-focus.png: 0.2ms (bundled)
15:31:42 T:3079415696 M:2532818944   DEBUG: Load general-text-blurred.png: 0.2ms (bundled)
15:31:43 T:3079415696 M:2532691968   DEBUG: SDLKeyboard: scancode: 114, sym: 275, unicode: 0, modifier: 0
15:31:43 T:3079415696 M:2532691968   DEBUG: OnKey: 61479 pressed, action is 2
15:31:43 T:3079415696 M:2532438016   DEBUG: Load home-general-icon.png: 14.9ms (bundled)
15:31:43 T:3079415696 M:2532438016   DEBUG: Load general-text-focus.png: 0.2ms (bundled)
15:31:43 T:3079415696 M:2532438016   DEBUG: Load system-text-blurred.png: 0.2ms (bundled)
15:31:44 T:3079415696 M:2532446208   DEBUG: SDLKeyboard: scancode: 113, sym: 276, unicode: 0, modifier: 0
15:31:44 T:3079415696 M:2532446208   DEBUG: OnKey: 61477 pressed, action is 1
15:31:44 T:3079415696 M:2532446208   DEBUG: Load home-videos-icon.png: 2.5ms (bundled)
15:31:44 T:3079415696 M:2532700160   DEBUG: Load music-text-blurred.png: 0.2ms (bundled)
15:31:44 T:3079415696 M:2532700160   DEBUG: SDLKeyboard: scancode: 36, sym: 13, unicode: 13, modifier: 0
15:31:44 T:3079415696 M:2532700160   DEBUG: OnKey: 61453 pressed, action is 7
15:31:44 T:3079415696 M:2532700160   DEBUG: OnMessage : Translating ActivateWindow(VideoFiles)
15:31:44 T:3079415696 M:2532700160   DEBUG: OnMessage : To ActivateWindow(VideoFiles)
15:31:44 T:3079415696 M:2532700160   DEBUG: Activating window ID: 10024
15:31:44 T:3079415696 M:2532700160   DEBUG: Checking if window ID 10024 is locked.
15:31:44 T:3079415696 M:2532700160   DEBUG: ------------------- GUI_MSG_WINDOW_DEINIT
15:31:44 T:3079415696 M:2532700160   DEBUG: Home
15:31:44 T:3079415696 M:2532700160   DEBUG: -------------------
15:31:45 T:3079415696 M:2533982208    INFO: Attempting to default to:
15:31:45 T:3079415696 M:2533982208   DEBUG: ------------------- GUI_MSG_WINDOW_INIT
15:31:45 T:3079415696 M:2533982208   DEBUG:
15:31:45 T:3079415696 M:2533982208   DEBUG: -------------------
15:31:45 T:3079415696 M:2533982208    INFO: Loading skin file: MyVideo.xml
15:31:45 T:3079415696 M:2533982208 WARNING: Skin has invalid include: BackgroundDim
15:31:45 T:3079415696 M:2533982208 WARNING: Skin has invalid include: BackgroundDim
15:31:45 T:3079415696 M:2533982208 WARNING: Skin has invalid include: BackgroundDim
15:31:45 T:3079415696 M:2533982208   DEBUG: Load MyVideo.xml: 30.26ms
15:31:45 T:3079415696 M:2533982208   DEBUG: Load scrollbar-slider-nofocus.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533982208   DEBUG: Load scrollbar-slider-focus.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533982208   DEBUG: Load view-options-focus.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533982208   DEBUG: Load view-options-nofocus.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533982208   DEBUG: Load view-options-extra-focus.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533982208   DEBUG: Load view-options-extra-nofocus.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533982208   DEBUG: Load menu-bar-button-arrow-focus.png: 0.1ms (bundled)
15:31:45 T:3079415696 M:2533982208   DEBUG: Load menu-bar-button-arrow-nofocus.png: 0.5ms (bundled)
15:31:45 T:3079415696 M:2533982208   DEBUG: Load menu-bar-button-focus.png: 0.1ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load button-focus.png: 2.9ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load button-nofocus.png: 0.1ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load radio-button-focus.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load radio-button-nofocus.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load top-bar-eject-focus.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load top-bar-eject-nofocus.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load top-bar-power-focus.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load top-bar-power-nofocus.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533728256    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-background.png Error: (2)
15:31:45 T:3079415696 M:2533728256   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-background.png
15:31:45 T:3079415696 M:2533728256   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-background.png
15:31:45 T:3079415696 M:2533728256    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-background.png Error: (2)
15:31:45 T:3079415696 M:2533728256   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-background.png
15:31:45 T:3079415696 M:2533728256   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-background.png
15:31:45 T:3079415696 M:2533728256    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-background.png Error: (2)
15:31:45 T:3079415696 M:2533728256   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-background.png
15:31:45 T:3079415696 M:2533728256   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-background.png
15:31:45 T:3079415696 M:2533728256    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-background.png Error: (2)
15:31:45 T:3079415696 M:2533728256   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-background.png
15:31:45 T:3079415696 M:2533728256   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-background.png
15:31:45 T:3079415696 M:2533728256    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-home-focus.png Error: (2)
15:31:45 T:3079415696 M:2533728256   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-home-focus.png
15:31:45 T:3079415696 M:2533728256   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-home-focus.png
15:31:45 T:3079415696 M:2533728256    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-home-nofocus.png Error: (2)
15:31:45 T:3079415696 M:2533728256   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-home-nofocus.png
15:31:45 T:3079415696 M:2533728256   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-home-nofocus.png
15:31:45 T:3079415696 M:2533728256    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:31:45 T:3079415696 M:2533728256   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:31:45 T:3079415696 M:2533728256   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:31:45 T:3079415696 M:2533728256    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:31:45 T:3079415696 M:2533728256   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:31:45 T:3079415696 M:2533728256   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:31:45 T:3079415696 M:2533728256   DEBUG: Alloc resources: 39.45ms (30.73 ms skin load, 0.40 ms preload)
15:31:45 T:3079415696 M:2533728256   DEBUG: CGUIMediaWindow::GetDirectory ()
15:31:45 T:3079415696 M:2533728256   DEBUG:   ParentPath = []
15:31:45 T:3079415696 M:2533728256   DEBUG: Sort, sorting took 0 millis
15:31:45 T:2959080304 M:2533728256   DEBUG: Running thread 2959080304
15:31:45 T:2959080304 M:2533728256   DEBUG: thread start, auto delete: 0
15:31:45 T:2959080304 M:2533728256   DEBUG: Thread 2959080304 terminating
15:31:45 T:3079415696 M:2533728256    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/backgrounds/default-background.jpg Error: (2)
15:31:45 T:3079415696 M:2533728256   ERROR: PICTURE: Error loading image special://skin/images/backgrounds/default-background.jpg
15:31:45 T:3079415696 M:2533728256   ERROR: Texture manager unable to load file: special://skin/images/backgrounds/default-background.jpg
15:31:45 T:3079415696 M:2533728256    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/backgrounds/default-background.jpg Error: (2)
15:31:45 T:3079415696 M:2533728256   ERROR: PICTURE: Error loading image special://skin/images/backgrounds/default-background.jpg
15:31:45 T:3079415696 M:2533728256   ERROR: Texture manager unable to load file: special://skin/images/backgrounds/default-background.jpg
15:31:45 T:3079415696 M:2533728256   DEBUG: Load listview-background-dim.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load button-list-nofocus.png: 0.1ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load defaultNetwork.png.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load defaultFile.png.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load button-list-focus.png: 0.1ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load defaultHardDisk.png.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2533728256   DEBUG: Load bottom-bar-top.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2532458496   DEBUG: Load bottom-bar-background.png: 2.3ms (bundled)
15:31:45 T:3079415696 M:2531188736   DEBUG: Load bottom-bar-overlay.png: 9.8ms (bundled)
15:31:45 T:3079415696 M:2531188736    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-background.png Error: (2)
15:31:45 T:3079415696 M:2531188736   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-background.png
15:31:45 T:3079415696 M:2531188736   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-background.png
15:31:45 T:3079415696 M:2531188736    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:31:45 T:3079415696 M:2531188736   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:31:45 T:3079415696 M:2531188736   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:31:45 T:3079415696 M:2531188736    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-separator-nofocus.png Error: (2)
15:31:45 T:3079415696 M:2531188736   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-separator-nofocus.png
15:31:45 T:3079415696 M:2531188736   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-separator-nofocus.png
15:31:45 T:3079415696 M:2531188736    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-separator-nofocus.png Error: (2)
15:31:45 T:3079415696 M:2531188736   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-separator-nofocus.png
15:31:45 T:3079415696 M:2531188736   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-separator-nofocus.png
15:31:45 T:3079415696 M:2531188736    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-separator-nofocus.png Error: (2)
15:31:45 T:3079415696 M:2531188736   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-separator-nofocus.png
15:31:45 T:3079415696 M:2531188736   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-separator-nofocus.png
15:31:45 T:3079415696 M:2531188736   DEBUG: Load control-area-background.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2531188736   DEBUG: Load menu-bar-separator.png: 0.0ms (bundled)
15:31:45 T:3079415696 M:2531188736   DEBUG: SDLKeyboard: scancode: 116, sym: 274, unicode: 0, modifier: 0
15:31:45 T:3079415696 M:2531188736   DEBUG: OnKey: 61480 pressed, action is 4
15:31:46 T:3079415696 M:2531323904   DEBUG: SDLKeyboard: scancode: 36, sym: 13, unicode: 13, modifier: 0
15:31:46 T:3079415696 M:2531323904   DEBUG: OnKey: 61453 pressed, action is 7
15:31:46 T:3079415696 M:2531323904   DEBUG: Clearing cached fileitems [myth://192.168.1.2/]
15:31:46 T:3079415696 M:2531323904   DEBUG: CGUIMediaWindow::GetDirectory (myth://192.168.1.2/)
15:31:46 T:3079415696 M:2531323904   DEBUG:   ParentPath = []
15:31:46 T:3079415696 M:2531323904   DEBUG: SECTION:LoadDLL(xbmc.so)
15:31:46 T:3079415696 M:2531323904   DEBUG: Loading Internal Library
15:31:46 T:3079415696 M:2531323904   DEBUG: Sort, sorting took 0 millis
15:31:46 T:2959080304 M:2531323904   DEBUG: Running thread 2959080304
15:31:46 T:2959080304 M:2531323904   DEBUG: thread start, auto delete: 0
15:31:46 T:3079415696 M:2531323904   DEBUG: Load button-list-nofocus.png: 0.1ms (bundled)
15:31:46 T:3079415696 M:2531323904   DEBUG: Load defaultFolder.png.png: 0.1ms (bundled)
15:31:46 T:3079415696 M:2531323904   DEBUG: Load button-list-focus.png: 0.1ms (bundled)
15:31:46 T:2959080304 M:2531323904   DEBUG: Thread 2959080304 terminating
15:31:46 T:3079415696 M:2531323904   DEBUG: Load defaultFolderBack.png.png: 0.0ms (bundled)
15:31:46 T:3079415696 M:2531323904   DEBUG: SDLKeyboard: scancode: 116, sym: 274, unicode: 0, modifier: 0
15:31:46 T:3079415696 M:2531323904   DEBUG: OnKey: 61480 pressed, action is 4
15:31:46 T:3079415696 M:2531323904   DEBUG: SDLKeyboard: scancode: 116, sym: 274, unicode: 0, modifier: 0
15:31:46 T:3079415696 M:2531323904   DEBUG: OnKey: 61480 pressed, action is 4
15:31:46 T:3079415696 M:2531323904   DEBUG: SDLKeyboard: scancode: 116, sym: 274, unicode: 0, modifier: 0
15:31:46 T:3079415696 M:2531323904   DEBUG: OnKey: 61480 pressed, action is 4
15:31:47 T:3079415696 M:2531328000   DEBUG: SDLKeyboard: scancode: 36, sym: 13, unicode: 13, modifier: 0
15:31:47 T:3079415696 M:2531328000   DEBUG: OnKey: 61453 pressed, action is 7
15:31:47 T:3079415696 M:2531328000   DEBUG: Clearing cached fileitems [myth://192.168.1.2/channels/]
15:31:47 T:3079415696 M:2531328000   DEBUG: CGUIMediaWindow::GetDirectory (myth://192.168.1.2/channels/)
15:31:47 T:3079415696 M:2531328000   DEBUG:   ParentPath = [myth://192.168.1.2/]
15:31:47 T:3079415696 M:2531328000   DEBUG: Sort, sorting took 0 millis
15:31:47 T:2959080304 M:2531328000   DEBUG: Running thread 2959080304
15:31:47 T:2959080304 M:2531328000   DEBUG: thread start, auto delete: 0
15:31:47 T:2959080304 M:2531328000   DEBUG: Thread 2959080304 terminating
15:31:47 T:3079415696 M:2531328000   DEBUG: Load button-list-focus.png: 0.1ms (bundled)
15:31:47 T:3079415696 M:2531328000   DEBUG: Load defaultFolderBack.png.png: 0.0ms (bundled)
15:31:48 T:3079415696 M:2531328000   DEBUG: SDLKeyboard: scancode: 9, sym: 27, unicode: 27, modifier: 0
15:31:48 T:3079415696 M:2531328000   DEBUG: OnKey: 61467 pressed, action is 10
15:31:48 T:3079415696 M:2531328000   DEBUG: CGUIWindowManager::PreviousWindow: Deactivate
15:31:48 T:3079415696 M:2531328000   DEBUG: ------------------- GUI_MSG_WINDOW_DEINIT
15:31:48 T:3079415696 M:2531328000   DEBUG:
15:31:48 T:3079415696 M:2531328000   DEBUG: -------------------
15:31:48 T:3079415696 M:2533613568   DEBUG: CGUIWindowManager::PreviousWindow: Activate new
15:31:48 T:3079415696 M:2533613568   DEBUG: ------------------- GUI_MSG_WINDOW_INIT
15:31:48 T:3079415696 M:2533613568   DEBUG: Home
15:31:48 T:3079415696 M:2533613568   DEBUG: -------------------
15:31:48 T:3079415696 M:2533613568    INFO: Loading skin file: Home.xml
15:31:48 T:3079415696 M:2533613568   DEBUG: Load Home.xml: 6.77ms
15:31:48 T:3079415696 M:2533613568   DEBUG: Load arrow-scroll-left-focus2.png: 0.0ms (bundled)
15:31:48 T:3079415696 M:2533613568   DEBUG: Load arrow-scroll-left-nofocus2.png: 0.0ms (bundled)
15:31:48 T:3079415696 M:2533613568   DEBUG: Load top-bar-eject-focus.png: 0.0ms (bundled)
15:31:48 T:3079415696 M:2533613568   DEBUG: Load top-bar-eject-nofocus.png: 0.0ms (bundled)
15:31:48 T:3079415696 M:2533613568   DEBUG: Load top-bar-power-focus.png: 0.0ms (bundled)
15:31:48 T:3079415696 M:2533613568   DEBUG: Load top-bar-power-nofocus.png: 0.0ms (bundled)
15:31:48 T:3079415696 M:2533613568    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-home-focus.png Error: (2)
15:31:48 T:3079415696 M:2533613568   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-home-focus.png
15:31:48 T:3079415696 M:2533613568   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-home-focus.png
15:31:48 T:3079415696 M:2533613568    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-home-nofocus.png Error: (2)
15:31:48 T:3079415696 M:2533613568   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-home-nofocus.png
15:31:48 T:3079415696 M:2533613568   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-home-nofocus.png
15:31:48 T:3079415696 M:2533613568    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:31:48 T:3079415696 M:2533613568   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:31:48 T:3079415696 M:2533613568   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:31:48 T:3079415696 M:2533613568    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:31:48 T:3079415696 M:2533613568   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:31:48 T:3079415696 M:2533613568   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:31:48 T:3079415696 M:2533613568   DEBUG: Alloc resources: 9.05ms (6.97 ms skin load, 0.08 ms preload)
15:31:48 T:3079415696 M:2533613568   DEBUG: Load home-videos-icon.png: 2.7ms (bundled)
15:31:48 T:3079415696 M:2533613568   DEBUG: Load bottom-bar-top.png: 0.0ms (bundled)
15:31:48 T:3079415696 M:2532343808   DEBUG: Load bottom-bar-background.png: 2.7ms (bundled)
15:31:48 T:3079415696 M:2532343808   DEBUG: Load music-text-blurred.png: 0.2ms (bundled)
15:31:48 T:3079415696 M:2532343808   DEBUG: Load general-text-blurred.png: 0.2ms (bundled)
15:31:48 T:3079415696 M:2532343808   DEBUG: Load videos-text-focus.png: 0.4ms (bundled)
15:31:48 T:3079415696 M:2530820096   DEBUG: Load bottom-bar-overlay.png: 9.9ms (bundled)
15:31:48 T:3079415696 M:2530820096    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-background.png Error: (2)
15:31:48 T:3079415696 M:2530820096   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-background.png
15:31:48 T:3079415696 M:2530820096   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-background.png
15:31:48 T:3079415696 M:2530820096    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:31:48 T:3079415696 M:2530820096   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:31:48 T:3079415696 M:2530820096   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:31:48 T:3079415696 M:2530820096    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-separator-nofocus.png Error: (2)
15:31:48 T:3079415696 M:2530820096   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-separator-nofocus.png
15:31:48 T:3079415696 M:2530820096   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-separator-nofocus.png
15:31:49 T:3079415696 M:2530824192   DEBUG: Load control-area-background.png: 0.0ms (bundled)
15:31:52 T:3079415696 M:2530824192    INFO: CheckIdle - Closing idle connection to mythtv backend 192.168.1.2
15:32:09 T:3079415696 M:2530824192    INFO: CheckIdle - Closing session to http://www.google.com (easy=0x9136888, multi=(nil))
15:32:10 T:3079415696 M:2530824192    INFO: CheckIdle - Closing session to http://feeds.feedburner.com (easy=0x9153298, multi=0x91990d8)
15:32:19 T:3079415696 M:2530824192   DEBUG: SECTION:UnloadDelayed(DLL: special://xbmc/system/ImageLib-i486-linux.so)
15:32:19 T:3079415696 M:2530824192   DEBUG: Unloading: ImageLib-i486-linux.so
15:32:22 T:3079415696 M:2526625792   DEBUG: SECTION:UnloadDelayed(DLL: xbmc.so)
15:32:22 T:3079415696 M:2526625792   DEBUG: Unloading: xbmc.so
15:37:06 T:3079415696 M:2526625792   DEBUG: Load videos-text-blurred.png: 0.5ms (bundled)
15:44:41 T:3079415696 M:2522472448   DEBUG: SDLKeyboard: scancode: 116, sym: 274, unicode: 0, modifier: 0
15:44:41 T:3079415696 M:2522472448   DEBUG: OnKey: 61480 pressed, action is 4
15:44:41 T:3079415696 M:2522472448   DEBUG: SDLKeyboard: scancode: 113, sym: 276, unicode: 0, modifier: 0
15:44:41 T:3079415696 M:2522472448   DEBUG: OnKey: 61477 pressed, action is 1
15:44:41 T:3079415696 M:2522218496   DEBUG: Load home-music-icon.png: 2.9ms (bundled)
15:44:41 T:3079415696 M:2522218496   DEBUG: Load pictures-text-blurred.png: 0.2ms (bundled)
15:44:41 T:3079415696 M:2522218496   DEBUG: Load music-text-focus.png: 0.2ms (bundled)
15:44:42 T:3079415696 M:2522218496   DEBUG: SDLKeyboard: scancode: 114, sym: 275, unicode: 0, modifier: 0
15:44:42 T:3079415696 M:2522218496   DEBUG: OnKey: 61479 pressed, action is 2
15:44:42 T:3079415696 M:2521710592   DEBUG: Load home-videos-icon.png: 2.7ms (bundled)
15:44:42 T:3079415696 M:2521583616   DEBUG: SDLKeyboard: scancode: 36, sym: 13, unicode: 13, modifier: 0
15:44:42 T:3079415696 M:2521583616   DEBUG: OnKey: 61453 pressed, action is 7
15:44:42 T:3079415696 M:2521583616   DEBUG: OnMessage : Translating ActivateWindow(VideoFiles)
15:44:42 T:3079415696 M:2521583616   DEBUG: OnMessage : To ActivateWindow(VideoFiles)
15:44:42 T:3079415696 M:2521583616   DEBUG: Activating window ID: 10024
15:44:42 T:3079415696 M:2521583616   DEBUG: Checking if window ID 10024 is locked.
15:44:42 T:3079415696 M:2521583616   DEBUG: ------------------- GUI_MSG_WINDOW_DEINIT
15:44:42 T:3079415696 M:2521583616   DEBUG: Home
15:44:42 T:3079415696 M:2521583616   DEBUG: -------------------
15:44:43 T:3079415696 M:2523365376   DEBUG: ------------------- GUI_MSG_WINDOW_INIT
15:44:43 T:3079415696 M:2523365376   DEBUG:
15:44:43 T:3079415696 M:2523365376   DEBUG: -------------------
15:44:43 T:3079415696 M:2523365376    INFO: Loading skin file: MyVideo.xml
15:44:43 T:3079415696 M:2523365376 WARNING: Skin has invalid include: BackgroundDim
15:44:43 T:3079415696 M:2523365376 WARNING: Skin has invalid include: BackgroundDim
15:44:43 T:3079415696 M:2523365376 WARNING: Skin has invalid include: BackgroundDim
15:44:43 T:3079415696 M:2523365376   DEBUG: Load MyVideo.xml: 26.87ms
15:44:43 T:3079415696 M:2523365376   DEBUG: Load scrollbar-slider-nofocus.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load scrollbar-slider-focus.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load view-options-focus.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load view-options-nofocus.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load view-options-extra-focus.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load view-options-extra-nofocus.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load menu-bar-button-arrow-focus.png: 0.1ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load menu-bar-button-arrow-nofocus.png: 0.5ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load menu-bar-button-focus.png: 0.1ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load button-focus.png: 2.6ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load button-nofocus.png: 0.1ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load radio-button-focus.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load radio-button-nofocus.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load top-bar-eject-focus.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load top-bar-eject-nofocus.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load top-bar-power-focus.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load top-bar-power-nofocus.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: SECTION:LoadDLL(special://xbmc/system/ImageLib-i486-linux.so)
15:44:43 T:3079415696 M:2523365376   DEBUG: Loading: /usr/share/xbmc/system/ImageLib-i486-linux.so
15:44:43 T:3079415696 M:2523365376    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-background.png Error: (2)
15:44:43 T:3079415696 M:2523365376   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-background.png
15:44:43 T:3079415696 M:2523365376   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-background.png
15:44:43 T:3079415696 M:2523365376    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-background.png Error: (2)
15:44:43 T:3079415696 M:2523365376   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-background.png
15:44:43 T:3079415696 M:2523365376   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-background.png
15:44:43 T:3079415696 M:2523365376    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-background.png Error: (2)
15:44:43 T:3079415696 M:2523365376   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-background.png
15:44:43 T:3079415696 M:2523365376   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-background.png
15:44:43 T:3079415696 M:2523365376    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-background.png Error: (2)
15:44:43 T:3079415696 M:2523365376   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-background.png
15:44:43 T:3079415696 M:2523365376   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-background.png
15:44:43 T:3079415696 M:2523365376    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-home-focus.png Error: (2)
15:44:43 T:3079415696 M:2523365376   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-home-focus.png
15:44:43 T:3079415696 M:2523365376   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-home-focus.png
15:44:43 T:3079415696 M:2523365376    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-home-nofocus.png Error: (2)
15:44:43 T:3079415696 M:2523365376   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-home-nofocus.png
15:44:43 T:3079415696 M:2523365376   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-home-nofocus.png
15:44:43 T:3079415696 M:2523365376    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:44:43 T:3079415696 M:2523365376   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:44:43 T:3079415696 M:2523365376   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:44:43 T:3079415696 M:2523365376    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:44:43 T:3079415696 M:2523365376   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:44:43 T:3079415696 M:2523365376   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:44:43 T:3079415696 M:2523365376   DEBUG: Alloc resources: 36.90ms (27.37 ms skin load, 0.40 ms preload)
15:44:43 T:3079415696 M:2523365376   DEBUG: CGUIMediaWindow::GetDirectory (myth://192.168.1.2/channels/)
15:44:43 T:3079415696 M:2523365376   DEBUG:   ParentPath = [myth://192.168.1.2/channels/]
15:44:43 T:3079415696 M:2523365376   DEBUG: SECTION:LoadDLL(xbmc.so)
15:44:43 T:3079415696 M:2523365376   DEBUG: Loading Internal Library
15:44:43 T:3079415696 M:2523365376   DEBUG: Sort, sorting took 0 millis
15:44:43 T:2959080304 M:2523365376   DEBUG: Running thread 2959080304
15:44:43 T:2959080304 M:2523365376   DEBUG: thread start, auto delete: 0
15:44:43 T:2959080304 M:2523365376   DEBUG: Thread 2959080304 terminating
15:44:43 T:3079415696 M:2523365376    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/backgrounds/default-background.jpg Error: (2)
15:44:43 T:3079415696 M:2523365376   ERROR: PICTURE: Error loading image special://skin/images/backgrounds/default-background.jpg
15:44:43 T:3079415696 M:2523365376   ERROR: Texture manager unable to load file: special://skin/images/backgrounds/default-background.jpg
15:44:43 T:3079415696 M:2523365376   DEBUG: Load listview-background-dim.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load button-list-focus.png: 0.1ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load defaultFolderBack.png.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523365376   DEBUG: Load bottom-bar-top.png: 0.0ms (bundled)
15:44:43 T:3079415696 M:2523111424   DEBUG: Load bottom-bar-background.png: 2.3ms (bundled)
15:44:43 T:3079415696 M:2521841664   DEBUG: Load bottom-bar-overlay.png: 9.7ms (bundled)
15:44:43 T:3079415696 M:2521841664    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-background.png Error: (2)
15:44:43 T:3079415696 M:2521841664   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-background.png
15:44:43 T:3079415696 M:2521841664   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-background.png
15:44:43 T:3079415696 M:2521841664    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/top-bar-status-background.png Error: (2)
15:44:43 T:3079415696 M:2521841664   ERROR: PICTURE: Error loading image special://skin/images/skin/top-bar-status-background.png
15:44:43 T:3079415696 M:2521841664   ERROR: Texture manager unable to load file: special://skin/images/skin/top-bar-status-background.png
15:44:43 T:3079415696 M:2521841664    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-separator-nofocus.png Error: (2)
15:44:43 T:3079415696 M:2521841664   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-separator-nofocus.png
15:44:43 T:3079415696 M:2521841664   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-separator-nofocus.png
15:44:43 T:3079415696 M:2521841664    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-separator-nofocus.png Error: (2)
15:44:43 T:3079415696 M:2521841664   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-separator-nofocus.png
15:44:43 T:3079415696 M:2521841664   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-separator-nofocus.png
15:44:43 T:3079415696 M:2521841664    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-separator-nofocus.png Error: (2)
15:44:43 T:3079415696 M:2521841664   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-separator-nofocus.png
15:44:43 T:3079415696 M:2521841664   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-separator-nofocus.png
15:44:43 T:3079415696 M:2521841664   DEBUG: Load control-area-background.png: 0.3ms (bundled)
15:44:43 T:3079415696 M:2521841664   DEBUG: Load menu-bar-separator.png: 0.0ms (bundled)
15:44:44 T:3079415696 M:2521862144   DEBUG: SDLKeyboard: scancode: 116, sym: 274, unicode: 0, modifier: 0
15:44:44 T:3079415696 M:2521862144   DEBUG: OnKey: 61480 pressed, action is 4
15:44:45 T:3079415696 M:2521853952   DEBUG: SDLKeyboard: scancode: 111, sym: 273, unicode: 0, modifier: 0
15:44:45 T:3079415696 M:2521853952   DEBUG: OnKey: 61478 pressed, action is 3
15:44:45 T:3079415696 M:2521853952   DEBUG: SDLKeyboard: scancode: 36, sym: 13, unicode: 13, modifier: 0
15:44:45 T:3079415696 M:2521853952   DEBUG: OnKey: 61453 pressed, action is 7
15:44:45 T:3079415696 M:2521853952   DEBUG: CGUIMediaWindow::GetDirectory (myth://192.168.1.2/)
15:44:45 T:3079415696 M:2521853952   DEBUG:   ParentPath = []
15:44:45 T:3079415696 M:2521853952   DEBUG: Sort, sorting took 0 millis
15:44:45 T:2959080304 M:2521853952   DEBUG: Running thread 2959080304
15:44:45 T:2959080304 M:2521853952   DEBUG: thread start, auto delete: 0
15:44:45 T:3079415696 M:2521853952   DEBUG: Load button-list-nofocus.png: 0.1ms (bundled)
15:44:45 T:3079415696 M:2521853952   DEBUG: Load defaultFolderBack.png.png: 0.1ms (bundled)
15:44:45 T:3079415696 M:2521853952   DEBUG: Load defaultFolder.png.png: 0.0ms (bundled)
15:44:45 T:3079415696 M:2521853952   DEBUG: Load button-list-focus.png: 0.1ms (bundled)
15:44:45 T:2959080304 M:2521853952   DEBUG: Thread 2959080304 terminating
15:44:46 T:3079415696 M:2521853952   DEBUG: SDLKeyboard: scancode: 111, sym: 273, unicode: 0, modifier: 0
15:44:46 T:3079415696 M:2521853952   DEBUG: OnKey: 61478 pressed, action is 3
15:44:46 T:3079415696 M:2521853952   DEBUG: SDLKeyboard: scancode: 111, sym: 273, unicode: 0, modifier: 0
15:44:46 T:3079415696 M:2521853952   DEBUG: OnKey: 61478 pressed, action is 3
15:44:46 T:3079415696 M:2521853952   DEBUG: SDLKeyboard: scancode: 111, sym: 273, unicode: 0, modifier: 0
15:44:46 T:3079415696 M:2521853952   DEBUG: OnKey: 61478 pressed, action is 3
15:44:46 T:3079415696 M:2521853952   DEBUG: SDLKeyboard: scancode: 116, sym: 274, unicode: 0, modifier: 0
15:44:46 T:3079415696 M:2521853952   DEBUG: OnKey: 61480 pressed, action is 4
15:44:47 T:3079415696 M:2521858048   DEBUG: SDLKeyboard: scancode: 116, sym: 274, unicode: 0, modifier: 0
15:44:47 T:3079415696 M:2521858048   DEBUG: OnKey: 61480 pressed, action is 4
15:44:47 T:3079415696 M:2521858048   DEBUG: SDLKeyboard: scancode: 36, sym: 13, unicode: 13, modifier: 0
15:44:47 T:3079415696 M:2521858048   DEBUG: OnKey: 61453 pressed, action is 7
15:44:47 T:3079415696 M:2521858048   DEBUG: Clearing cached fileitems [myth://192.168.1.2/guide/]
15:44:47 T:3079415696 M:2521858048   DEBUG: CGUIMediaWindow::GetDirectory (myth://192.168.1.2/guide/)
15:44:47 T:3079415696 M:2521858048   DEBUG:   ParentPath = [myth://192.168.1.2/]
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '5 - WNYW_HD' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '11 - WPIX_HD' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '11 - E1_10  ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '9 - D1_1  W' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '47 - D1_2  W' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '4 - WNBC_HD' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '7 - WABC_HD' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '4 - WNBC_We' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '4 - WNBC_4.' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '7 - D2_15  ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '7 - WABC_SD' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '2 - WCBS_HD' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '13 - WNET_HD' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '13 - PBS_KID' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '13 - WNET_WR' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '128 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '129 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '130 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '131 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '132 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '133 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '134 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '135 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '136 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '137 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '138 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '144 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '145 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '146 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '147 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '148 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '149 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '150 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '151 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '152 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '153 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '154 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '155 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '156 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '157 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '158 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '450 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '468 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '470 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '10 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '13 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '14 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '15 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '43 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '2 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '1 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '3 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '4 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '5 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '6 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '7 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '8 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '11 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '9 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '12 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '16 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '17 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '18 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '19 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '20 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '355 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '336 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '338 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '339 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '21 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '115 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '502 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '504 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '505 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '507 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '509 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '511 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '513 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '541 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '547 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '568 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '205 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '22 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '23 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '24 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '25 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '26 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '27 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '28 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '29 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: GetGuide - Channel '30 - ' Icon ''
15:44:47 T:3079415696 M:2521858048   DEBUG: Sort, sorting took 0 millis
15:44:47 T:2959080304 M:2521858048   DEBUG: Running thread 2959080304
15:44:47 T:2959080304 M:2521858048   DEBUG: thread start, auto delete: 0
15:44:47 T:2948594544 M:2521858048   DEBUG: Running thread 2948594544
15:44:47 T:2948594544 M:2521858048   DEBUG: thread start, auto delete: 0
15:44:47 T:2931809136 M:2521858048   DEBUG: Running thread 2931809136
15:44:47 T:2931809136 M:2521858048   DEBUG: thread start, auto delete: 0
15:44:47 T:2923416432 M:2521858048   DEBUG: Running thread 2923416432
15:44:47 T:2923416432 M:2521858048   DEBUG: thread start, auto delete: 0
15:44:47 T:2940201840 M:2521858048   DEBUG: Running thread 2940201840
15:44:47 T:2940201840 M:2521858048   DEBUG: thread start, auto delete: 0
15:44:47 T:3079415696 M:2521858048   DEBUG: Load button-list-nofocus.png: 0.1ms (bundled)
15:44:47 T:3079415696 M:2521858048   DEBUG: Load defaultFolder.png.png: 0.1ms (bundled)
15:44:47 T:3079415696 M:2521858048   DEBUG: Load button-list-focus.png: 0.1ms (bundled)
15:44:47 T:3079415696 M:2521858048   DEBUG: Load defaultFolderBack.png.png: 0.0ms (bundled)
15:44:47 T:2923416432 M:2521858048   DEBUG: Thread 2923416432 terminating
15:44:47 T:2948594544 M:2521858048   DEBUG: Thread 2948594544 terminating
15:44:47 T:2940201840 M:2521858048   DEBUG: Thread 2940201840 terminating
15:44:47 T:2931809136 M:2521858048   DEBUG: Thread 2931809136 terminating
15:44:47 T:2959080304 M:2521858048   DEBUG: Thread 2959080304 terminating
15:44:48 T:3079415696 M:2521866240   DEBUG: SDLKeyboard: scancode: 36, sym: 13, unicode: 13, modifier: 0
15:44:48 T:3079415696 M:2521866240   DEBUG: OnKey: 61453 pressed, action is 7
15:44:48 T:3079415696 M:2521866240   DEBUG: CGUIMediaWindow::GetDirectory (myth://192.168.1.2/)
15:44:48 T:3079415696 M:2521866240   DEBUG:   ParentPath = []
15:44:48 T:3079415696 M:2521866240   DEBUG: Sort, sorting took 0 millis
15:44:48 T:2923416432 M:2521866240   DEBUG: Running thread 2923416432
15:44:48 T:2923416432 M:2521866240   DEBUG: thread start, auto delete: 0
15:44:48 T:3079415696 M:2521866240   DEBUG: Load button-list-nofocus.png: 0.1ms (bundled)
15:44:48 T:3079415696 M:2521866240   DEBUG: Load defaultFolderBack.png.png: 0.1ms (bundled)
15:44:48 T:3079415696 M:2521866240   DEBUG: Load defaultFolder.png.png: 0.1ms (bundled)
15:44:48 T:3079415696 M:2521866240   DEBUG: Load button-list-focus.png: 0.1ms (bundled)
15:44:48 T:2923416432 M:2521866240   DEBUG: Thread 2923416432 terminating
15:44:53 T:3079415696 M:2521866240    INFO: CheckIdle - Closing idle connection to mythtv backend 192.168.1.2
15:45:13 T:3079415696 M:2521866240   DEBUG: SECTION:UnloadDelayed(DLL: special://xbmc/system/ImageLib-i486-linux.so)
15:45:13 T:3079415696 M:2521866240   DEBUG: Unloading: ImageLib-i486-linux.so
15:45:23 T:3079415696 M:2521866240   DEBUG: SECTION:UnloadDelayed(DLL: xbmc.so)
15:45:23 T:3079415696 M:2521866240   DEBUG: Unloading: xbmc.so
15:47:24 T:3079415696 M:2521866240   DEBUG: Load button-list-alt-focus.png: 0.1ms (bundled)
15:47:24 T:3079415696 M:2521866240   DEBUG: SECTION:LoadDLL(special://xbmc/system/ImageLib-i486-linux.so)
15:47:24 T:3079415696 M:2521866240   DEBUG: Loading: /usr/share/xbmc/system/ImageLib-i486-linux.so
15:47:24 T:3079415696 M:2521866240    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-background.png Error: (2)
15:47:24 T:3079415696 M:2521866240   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-background.png
15:47:24 T:3079415696 M:2521866240   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-background.png
15:47:34 T:3079415696 M:2517139456    INFO:   msg: PICTURE::LoadImage: Unable to open image: special://skin/images/skin/breadcrumb-background.png Error: (2)
15:47:34 T:3079415696 M:2517139456   ERROR: PICTURE: Error loading image special://skin/images/skin/breadcrumb-background.png
15:47:34 T:3079415696 M:2517139456   ERROR: Texture manager unable to load file: special://skin/images/skin/breadcrumb-background.png
15:48:05 T:3079415696 M:2521128960   DEBUG: SECTION:UnloadDelayed(DLL: special://xbmc/system/ImageLib-i486-linux.so)
15:48:05 T:3079415696 M:2521128960   DEBUG: Unloading: ImageLib-i486-linux.so


```

---

