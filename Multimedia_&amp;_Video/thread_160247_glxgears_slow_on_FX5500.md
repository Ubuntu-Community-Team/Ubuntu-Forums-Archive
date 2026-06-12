---
title: "glxgears slow on FX5500"
date: 2006-04-14
forum: Multimedia &amp; Video
---

### Post by stocknutz1 on 2006-04-14
I recently installed a GeForece FX5500 w/ 256 MB.

For some reason glxgears is unusually slow:

erics@eric:~$ glxgears -printfps
879 frames in 5.0 seconds = 175.565 FPS
897 frames in 5.0 seconds = 179.231 FPS
886 frames in 5.0 seconds = 177.170 FPS

glxinfo seems to indicate that DR is enabled:

erics@eric:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/AGP/SSE/3DNOW!
OpenGL version string: 2.0.0 NVIDIA 76.67
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample,
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shadow, GL_ARB_shader_objects,
    GL_ARB_shading_language_100, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr,
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,
    GL_EXT_Cg_shader, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side,
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_HP_occlusion_test, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence,
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program,
    GL_NV_fragment_program_option, GL_NV_half_float, GL_NV_light_max_exponent,
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query,
    GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, GL_NV_point_sprite,
    GL_NV_primitive_restart, GL_NV_register_combiners,
    GL_NV_register_combiners2, GL_NV_texgen_reflection,
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4,
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle,
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3,
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2,
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

Nvidia module looks like it is loaded:

erics@eric:~$ lsmod | grep nvidia
nvidia               3711172  12
nvidia_agp              8412  1
agpgart                34888  2 nvidia,nvidia_agp

AGP status looks okay:

erics@eric:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

erics@eric:~$ uname -a
Linux eric 2.6.12-9-k7 #1 Mon Oct 10 13:47:52 BST 2005 i686 GNU/Linux


I'm stumped, does anyone have any ideas?

---

### Post by darknightuk on 2006-04-14
post ur xorg.conf

---

### Post by stocknutz1 on 2006-04-14
erics@eric:~$ cat /etc/X11/xorg.conf | grep -v '#'

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "dbe"
        Load    "nvidia"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "GeForce FX 5500"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
        Option          "TwinView"
        Option          "MetaModes" "1440x900,1440x900"
        Option          "SecondMonitorHorizSync" "30-80"
        Option          "SecondMonitorVertRefresh" "55-75"
        Option          "RenderAccel"           "true"
        Option "NvAGP" "2"
        Option "NoLogo" "1"
        Option "CursorShadow" "1"
        Option "ConnectedMonitor" "crt, crt"
        Option "NoPowerConnectorCheck"
EndSection


Section "Monitor"
        Identifier      "ENV H193WK 0"
        HorizSync       30-80
        VertRefresh     55-75
        Option          "DPMS"
EndSection


Section "Screen"
        Identifier      "Screen 0"
        Device          "GeForce FX 5500"
        Monitor         "ENV H193WK 0"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1280x800"
                Viewport 0 0
        EndSubSection
EndSection


Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Screen 0" 0 0
        Option          "Xinerama" "off"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by taurus on 2006-04-14
How did you install your nVidia driver?

---

### Post by stocknutz1 on 2006-04-14
[QUOTE=taurus]How did you install your nVidia driver?[/QUOTE]
Just apt-get out of the universe/multiverse repositories. I didn't compile or run the nvidia install script.

---

### Post by PriceChild on 2006-04-14
[quote=stocknutz1]I didn't compile or run the nvidia install script.[/quote]

Use method 2:

[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

Works a dream for me :)

---

