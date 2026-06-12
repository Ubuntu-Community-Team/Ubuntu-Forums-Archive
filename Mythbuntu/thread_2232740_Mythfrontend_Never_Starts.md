---
title: "Mythfrontend Never Starts"
date: 2014-07-03
forum: Mythbuntu
---

### Post by mattlach on 2014-07-03
Hey all,

Brand new 14.04 nstall on an AMD CPU and radeon graphics, running mesa drivers.  8gb ram.

Backend is up and running properly on my server.  I already have a main HTCP running the XBMC plugin that works perfectly.  (well, there are a few minor bugs, but nothing major)

Just threw together a new rig from spare parts for a bedroom TV.  Did a frontend only install.  System boots up fine.  First time config, including database and login information was successful.

Problem is, mythfrontend never starts.

PS shows that it is running, but nothing ever shows up on screen:

```

$ ps -A |grep -i myth
 1998 ?        00:00:00 mythfrontend
 2007 ?        00:00:00 mythfrontend.re

```

If i instead run mythfrontend from the terminal, this is all I see:

```

$ mythfrontend
2014-07-03 22:03:40.100537 I  Setup Interrupt handler
2014-07-03 22:03:40.100601 I  Setup Terminated handler
2014-07-03 22:03:40.100623 I  Setup Segmentation fault handler
2014-07-03 22:03:40.100647 I  Setup Aborted handler
2014-07-03 22:03:40.100738 I  Setup Bus error handler
2014-07-03 22:03:40.100768 I  Setup Floating point exception handler
2014-07-03 22:03:40.100792 I  Setup Illegal instruction handler
2014-07-03 22:03:40.100831 I  Setup Real-time signal 0 handler
2014-07-03 22:03:40.100869 I  Setup User defined signal 1 handler
2014-07-03 22:03:40.100890 I  Setup User defined signal 2 handler
2014-07-03 22:03:40.101143 C  mythfrontend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
2014-07-03 22:03:40.101159 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2014-07-03 22:03:40.101172 N  Enabled verbose msgs:  general
2014-07-03 22:03:40.101203 N  Setting Log Level to LOG_INFO
2014-07-03 22:03:40.113214 N  Using runtime prefix = /usr
2014-07-03 22:03:40.113386 I  Added logging to the console
2014-07-03 22:03:40.113307 N  Using configuration directory = /home/myth/.mythtv
2014-07-03 22:03:40.113786 I  Assumed character encoding: en_US.UTF-8
2014-07-03 22:03:40.115257 N  Empty LocalHostName.
2014-07-03 22:03:40.115298 I  Using localhost value of mythbuntu-bedroom
2014-07-03 22:03:40.115437 I  Testing network connectivity to 'xxx.xxx.xxx.xxx'
2014-07-03 22:03:40.118135 I  Starting process manager
2014-07-03 22:03:40.121929 I  Starting IO manager (write)
2014-07-03 22:03:40.122210 I  Starting IO manager (read)
2014-07-03 22:03:40.122412 I  Starting process signal handler
2014-07-03 22:03:40.220088 I  New Client:  (#1)
2014-07-03 22:03:40.220227 I  Added syslogging

```

Nothing ever happens after this, and nothing pops up on screen.

Can anyone suggest what I might do to troubleshoot?

Thanks,
Matt

---

### Post by blm-ubunet on 2014-07-04
If this is a mythbuntu version of mythtv, then IIRC they wrap the FE exe in a script. try:

```
mythfrontend.real -O ThemePainter=qt -O Theme=MythCenter -v all --loglevel=debug
```

Problem could be version mismatch (RFE-MBE), missing themes or broken openGL.

---

### Post by mattlach on 2014-07-04
> **blm-ubunet said:**
> If this is a mythbuntu version of mythtv, then IIRC they wrap the FE exe in a script. try:

```
mythfrontend.real -O ThemePainter=qt -O Theme=MythCenter -v all --loglevel=debug
```

Problem could be version mismatch (RFE-MBE), missing themes or broken openGL.

Thank you for your help.

passing the options you suggest above doesn't fix the problem, but it does give me some more detailed console log output.   Unfortunately I don't see anything in here that suggests what the problem is.  Do you?

