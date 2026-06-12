---
title: "my system isnt exactly &quot;smooth&quot; and I have no clue what to do..."
date: 2008-06-15
forum: Multimedia Software
---

### Post by Majin_Buu on 2008-06-15
:confused:I'm quite new to the whole linux universe. I've managed to install ubuntu with kde/compiz-fusion/etc but my system doesnt exactly run "smooth" during browsing, moving windows etc.

Kinda hard to explain but every action lags somewhat, and when ever I scroll in opera/konqueror etc I can see a slight delay causing a frame to move slowly like theres no anti aliasaing?

This is especially noticeable when im running youtube, the video looks its running the movie with slow-motion frames.

Im using envy-nvidia drivers.

Anyone know what I can do to make the system run smoothly?

My system specs:

amd athlon 64 4400+
2GB RAM
8600GT 256 GDR3 Nvidia

:confused: :confused:

---

### Post by rnrover on 2008-06-15
> **Majin_Buu said:**
> :confused:I'm quite new to the whole linux universe. I've managed to install ubuntu with kde/compiz-fusion/etc but my system doesnt exactly run "smooth" during browsing, moving windows etc.

Kinda hard to explain but every action lags somewhat, and when ever I scroll in opera/konqueror etc I can see a slight delay causing a frame to move slowly like theres no anti aliasaing?

This is especially noticeable when im running youtube, the video looks its running the movie with slow-motion frames.

Im using envy-nvidia drivers.

Anyone know what I can do to make the system run smoothly?

My system specs:

amd athlon 64 4400+
2GB RAM
8600GT 256 GDR3 Nvidia

:confused: :confused:

Keep reading.  I am also a newbie, but I have spent several weeks tweaking my system.  I had your same issue a while back and found out that I had installed the 386 version instead of the 64 bit version. After I reinstalled, it all went smooth.  With envy it installed the first driver in the list instead of the correct one.

Good luck.  When you get it all working it is fantastic.

---

### Post by prshah on 2008-06-15
> **Majin_Buu said:**
> my system doesnt exactly run "smooth" during browsing, moving windows etc.

Kinda hard to explain but every action lags somewhat, and when ever I scroll in opera/konqueror etc I can see a slight delay causing a frame to move slowly like theres no anti aliasaing?


Open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here.
 ```

glxinfo | grep -i direct

```

This will give us information about whether or not the graphics is setup correctly.

---

### Post by Majin_Buu on 2008-06-15
> **prshah said:**
> Open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here.
 ```

glxinfo | grep -i direct

```

This will give us information about whether or not the graphics is setup correctly.

```
glxinfo | grep -i direct
direct rendering: Yes
```

Thanks for responding, here's some additional information regarding my gpu:



```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer,
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap,
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer,
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8600 GT/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 173.14.05
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers,
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow,
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite,
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,
    GL_EXT_Cg_shader, GL_EXT_bindable_uniform, GL_EXT_depth_bounds_test,
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample,
    GL_EXT_framebuffer_object, GL_EXTX_framebuffer_mixed_formats,
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4,
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil,
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D,
    GL_EXT_texture_array, GL_EXT_texture_buffer_object,
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB,
    GL_EXT_texture_shared_exponent, GL_EXT_timer_query, GL_EXT_vertex_array,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color,
    GL_NV_depth_buffer_float, GL_NV_conditional_render, GL_NV_depth_clamp,
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance,
    GL_NV_fragment_program, GL_NV_fragment_program_option,
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage,
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_half_float,
    GL_NV_light_max_exponent, GL_NV_multisample_coverage,
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query,
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object,
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart,
    GL_NV_register_combiners, GL_NV_register_combiners2,
    GL_NV_texgen_reflection, GL_NV_texture_compression_vtc,
    GL_NV_texture_env_combine4, GL_NV_texture_expand_normal,
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2,
    GL_NV_texture_shader3, GL_NV_transform_feedback, GL_NV_vertex_array_range,
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_NV_vertex_program2, GL_NV_vertex_program2_option,
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SUN_slice_accum
```



@rnrover

Yeah I guess but it looks like (using google) this is a common thing with linux, a lot of screen tearing :( I hope im wrong though. Alas running this in 64bit wont change my issues, thanks anways friend :)

