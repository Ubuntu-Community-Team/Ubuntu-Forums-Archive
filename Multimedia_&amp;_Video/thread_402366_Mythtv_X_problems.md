---
title: "Mythtv X problems"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by ebike on 2007-04-05
Hi All,

I have set up Mythtv on a new Nvidia based box and am having trouble with the X setup. Most things run fine, but I am getting pre-buffer pauses with Mythtv ... in particular "NVP: prebuffering pause" The errors as reported below are BadDevice errors, though what device is not reported. Mythtv also uses 30% cpu, where it used to use 17% ...

Mythfrontend log is:

> X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-04-06 08:30:45.104 Using runtime prefix = /usr
2007-04-06 08:30:45.115 Gnome-Screensaver support enabled
2007-04-06 08:30:45.116 DPMS is disabled.
2007-04-06 08:30:45.156 New DB connection, total: 1
2007-04-06 08:30:45.327 Connected to database 'mythconverg' at host: 192.168.0.3
2007-04-06 08:30:45.329 Total desktop dim: 1024x768, with 1 screen[s].
2007-04-06 08:30:45.334 Using screen 0, 1024x768 at 0,0
2007-04-06 08:30:45.351 Current Schema Version: 1160
2007-04-06 08:30:45.352 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-06 08:30:45.352 Enabled verbose msgs:  important general
2007-04-06 08:30:45.838 Total desktop dim: 1024x768, with 1 screen[s].
2007-04-06 08:30:45.840 Using screen 0, 1024x768 at 0,0
2007-04-06 08:30:45.842 Switching to square mode (Retro)
2007-04-06 08:30:45.875 Using the OpenGL painter
2007-04-06 08:30:46.321 Joystick disabled.
2007-04-06 08:30:46.364 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-06 08:30:46.893 Registering Internal as a media playback plugin.
2007-04-06 08:30:46.954 Registering MythDVD DVD Media Handler as a media handler ext()
2007-04-06 08:30:46.955 Registering MythDVD VCD Media Handler as a media handler ext()
2007-04-06 08:30:46.996 Registering MythGallery Media Handler 1/2 as a media handler ext()
2007-04-06 08:30:46.996 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
2007-04-06 08:30:47.112 Using NV NPOT texture extension
adding: 0,0,0 -- CF  CardReader
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2007-04-06 08:30:50.243 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-04-06 08:30:50.244 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2007-04-06 08:30:50.335 New DB connection, total: 2
2007-04-06 08:30:50.508 Connected to database 'mythconverg' at host: 192.168.0.3
Failed to find network interface eth1
SIP listening on IP Address :5060 NAT address 58.28.128.129
SIP: Cannot transmit SIP message to 202.180.81.49
Destroying SipFsm object
2007-04-06 08:31:56.966 Connecting to backend server: 192.168.0.3:6543 (try 1 of 5)
2007-04-06 08:31:56.968 Using protocol version 31
2007-04-06 08:31:56.972 TV: Attempting to change from None to WatchingLiveTV
2007-04-06 08:31:56.977 Using protocol version 31
2007-04-06 08:31:58.225 AFD: Opened codec 0x8d134a0, id(MPEG2VIDEO) type(Video)
2007-04-06 08:31:58.242 AFD: Opened codec 0x8d137f0, id(MP2) type(Audio)
2007-04-06 08:31:58.247 Opening OSS audio device '/dev/dsp'.
2007-04-06 08:31:58.289 VideoOutputXv: XvMCTex: Init failed
2007-04-06 08:31:58.291 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  140
  Minor opcode:  14
  Resource id:  0x17d
2007-04-06 08:31:58.742 The realtime priority setting is not enabled.
2007-04-06 08:31:58.742 TV: Changing from None to WatchingLiveTV
2007-04-06 08:31:58.862 Video timing method: USleep with busy wait
2007-04-06 08:32:07.987 NVP: prebuffering pause
2007-04-06 08:32:08.049 New DB connection, total: 3
2007-04-06 08:32:08.220 Connected to database 'mythconverg' at host: 192.168.0.3
2007-04-06 08:32:58.307 NVP: Prebuffer wait timed out 10 times.
2007-04-06 08:33:04.682 NVP: prebuffering pause
2007-04-06 08:33:34.831 NVP: prebuffering pause


The relevant section of xorg.conf is:

> Section "Monitor"
    Identifier   "Generic Monitor"
    ModelName    "HTC001e"
    HorizSync    31.47 - 79.98
    VertRefresh  59.94 - 75.03
    #Option         "DPMS"

    DisplaySize 928 522     # in mm
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
    Driver         "nvidia"
    Option         "NoLogo"
    Option         "NVAGP" "2"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
       Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection



glxinfo reports:

> 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 MX Integrated GPU/AGP/SSE/3DNOW!
OpenGL version string: 1.5.6 NVIDIA 87.76
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_pixel_buffer_object,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects,
    GL_ARB_shading_language_100, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
  GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shared_texture_palette,
    GL_EXT_stencil_wrap, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fence,
    GL_NV_fog_distance, GL_NV_gpu_program_parameters,
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil,
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_register_combiners,
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4,
    GL_NV_texture_rectangle, GL_NV_vertex_array_range,
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_SGIS_generate_mipmap, GL_SGIS_multitexture, GL_SGIS_texture_lod,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x33 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x39 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3a 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3b 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3d 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xa0 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None



My nvidia driver is nvidia-kernel-1.0.8776

Any help much appreciated.

PS: Let me know if you want any more data...

---

### Post by scottishnarn on 2007-04-06
Try running mythfrontend with nice -1 i.e. ```
nice -1 mythfrontend
```It's counter intuitive and it shouldn't work, but it did for me.

---

### Post by ebike on 2007-04-08
You are right, it shoudn't work, and didn't for me ....

---