```

$ mythfrontend.real -O ThemePainter=qt -O Theme=MythCenter -v all --loglevel=debug
2014-07-04 14:27:28.930042 I  Setup Interrupt handler
2014-07-04 14:27:28.930105 I  Setup Terminated handler
2014-07-04 14:27:28.930123 I  Setup Segmentation fault handler
2014-07-04 14:27:28.930146 I  Setup Aborted handler
2014-07-04 14:27:28.930169 I  Setup Bus error handler
2014-07-04 14:27:28.930187 I  Setup Floating point exception handler
2014-07-04 14:27:28.930210 I  Setup Illegal instruction handler
2014-07-04 14:27:28.930232 I  Setup Real-time signal 0 handler
2014-07-04 14:27:28.930258 I  Setup User defined signal 1 handler
2014-07-04 14:27:28.930276 I  Setup User defined signal 2 handler
2014-07-04 14:27:28.930523 C  mythfrontend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
2014-07-04 14:27:28.930544 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2014-07-04 14:27:28.930553 N  Enabled verbose msgs: all
2014-07-04 14:27:28.930586 N  Setting Log Level to LOG_DEBUG
2014-07-04 14:27:28.944259 N  Using runtime prefix = /usr
2014-07-04 14:27:28.944312 N  Using configuration directory = /home/myth/.mythtv
2014-07-04 14:27:28.944501 I  Assumed character encoding: en_US.UTF-8
2014-07-04 14:27:28.944717 I  Added logging to the console
2014-07-04 14:27:28.945602 E  (old)Settings::ReadSettings(settings.txt) - No such file settings.txt
2014-07-04 14:27:28.946078 N  Empty LocalHostName.
2014-07-04 14:27:28.946128 I  Using localhost value of mythbuntu-bedroom
2014-07-04 14:27:28.946164 I  Clearing Settings Cache.
2014-07-04 14:27:28.946248 I  DefaultUPnP() - No default UPnP backend
2014-07-04 14:27:28.946301 I  Testing network connectivity to 'xxx.xxx.xxx.xxx'
2014-07-04 14:27:28.947780 I  Starting process manager
2014-07-04 14:27:28.947890 I  Starting process signal handler
2014-07-04 14:27:28.948686 D  Launching: ping -t 3 -c 1  xxx.xxx.xxx.xxx  >/dev/null 2>&1
2014-07-04 14:27:28.951392 I  Starting IO manager (read)
2014-07-04 14:27:28.951842 I  Starting IO manager (write)
2014-07-04 14:27:28.952388 I  Managed child (PID: 2836) has started! * command=ping -t 3 -c 1  xxx.xxx.xxx.xxx  >/dev/null 2>&1, timeout=0
2014-07-04 14:27:28.952481 I  (0x2456200)::IncrRef() -> 2
2014-07-04 14:27:29.048475 I  Managed child (PID: 2836) has exited! command=ping -t 3 -c 1  xxx.xxx.xxx.xxx  >/dev/null 2>&1, status=0, result=0
2014-07-04 14:27:29.048712 I  (0x2456200)::DecrRef() -> 1
2014-07-04 14:27:29.048869 I  (0x2456200)::DecrRef() -> 0
2014-07-04 14:27:29.049088 I  Clearing Settings Cache.
2014-07-04 14:27:29.052065 I  New Client:  (#1)
2014-07-04 14:27:29.065570 I  Database connection created: DBManager0
2014-07-04 14:27:29.065632 I  New DB connection, total: 1

```

Basic OpenGL troubleshooting using glxgears seems to work fine, with results rendered on screen.