---

### Post by Majin_Buu on 2008-06-16
=Bump= :popcorn:

---

### Post by Cresho on 2008-06-16
too bad you don't use gnome.  I would of set up up with awsome 200fps visuals on a 60hz lcd.  Mines animate so smooth, it makes me cry.

you will need to adapt my notes into your kubuntu setup.

[http://ubuntuforums.org/showthread.php?t=646356&highlight=smooth](http://ubuntuforums.org/showthread.php?t=646356&highlight=smooth)

---

### Post by luposolo on 2008-06-16
did you install your graphic drivers, if you havent there program called envy that will easily install your drivers here is the link [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by zxscooby on 2008-06-16
I had a similar problem on an old laptop of mine.
After hours of trouble shooting drivers i found that 
the problem was my processor not being utilized properly
due to a problem with powernowd , a cpu scaling module.
I disabled it at startup and the problem was corrected.

---

### Post by prshah on 2008-06-16
> **Majin_Buu said:**
> ```
glxinfo | grep -i direct
direct rendering: Yes
```




OK your graphics seems set up fine. Next lets look at processor usage, and RAM.```
free -m
top -b -n 1
```

Post the outputs. For the "top" command, you will have to scroll past the upper lines in the terminal; ie. "top" will display more than 1 terminal screen worth of information.

---

### Post by Majin_Buu on 2008-06-16
> **prshah said:**
> OK your graphics seems set up fine. Next lets look at processor usage, and RAM.```
free -m
top -b -n 1
```

Post the outputs. For the "top" command, you will have to scroll past the upper lines in the terminal; ie. "top" will display more than 1 terminal screen worth of information.

```
free -m

             total       used       free     shared    buffers     cached
Mem:          2026        417       1608          0         13        243
-/+ buffers/cache:        161       1864
Swap:         5930          0       5930
```


```
top -b -n 1
top - 16:47:35 up 3 min,  1 user,  load average: 0.64, 0.73, 0.33
Tasks: 111 total,   1 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.1%us,  6.3%sy,  0.0%ni, 69.8%id,  6.7%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   2074628k total,   432236k used,  1642392k free,    13464k buffers
Swap:  6072528k total,        0k used,  6072528k free,   249336k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5984 greenfis  20   0  2304 1008  756 R    4  0.0   0:00.02 top
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.32 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0
   48 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify
  136 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod
  178 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  179 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  180 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0
  221 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0
  222 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1
 1414 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0
 1419 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/1
 1420 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux
 1442 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd
 1445 root      15  -5     0    0    0 S    0  0.0   0:00.18 khubd
 1564 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt
 2037 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0
 2042 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1
 2043 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2
 2044 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3
 2342 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0
 2420 root      15  -5     0    0    0 S    0  0.0   0:00.02 scsi_eh_4
 2421 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_5
 2565 root      15  -5     0    0    0 S    0  0.0   0:00.00 kjournald
 2779 root      16  -4  2420  964  380 S    0  0.0   0:00.46 udevd
 3200 root      15  -5     0    0    0 S    0  0.0   0:00.06 rt61pci
 3212 root      15  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused
 4646 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty
 4647 root      20   0  1716  512  440 S    0  0.0   0:00.00 getty
 4649 root      20   0  1716  512  440 S    0  0.0   0:00.00 getty
 4651 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty
 4653 root      20   0  1716  512  440 S    0  0.0   0:00.00 getty
 4833 root      20   0  2456 1352  692 S    0  0.1   0:00.00 acpid
 4889 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/0
 4890 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/1
 4946 syslog    20   0  1936  644  512 S    0  0.0   0:00.04 syslogd
 5003 root      20   0  1872  540  444 S    0  0.0   0:00.20 dd
 5006 klog      20   0  3740 2608  424 S    0  0.1   0:00.18 klogd
 5028 messageb  20   0  2696 1152  792 S    0  0.1   0:00.12 dbus-daemon
 5045 root      20   0 21088 2192 1888 S    0  0.1   0:00.03 NetworkManager
 5059 root      20   0  3536 1320 1132 S    0  0.1   0:00.00 NetworkManagerD
 5098 root      20   0  3252  728  564 S    0  0.0   0:00.00 kdm
 5105 root      20   0 68564  30m 6620 S    0  1.5   0:29.92 Xorg
 5118 avahi     20   0  2760 1400 1180 S    0  0.1   0:00.04 avahi-daemon
 5119 root      20   0  3992 1748 1380 S    0  0.1   0:00.02 kdm
 5121 avahi     20   0  2760  468  288 S    0  0.0   0:00.00 avahi-daemon
 5164 root      20   0  5916 2268 1696 S    0  0.1   0:00.02 cupsd
 5240 root      20   0  2020  904  776 S    0  0.0   0:00.00 dhcdbd
 5259 haldaemo  20   0  6204 4232 3588 S    0  0.2   0:00.40 hald
 5262 root      20   0  7840 2272 1528 S    0  0.1   0:00.02 console-kit-dae
 5324 root      20   0  3352 1152  976 S    0  0.1   0:00.02 hald-runner
 5338 root      20   0  3416 1156 1012 S    0  0.1   0:00.00 hald-addon-inpu
 5344 root      20   0  3428 1208 1060 S    0  0.1   0:00.00 hald-addon-cpuf
 5345 haldaemo  20   0  2204  908  780 S    0  0.0   0:00.00 hald-addon-acpi
 5369 root      20   0  3420 1156 1004 S    0  0.1   0:00.04 hald-addon-stor
 5392 root      20   0  3172 1252 1084 S    0  0.1   0:00.00 hcid
 5402 root      15  -5     0    0    0 S    0  0.0   0:00.00 btaddconn
 5403 root      15  -5     0    0    0 S    0  0.0   0:00.00 btdelconn
 5413 root      20   0  3020 1104  968 S    0  0.1   0:00.00 bluetoothd-serv
 5417 root      20   0  3084 1300 1148 S    0  0.1   0:00.00 bluetoothd-serv
 5423 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd
 5458 daemon    20   0  1984  424  300 S    0  0.0   0:00.00 atd
 5474 root      20   0  2104  892  712 S    0  0.0   0:00.00 cron
 5580 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty
 5598 dhcp      20   0  2440 1188  868 S    0  0.1   0:00.00 dhclient
 5687 greenfis  20   0  1772  528  444 S    0  0.0   0:00.08 x-session-manag
 5791 greenfis  20   0  4480  532  268 S    0  0.0   0:00.00 ssh-agent
 5822 root      20   0  1564  160  100 S    0  0.0   0:00.00 start_kdeinit
 5823 greenfis  20   0 25864 4288 2768 S    0  0.2   0:00.16 kdeinit
 5826 greenfis  20   0 25676 3004 1716 S    0  0.1   0:00.12 dcopserver
 5829 greenfis  20   0 26864 6188 4864 S    0  0.3   0:00.12 klauncher
 5831 greenfis  20   0 31904  12m  10m S    0  0.6   0:00.62 kded
 5836 greenfis  20   0  1696  372  304 S    0  0.0   0:00.00 kwrapper
 5838 greenfis  20   0 26884 7872 6052 S    0  0.4   0:00.14 ksmserver
 5839 greenfis  20   0 30384  11m 8788 S    0  0.6   0:01.48 kwin
 5841 greenfis  20   0 31872  13m  10m S    0  0.7   0:02.56 kdesktop
 5843 greenfis  20   0 35116  16m  13m S    0  0.8   0:02.58 kicker
 5844 greenfis  20   0 25932 5040 3528 S    0  0.2   0:00.02 kio_file
 5845 greenfis  20   0 27024 5852 4292 S    0  0.3   0:00.04 kio_media
 5847 greenfis  20   0 30768  11m 9572 S    0  0.6   0:00.36 kio_uiserver
 5848 greenfis  20   0 26944 5540 3980 S    0  0.3   0:00.02 kio_system
 5849 greenfis  20   0 26988 6164 4584 S    0  0.3   0:00.02 kio_trash
 5878 greenfis  20   0 20960 6864 5156 S    0  0.3   0:01.37 artsd
 5880 greenfis  20   0 26648 7400 5656 S    0  0.4   0:00.12 kaccess
 5883 greenfis  20   0 31256  11m 9008 S    0  0.6   0:00.30 kmix
 5884 greenfis  20   0 29748  15m  13m S    0  0.8   0:00.36 katapult
 5891 greenfis  20   0 33792 9972 7216 S    0  0.5   0:00.24 knotify
 5892 greenfis  20   0 37912  17m  13m S    0  0.9   0:00.68 konqueror
 5897 greenfis  20   0 40012  17m  11m S    0  0.9   0:00.56 python
 5899 greenfis  20   0 32484  10m 8256 S    0  0.5   0:00.26 knetworkmanager
 5900 greenfis  20   0 39648  10m 7272 S    0  0.5   0:00.18 kblueplugd
 5902 greenfis  20   0 27836 9132 6988 S    0  0.4   0:00.26 klipper
 5906 greenfis  20   0 33580  13m 9832 S    0  0.7   0:03.48 adept_notifier
 5907 greenfis  20   0  8036 2120 1732 S    0  0.1   0:00.02 aspell
 5908 greenfis  20   0 37912  17m  13m S    0  0.9   0:00.74 konqueror
 5920 greenfis  20   0  121m  53m  17m S    0  2.6   0:15.68 opera
 5936 greenfis  20   0 61648  18m  14m S    0  0.9   0:01.91 konversation
 5966 greenfis  20   0 33456  14m  11m S    0  0.7   0:00.84 konsole
 5967 greenfis  20   0  5604 3016 1412 S    0  0.1   0:00.26 bash
```

There you go prshah :KS


@luposolo I compiled the drivers my self instead of envyng, since 173 is still in beta

@zxscooby

Got a link?

@Cresho

Thanks but i've already used a similar setup

---

### Post by prshah on 2008-06-16
> **Majin_Buu said:**
> ```
free -m

             total       used       free     shared    buffers     cached
Mem:          2026        417       1608          0         13        243
-/+ buffers/cache:        161       1864
Swap:         5930          0       5930
```


```
top -b -n 1
top - 16:47:35 up 3 min,  1 user,  load average: 0.64, 0.73, 0.33
Tasks: 111 total,   1 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.1%us,  6.3%sy,  0.0%ni, 69.8%id,  6.7%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   2074628k total,   432236k used,  1642392k free,    13464k buffers
Swap:  6072528k total,        0k used,  6072528k free,   249336k cached

```



All look good; I thought you'd have less RAM, but that's obviously not the case.

Final item:
```
sudo hdparm -tT /dev/sda
```

replace /dev/sda with the device that represents your actual ubuntu drive.

---

### Post by Majin_Buu on 2008-06-16
> **prshah said:**
> All look good; I thought you'd have less RAM, but that's obviously not the case.

Final item:
```
sudo hdparm -tT /dev/sda
```

replace /dev/sda with the device that represents your actual ubuntu drive.

```
sudo hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   1472 MB in  2.00 seconds = 735.91 MB/sec
 Timing buffered disk reads:  196 MB in  3.03 seconds =  64.74 MB/sec
```

---

### Post by prshah on 2008-06-16
> **Majin_Buu said:**
> ```

 Timing cached reads:   1472 MB in  2.00 seconds = 735.91 MB/sec
 Timing buffered disk reads:  196 MB in  3.03 seconds =  64.74 MB/sec
```
Also looks OK. Now I give up.```

Graphics     ...     [OK]
Processor    ...     [OK]
RAM          ...     [OK]
HDD          ...     [OK]

```

Can't figure out why you feel the system is not smooth. Bummer.

---

### Post by Majin_Buu on 2008-06-17
> **prshah said:**
> Also looks OK. Now I give up.```

Graphics     ...     [OK]
Processor    ...     [OK]
RAM          ...     [OK]
HDD          ...     [OK]

```

Can't figure out why you feel the system is not smooth. Bummer.

Hi prshah! Thanks for at least trying to help me. Well it's kinda hard to explain I wish I could have made a video, it's easier to detect in motion.

Just imagine there's a lot of screen tearing and the system doesnt run "smooth"... I don't know how to explain it...

But if you remember in windows, if you're using a generic driver instead of your gpus vendors one, the system will have lots of screen tearing and pretty unstable GUI.

Thanks again :)

---