```

$ glxgears -info
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
GL_RENDERER   = Gallium 0.4 on AMD PALM
GL_VERSION    = 3.0 Mesa 10.1.3
GL_VENDOR     = X.Org
GL_EXTENSIONS = GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_framebuffer_sRGB GL_ARB_multitexture GL_EXT_framebuffer_sRGB GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_compression_s3tc GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_depth_clamp GL_NV_fog_distance GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_NV_primitive_restart GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_color_buffer_float GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_ATI_texture_compression_3dc GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_mirror_clamp GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_ATI_texture_mirror_once GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_texture_array GL_EXT_texture_compression_latc GL_EXT_texture_integer GL_EXT_texture_sRGB_decode GL_EXT_timer_query GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_AMD_conservative_depth GL_AMD_draw_buffers_blend GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_stencil_export GL_ARB_ES2_compatibility GL_ARB_blend_func_extended GL_ARB_debug_output GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_stencil_export GL_ARB_shader_texture_lod GL_ARB_texture_cube_map_array GL_ARB_texture_multisample GL_ARB_texture_rgb10_a2ui GL_ARB_uniform_buffer_object GL_ARB_vertex_type_2_10_10_10_rev GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_NV_texture_barrier GL_ARB_get_program_binary GL_ARB_robustness GL_ARB_shader_bit_encoding GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_NV_vdpau_interop GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_base_instance GL_ARB_conservative_depth GL_ARB_internalformat_query GL_ARB_map_buffer_alignment GL_ARB_shading_language_420pack GL_ARB_shading_language_packing GL_ARB_texture_storage GL_ARB_transform_feedback_instanced GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_transform_feedback GL_AMD_shader_trinary_minmax GL_ARB_clear_buffer_object GL_ARB_invalidate_subdata GL_ARB_texture_storage_multisample GL_ARB_vertex_attrib_binding GL_KHR_debug GL_ARB_texture_mirror_clamp_to_edge GL_ARB_vertex_type_10f_11f_11f_rev 
```


What is this RFE-MBE version mismatch you are talking about?

I would be surprised if there are any version mismatches or missing themes.   This is a clean front end only install of mythbuntu 14.04 straight off of the ISO on the webpage.   The backend is a backend only install from the same ISO I did a couple of weeks ago.   Both are updated with all current updates.

Any further thoughts?

Thank you very much for your help!

--Matt

---

### Post by mattlach on 2014-07-04
Hmm,

Could this explain the problem?

```

$ vdpauinfo
display: :0.0   screen: 0
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
Error creating VDPAU device: 1

```

Will the frontend fail to load without vdpau?   I would have thought it would load fine but be slow when playing content if vdpau were acting up.

Thanks,
Matt

---

### Post by mattlach on 2014-07-04
I was able to enable vdpau based on some information towards the end of [this thread on phoronix](http://www.phoronix.com/forums/showthread.php?93947-Getting-VDPAU-working-through-14-04).

```

$ vdpauinfo
display: :0.0   screen: 0
API version: 1
Information string: G3DVL VDPAU Driver Shared Library version 1.0

Video surface:

name   width height types
-------------------------------------------
420    16384 16384  NV12 YV12 
422    16384 16384  UYVY YUYV 
444    16384 16384  Y8U8V8A8 V8U8Y8A8 

Decoder capabilities:

name               level macbs width height
-------------------------------------------
MPEG1                 0  9216  2048  1152
MPEG2_SIMPLE          3  9216  2048  1152
MPEG2_MAIN            3  9216  2048  1152
H264_BASELINE        41  9216  2048  1152
H264_MAIN            41  9216  2048  1152
H264_HIGH            41  9216  2048  1152
VC1_ADVANCED          4  9216  2048  1152
MPEG4_PART2_SP        3  9216  2048  1152
MPEG4_PART2_ASP       5  9216  2048  1152

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8         16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 
R8G8B8A8         16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 
R10G10B10A2      16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 
B10G10R10A2      16384 16384    y  NV12 YV12 UYVY YUYV Y8U8V8A8 V8U8Y8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8         16384 16384
R8G8B8A8         16384 16384
R10G10B10A2      16384 16384
B10G10R10A2      16384 16384
A8               16384 16384

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     -
INVERSE_TELECINE                 -
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         -
HIGH QUALITY SCALING - L1        -
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y        48     2048
VIDEO_SURFACE_HEIGHT             y        48     1152
CHROMA_TYPE                      y  
LAYERS                           y         0        4

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  
```

Looks like it is working, but other than running this, I'm not quite sure how to test it inside X.

mythfrontend still fails to start.

Any ideas anyone might have would be greatly appreciated!

--Matt

---

### Post by blm-ubunet on 2014-07-04
The frontends find all backends using UPnP request protocol.
DefaultUPnP() - No default UPnP backend

The MBE can not be found if:
- UPnP is blocked by firewall
- UPnP ports are blocked/disabled
- MBE using linklocal IP (127.0.0.1)

Try running this (with the actual MBE IP adr):
ping -t 3 -c 1  xxx.xxx.xxx.xxx

Do you have a config.xml file in /home/myth/.mythtv/ ?

To test VDPAU (outside any big media player) you would need to build "qvdpautest".
I seem to recall problem compiling this a couple weeks ago (on new 14.04 install).

---

### Post by mattlach on 2014-07-04
> **blm-ubunet said:**
> The frontends find all backends using UPnP request protocol.
DefaultUPnP() - No default UPnP backend

The MBE can not be found if:
- UPnP is blocked by firewall
- UPnP ports are blocked/disabled
- MBE using linklocal IP (127.0.0.1)

Try running this (with the actual MBE IP adr):
ping -t 3 -c 1  xxx.xxx.xxx.xxx

Do you have a config.xml file in /home/myth/.mythtv/ ?

To test VDPAU (outside any big media player) you would need to build "qvdpautest".
I seem to recall problem compiling this a couple weeks ago (on new 14.04 install).

The system can definitely ping my backend.   That isn't the issue at all.

I couldn't get the environment right to compile qvdpautest, but I have confirmed that it is working via "mplayer -vo vdpau"

The config file is definitely int he correct location, and contains all the correct IP, port and password information for the backend.

It appears to be a local machine issue.   For some reason the front end just won't display on screen.

I did another clean install, still nothing...

Any further suggestions much appreciated.

---

### Post by blm-ubunet on 2014-07-04
"mplayer -vo vdpau" only tests VDPAU video overlay & not decode, need to add "-vc ffh264vdpau" etc to be sure it uses h/w decode (obv. for h264/AVC).

Your (mythfrontend) stdout/err log stops dead at the point the FE connects to dB server (mysql) & accesses mythconverg.
I would guess that mysql server is only listening on link-local IP.
When mysql listens only on link-local then only local BE & FE will work.

---

### Post by mattlach on 2014-07-05
> **blm-ubunet said:**
> "mplayer -vo vdpau" only tests VDPAU video overlay & not decode, need to add "-vc ffh264vdpau" etc to be sure it uses h/w decode (obv. for h264/AVC).

Your (mythfrontend) stdout/err log stops dead at the point the FE connects to dB server (mysql) & accesses mythconverg.
I would guess that mysql server is only listening on link-local IP.
When mysql listens only on link-local then only local BE & FE will work.

So you think it's a backend issue?

I already have another independent frontend that is working properly though.

---

### Post by blm-ubunet on 2014-07-05
If that other independent mythtv FE is on a different PC ...then that theory is ruined..

IPv6 ?

I'm not sure why the remote FE log file stops with no clues (except FE crashed).
Are there any clues in the master BE log at the same time?

---

### Post by mattlach on 2014-07-05
> **blm-ubunet said:**
> If that other independent mythtv FE is on a different PC ...then that theory is ruined..

IPv6 ?

I'm not sure why the remote FE log file stops with no clues (except FE crashed).
Are there any clues in the master BE log at the same time?

Yeah,

My setup is as follows:

1 standalone backend running as a guest on my VMWare ESXi server

1 Standalone frontend on my Windows 8.1 HTPC, running the MythTV plugin in XBMC

2 Desktop linux installs (Linux Mint, one laptop, one Desktop) which occasionally load up the mythtv frontend to schedule recordings or play something)

1 Mythbuntu frontend install in bedroom that just isn't working.


Do you have any suggestions which log files to look at or what to search for?

I just recursively grepped the entirety of /var/log on my backend looking for the frontends IP or hostname, and came up with nothing.

---

### Post by mattlach on 2014-07-05
Alright, I still have no idea why it wasn't working, but on a whim, I deleted the entire .mythtv folder in my user home folder, and viola, everything suddenly works.

There must be something wrong with how the original config files were created on install for my machine, and letting mythtv recreate them on their own just magically fixed everything.

Thanks for all the help!

--Matt

---

