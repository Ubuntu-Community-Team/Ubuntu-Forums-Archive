---
title: "Upgrade in Video Hardware == Downgrade in X performance?"
date: 2010-04-14
forum: Multimedia Software
---

### Post by Cyclops_ on 2010-04-14
Hi all!

I just purchased some upgrades in Hardware, in order to support 3 monitors.  I tried playing around with getting Compiz set up on them, but as I have been unable to get it to work with Xinerama, at the moment, I am back to no Compiz.

HOWEVER, without Compiz, one would think, that with my hardware, I should be rocking the video scene....  BUT it turns out that's not the case.  Anything that requires screen updating is causing extra CPU load.  When I run 'htop' it tells me that it's the X server who's the culprit.  Seriously, with the video cards that I have, this should _not_ be a problem!

Here is what I have:

Two nVidia GeForce GTS 250's
Core 2 Duo 3.0GHz
XFX nForce 750i board
Three LCD monitors


Here is my xorg.conf:

```

Section "Files"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    #FontPath        "/usr/share/fonts/X11/util"
    #FontPath        "/usr/share/fonts/X11/encodings"
    #FontPath        "unix/:7100"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 75.0
    VertRefresh     56.0 - 61.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "KTC W2408S"
    HorizSync       31.0 - 75.0
    VertRefresh     56.0 - 63.0
    #Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "NTS MB24W"
    HorizSync       30.0 - 74.0
    VertRefresh     50.0 - 61.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    Option         "AllowGLXWithComposite" "true"
    Option         "UseCompositeWrapper" "true"
    Option         "NoLogo" "True"
    Option         "backingstore" "true"
    Option         "TripleBuffer" "true"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "true"
    Option         "UseCompositeWrapper" "true"
    Option         "AddARGBGLXVisuals" "true"
    Option         "NoLogo" "True"
    Option         "backingstore" "true"
    Option         "TripleBuffer" "true"
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "true"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    # Removed Option "TwinView" "1"
    SubSection "Display"
        Depth       24
    EndSubSection
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load    "glx"
    Disable    "dri2"
    #Load           "freetype"
    #Disable    "dri2"
    #Load           "dri"
    #Load           "type1"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 3840 0
    Screen      1  "Screen1" 0 0
    Screen      2  "Screen2" 1920 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "Xinerama" "1"
    Option         "AIGLX" "true"
    #Option         "XGL" "true"
EndSection

Section "Device"
    Identifier     "Device0"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
    BusID          "PCI:3:0:0"
    Screen          0
    Driver    "nvidia"
EndSection

Section "Device"
    Identifier     "Device1"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
    BusID          "PCI:4:0:0"
    Driver    "nvidia"
EndSection

Section "Device"
    Identifier     "Device2"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
    Option         "AllowGLXWithComposite" "true"
    Option         "UseCompositeWrapper" "true"
    Option         "NoLogo" "True"
    Option         "backingstore" "true"
    Option         "TripleBuffer" "true"
    Option         "AddARGBGLXVisuals" "true"
    BusID          "PCI:3:0:0"
    Screen          1
    Driver    "nvidia"
    #Option         "XAANoOffscreenPixmaps"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

```I _did_ install xserver-xgl, but right now it's disabled (by creating the file ~/.config/xserver-xgl/disable).

If anyone can please help, I would much appreciate.  My CPU load goes up any time anything graphical happens, including something as simple as just moving a window around!!!!!  (or resizing one for that matter).

I've tried various nVidia drivers.  Among them:
```

173.14.20-0ubuntu5
185.18.36-0ubuntu10~karmic~nvidiavdpauppa8
190.53-0ubuntu1~karmic~nvidiavdpauppa14
195.36.15-0ubuntu1~karmic~nvidiavdpauppa2

```PLEASE HELP!

Sincerely,
Going Insane :)

---

### Post by Yellow Pasque on 2010-04-14
It sounds like direct rendering is not working. Posting your /var/log/Xorg.0.log file or at least the output of this might be helpful:
```
LIBGL_DEBUG=verbose glxinfo
```

---

### Post by Cyclops_ on 2010-04-15
OK.  Here you go.

for LIBGL_DEBUG=verbose glxinfo:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
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
    GLX_NV_video_capture
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTS 250/PCI/SSE2
OpenGL version string: 3.2.0 NVIDIA 195.36.15
OpenGL shading language version string: 1.50 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_compatibility, GL_ARB_copy_buffer, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_geometry_shader4, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_imaging, GL_ARB_map_buffer_range, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_seamless_cube_map, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_rg, GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
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
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_explicit_multisample, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_transform_feedback, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_NV_vertex_program2, GL_NV_vertex_program2_option, 
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

84 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x31 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x32 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x33 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x42 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x49 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x4a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x4c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x4e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x4f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x54 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x56 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x57 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x5f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x60 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x61 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x63 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x64 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x65 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x66 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x67 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x68 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x69 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x6a 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x6b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x6c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x6d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x6e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x6f 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x70 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x71 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x72 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon

164 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x75  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x76  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x77  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x78  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x79  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x7a  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x7b  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x7c  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x7d  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x7e  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x7f  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x80  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x81  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x82  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x83  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x84  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x85  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x86  0 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x87  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x88  0 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x89  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x8a  0 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x8b  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x8c  0 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x8d  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x8e  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x8f  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x90  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x91  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x92  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x93  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x94  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x95  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x96  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x97  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x98  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x99  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x9a  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x9b  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x9c  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x9d  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x9e  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x9f  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xa0  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xa1  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xa2  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xa3  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xa4  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xa5  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xa6  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xa7  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xa8  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xa9  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xaa  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xab  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xac  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xad  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0xae  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xaf  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0xb0  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0xb1  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xb2  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xb3  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0xb4  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0xb5  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb6  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb7  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0xb8  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0xb9  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xba  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xbb  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xbc  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xbd  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0xbe  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0xbf  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0xc0  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0xc1  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xc2  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xc3  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xc4  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xc5  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0xc6  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0xc7  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0xc8  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0xc9  0 sg  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0xca  0 sg  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0xcb  0 sg  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0xcc  0 sg  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0xcd  0 sg  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0xce  0 sg  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0xcf  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  0 16 16 16 16  0 0 None
0xd0  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  8 16 16 16 16  0 0 None
0xd1  0 sg  0 32  0 r  .  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0xd2  0 sg  0 32  0    .  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0xd3  0 sg  0 32  0 r  y  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0xd4  0 sg  0 32  0    y  . 16 16  0  0  4  0  0 16 16 16 16  0 0 None
0xd5  0 sg  0 32  0 r  .  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0xd6  0 sg  0 32  0    .  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0xd7  0 sg  0 32  0 r  y  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0xd8  0 sg  0 32  0    y  . 32  0  0  0  4  0  0 16 16 16 16  0 0 None
0xd9  0 sg  0 64  0 r  .  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0xda  0 sg  0 64  0    .  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0xdb  0 sg  0 64  0 r  y  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0xdc  0 sg  0 64  0    y  . 16 16 16 16  4  0  0 16 16 16 16  0 0 None
0xdd  0 sg  0 128  0 r  .  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0xde  0 sg  0 128  0    .  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0xdf  0 sg  0 128  0 r  y  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0xe0  0 sg  0 128  0    y  . 32 32 32 32  4  0  0 16 16 16 16  0 0 None
0xe1  0 sg  0 32  0 r  .  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0xe2  0 sg  0 32  0    .  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0xe3  0 sg  0 32  0 r  y  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0xe4  0 sg  0 32  0    y  . 16 16  0  0  4 24  0 16 16 16 16  0 0 None
0xe5  0 sg  0 32  0 r  .  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0xe6  0 sg  0 32  0    .  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0xe7  0 sg  0 32  0 r  y  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0xe8  0 sg  0 32  0    y  . 16 16  0  0  4 24  8 16 16 16 16  0 0 None
0xe9  0 sg  0 32  0 r  .  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0xea  0 sg  0 32  0    .  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0xeb  0 sg  0 32  0 r  y  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0xec  0 sg  0 32  0    y  . 32  0  0  0  4 24  0 16 16 16 16  0 0 None
0xed  0 sg  0 32  0 r  .  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0xee  0 sg  0 32  0    .  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0xef  0 sg  0 32  0 r  y  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0xf0  0 sg  0 32  0    y  . 32  0  0  0  4 24  8 16 16 16 16  0 0 None
0xf1  0 sg  0 64  0 r  .  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0xf2  0 sg  0 64  0    .  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0xf3  0 sg  0 64  0 r  y  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0xf4  0 sg  0 64  0    y  . 16 16 16 16  4 24  0 16 16 16 16  0 0 None
0xf5  0 sg  0 64  0 r  .  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0xf6  0 sg  0 64  0    .  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0xf7  0 sg  0 64  0 r  y  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0xf8  0 sg  0 64  0    y  . 16 16 16 16  4 24  8 16 16 16 16  0 0 None
0xf9  0 sg  0 128  0 r  .  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0xfa  0 sg  0 128  0    .  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0xfb  0 sg  0 128  0 r  y  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0xfc  0 sg  0 128  0    y  . 32 32 32 32  4 24  0 16 16 16 16  0 0 None
0xfd  0 sg  0 128  0 r  .  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0xfe  0 sg  0 128  0    .  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0xff  0 sg  0 128  0 r  y  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x100  0 sg  0 128  0    y  . 32 32 32 32  4 24  8 16 16 16 16  0 0 None
0x101  0 sg  0 16  0 r  .  . 16  0  0  0  4  0  0 16 16 16 16  0 0 None
0x102  0 sg  0 16  0    .  . 16  0  0  0  4  0  0 16 16 16 16  0 0 None
0x103  0 sg  0 16  0 r  y  . 16  0  0  0  4  0  0 16 16 16 16  0 0 None
0x104  0 sg  0 16  0    y  . 16  0  0  0  4  0  0 16 16 16 16  0 0 None
0x105  0 sg  0 64  0 r  .  . 32 32  0  0  4  0  0 16 16 16 16  0 0 None
0x106  0 sg  0 64  0    .  . 32 32  0  0  4  0  0 16 16 16 16  0 0 None
0x107  0 sg  0 64  0 r  y  . 32 32  0  0  4  0  0 16 16 16 16  0 0 None
0x108  0 sg  0 64  0    y  . 32 32  0  0  4  0  0 16 16 16 16  0 0 None
0x109  0 sg  0 16  0 r  .  . 16  0  0  0  4 24  0 16 16 16 16  0 0 None
0x10a  0 sg  0 16  0    .  . 16  0  0  0  4 24  0 16 16 16 16  0 0 None
0x10b  0 sg  0 16  0 r  y  . 16  0  0  0  4 24  0 16 16 16 16  0 0 None
0x10c  0 sg  0 16  0    y  . 16  0  0  0  4 24  0 16 16 16 16  0 0 None
0x10d  0 sg  0 16  0 r  .  . 16  0  0  0  4 24  8 16 16 16 16  0 0 None
0x10e  0 sg  0 16  0    .  . 16  0  0  0  4 24  8 16 16 16 16  0 0 None
0x10f  0 sg  0 16  0 r  y  . 16  0  0  0  4 24  8 16 16 16 16  0 0 None
0x110  0 sg  0 16  0    y  . 16  0  0  0  4 24  8 16 16 16 16  0 0 None
0x111  0 sg  0 64  0 r  .  . 32 32  0  0  4 24  0 16 16 16 16  0 0 None
0x112  0 sg  0 64  0    .  . 32 32  0  0  4 24  0 16 16 16 16  0 0 None
0x113  0 sg  0 64  0 r  y  . 32 32  0  0  4 24  0 16 16 16 16  0 0 None
0x114  0 sg  0 64  0    y  . 32 32  0  0  4 24  0 16 16 16 16  0 0 None
0x115  0 sg  0 64  0 r  .  . 32 32  0  0  4 24  8 16 16 16 16  0 0 None
0x116  0 sg  0 64  0    .  . 32 32  0  0  4 24  8 16 16 16 16  0 0 None
0x117  0 sg  0 64  0 r  y  . 32 32  0  0  4 24  8 16 16 16 16  0 0 None
0x118  0 sg  0 64  0    y  . 32 32  0  0  4 24  8 16 16 16 16  0 0 None

```

For /var/log/Xorg.0.log:
```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux camelot 2.6.31-20-generic-pae #58-Ubuntu SMP Fri Mar 12 06:25:51 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=cf2256fb-f62a-453f-abc6-ff997d3e7f88 ro splash quiet splash
Build Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 14 10:34:36 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Screen "Screen2" (2)
(**) |   |-->Monitor "Monitor2"
(**) |   |-->Device "Device2"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "1"
(**) Option "AIGLX" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(!!) More than one possible primary device found.  Using first one seen.
(--) PCI:*(0:3:0:0) 10de:0615:196e:0593 nVidia Corporation G92 [GeForce GTS 250] rev 162, Mem @ 0xf9000000/16777216, 0xc0000000/268435456, 0xf6000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(--) PCI: (0:4:0:0) 10de:0615:0000:0000 nVidia Corporation G92 [GeForce GTS 250] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.15  Thu Mar 11 23:39:48 PST 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.15  Thu Mar 11 22:01:49 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "TripleBuffer" "true"
(**) NVIDIA(0): Option "UseCompositeWrapper" "true"
(**) Apr 14 10:34:36 NVIDIA(0): Enabling RENDER acceleration
(II) Apr 14 10:34:36 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Apr 14 10:34:36 NVIDIA(0):     enabled.
(II) Apr 14 10:34:37 NVIDIA(0): NVIDIA GPU GeForce GTS 250 (G92) at PCI:3:0:0 (GPU-0)
(--) Apr 14 10:34:37 NVIDIA(0): Memory: 1048576 kBytes
(--) Apr 14 10:34:37 NVIDIA(0): VideoBIOS: 62.92.89.00.51
(II) Apr 14 10:34:37 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Apr 14 10:34:37 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Apr 14 10:34:37 NVIDIA(0): Connected display device(s) on GeForce GTS 250 at PCI:3:0:0:
(--) Apr 14 10:34:37 NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) Apr 14 10:34:37 NVIDIA(0):     NTS MB24W (DFP-1)
(--) Apr 14 10:34:37 NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
(--) Apr 14 10:34:37 NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
(--) Apr 14 10:34:37 NVIDIA(0): NTS MB24W (DFP-1): 330.0 MHz maximum pixel clock
(--) Apr 14 10:34:37 NVIDIA(0): NTS MB24W (DFP-1): Internal Dual Link TMDS
(II) Apr 14 10:34:37 NVIDIA(0): Display Device found referenced in MetaMode: DFP-0
(WW) Apr 14 10:34:37 NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
(WW) Apr 14 10:34:37 NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
(WW) Apr 14 10:34:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Apr 14 10:34:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Apr 14 10:34:37 NVIDIA(0):     VertRefresh check for mode "1920x1080".
(WW) Apr 14 10:34:37 NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
(WW) Apr 14 10:34:37 NVIDIA(0):     mode "1280x720" is specified in the EDID; however, the
(WW) Apr 14 10:34:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Apr 14 10:34:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Apr 14 10:34:37 NVIDIA(0):     VertRefresh check for mode "1280x720".
(WW) Apr 14 10:34:37 NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
(WW) Apr 14 10:34:37 NVIDIA(0):     mode "720x576" is specified in the EDID; however, the
(WW) Apr 14 10:34:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Apr 14 10:34:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Apr 14 10:34:37 NVIDIA(0):     VertRefresh check for mode "720x576".
(WW) Apr 14 10:34:37 NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
(WW) Apr 14 10:34:37 NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
(WW) Apr 14 10:34:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Apr 14 10:34:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Apr 14 10:34:37 NVIDIA(0):     VertRefresh check for mode "1920x1080".
(WW) Apr 14 10:34:37 NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
(WW) Apr 14 10:34:37 NVIDIA(0):     mode "1280x720" is specified in the EDID; however, the
(WW) Apr 14 10:34:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Apr 14 10:34:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Apr 14 10:34:37 NVIDIA(0):     VertRefresh check for mode "1280x720".
(WW) Apr 14 10:34:37 NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
(WW) Apr 14 10:34:37 NVIDIA(0):     mode "720x576" is specified in the EDID; however, the
(WW) Apr 14 10:34:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Apr 14 10:34:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Apr 14 10:34:37 NVIDIA(0):     VertRefresh check for mode "720x576".
(II) Apr 14 10:34:37 NVIDIA(0): Assigned Display Device: DFP-0
(II) Apr 14 10:34:37 NVIDIA(0): Validated modes:
(II) Apr 14 10:34:37 NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0"
(II) Apr 14 10:34:37 NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) Apr 14 10:34:37 NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config
(--) Apr 14 10:34:37 NVIDIA(0):     option
(==) Apr 14 10:34:37 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "NoLogo" "True"
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "nvidia-auto-select +0+0"
(**) NVIDIA(1): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(1): Option "TripleBuffer" "true"
(**) NVIDIA(1): Option "AddARGBGLXVisuals" "true"
(**) NVIDIA(1): Option "UseCompositeWrapper" "true"
(**) Apr 14 10:34:37 NVIDIA(1): Enabling RENDER acceleration
(II) Apr 14 10:34:37 NVIDIA(1): NVIDIA GPU GeForce GTS 250 (G92) at PCI:4:0:0 (GPU-1)
(--) Apr 14 10:34:37 NVIDIA(1): Memory: 1048576 kBytes
(--) Apr 14 10:34:37 NVIDIA(1): VideoBIOS: 62.92.7d.00.00
(II) Apr 14 10:34:37 NVIDIA(1): Detected PCI Express Link width: 8X
(--) Apr 14 10:34:37 NVIDIA(1): Interlaced video modes are supported on this GPU
(--) Apr 14 10:34:37 NVIDIA(1): Connected display device(s) on GeForce GTS 250 at PCI:4:0:0:
(--) Apr 14 10:34:37 NVIDIA(1):     KTC W2408S (CRT-1)
(--) Apr 14 10:34:37 NVIDIA(1): KTC W2408S (CRT-1): 400.0 MHz maximum pixel clock
(II) Apr 14 10:34:37 NVIDIA(1): Assigned Display Device: CRT-1
(II) Apr 14 10:34:37 NVIDIA(1): Validated modes:
(II) Apr 14 10:34:37 NVIDIA(1):     "nvidia-auto-select+0+0"
(II) Apr 14 10:34:37 NVIDIA(1): Virtual screen size determined to be 1920 x 1200
(--) Apr 14 10:34:37 NVIDIA(1): DPI set to (93, 95); computed from "UseEdidDpi" X config
(--) Apr 14 10:34:37 NVIDIA(1):     option
(**) Apr 14 10:34:37 NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(2): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(2): RGB weight 888
(==) NVIDIA(2): Default visual is TrueColor
(==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(2): Option "NoLogo" "True"
(**) NVIDIA(2): Option "TwinView" "0"
(**) NVIDIA(2): Option "MetaModes" "DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(2): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(2): Option "TripleBuffer" "true"
(**) NVIDIA(2): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(2): Option "UseCompositeWrapper" "true"
(**) Apr 14 10:34:37 NVIDIA(2): Enabling RENDER acceleration
(II) Apr 14 10:34:37 NVIDIA(2): NVIDIA GPU GeForce GTS 250 (G92) at PCI:3:0:0 (GPU-0)
(--) Apr 14 10:34:37 NVIDIA(2): Memory: 1048576 kBytes
(--) Apr 14 10:34:37 NVIDIA(2): VideoBIOS: 62.92.89.00.51
(II) Apr 14 10:34:37 NVIDIA(2): Detected PCI Express Link width: 16X
(--) Apr 14 10:34:37 NVIDIA(2): Interlaced video modes are supported on this GPU
(--) Apr 14 10:34:37 NVIDIA(2): Connected display device(s) on GeForce GTS 250 at PCI:3:0:0:
(--) Apr 14 10:34:37 NVIDIA(2):     Samsung SyncMaster (DFP-0)
(--) Apr 14 10:34:37 NVIDIA(2):     NTS MB24W (DFP-1)
(--) Apr 14 10:34:37 NVIDIA(2): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
(--) Apr 14 10:34:37 NVIDIA(2): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
(--) Apr 14 10:34:37 NVIDIA(2): NTS MB24W (DFP-1): 330.0 MHz maximum pixel clock
(--) Apr 14 10:34:37 NVIDIA(2): NTS MB24W (DFP-1): Internal Dual Link TMDS
(II) Apr 14 10:34:37 NVIDIA(2): Display Device found referenced in MetaMode: DFP-1
(WW) Apr 14 10:34:37 NVIDIA(2): The EDID for NTS MB24W (DFP-1) contradicts itself: mode
(WW) Apr 14 10:34:37 NVIDIA(2):     "1600x1200" is specified in the EDID; however, the EDID's
(WW) Apr 14 10:34:37 NVIDIA(2):     valid HorizSync range (30.000-74.000 kHz) would exclude
(WW) Apr 14 10:34:37 NVIDIA(2):     this mode's HorizSync (75.0 kHz); ignoring HorizSync check
(WW) Apr 14 10:34:37 NVIDIA(2):     for mode "1600x1200".
(WW) Apr 14 10:34:37 NVIDIA(2): The EDID for NTS MB24W (DFP-1) contradicts itself: mode
(WW) Apr 14 10:34:37 NVIDIA(2):     "1600x1200" is specified in the EDID; however, the EDID's
(WW) Apr 14 10:34:37 NVIDIA(2):     valid HorizSync range (30.000-74.000 kHz) would exclude
(WW) Apr 14 10:34:37 NVIDIA(2):     this mode's HorizSync (75.0 kHz); ignoring HorizSync check
(WW) Apr 14 10:34:37 NVIDIA(2):     for mode "1600x1200".
(II) Apr 14 10:34:38 NVIDIA(2): Assigned Display Device: DFP-1
(II) Apr 14 10:34:38 NVIDIA(2): Validated modes:
(II) Apr 14 10:34:38 NVIDIA(2):     "DFP-1:nvidia-auto-select+0+0"
(II) Apr 14 10:34:38 NVIDIA(2): Virtual screen size determined to be 1920 x 1200
(--) Apr 14 10:34:38 NVIDIA(2): DPI set to (95, 95); computed from "UseEdidDpi" X config
(--) Apr 14 10:34:38 NVIDIA(2):     option
(**) Apr 14 10:34:38 NVIDIA(2): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Apr 14 10:34:38 NVIDIA: Using 768.00 MB of virtual memory for indirect framebuffer
(II) Apr 14 10:34:38 NVIDIA:     access.
(II) Apr 14 10:34:38 NVIDIA(0): Initialized GPU GART.
(II) Apr 14 10:34:38 NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) Apr 14 10:34:38 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Apr 14 10:34:38 NVIDIA(0): Initialized X Rendering Acceleration
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(**) NVIDIA(0): Option "BackingStore" "true"
(**) NVIDIA(0): Backing store enabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Apr 14 10:34:38 NVIDIA(1): Initialized GPU GART.
(II) Apr 14 10:34:38 NVIDIA(1): Setting mode "nvidia-auto-select+0+0"
(II) Apr 14 10:34:38 NVIDIA(1): Initialized OpenGL Acceleration
(==) NVIDIA(1): Disabling shared memory pixmaps
(II) Apr 14 10:34:38 NVIDIA(1): Initialized X Rendering Acceleration
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules//libxaa.so
(**) NVIDIA(1): Option "BackingStore" "true"
(**) NVIDIA(1): Backing store enabled
(==) NVIDIA(1): Silken mouse enabled
(II) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) Apr 14 10:34:38 NVIDIA(2): Initialized GPU GART.
(II) Apr 14 10:34:38 NVIDIA(2): Setting mode "DFP-1:nvidia-auto-select+0+0"
(II) Apr 14 10:34:38 NVIDIA(2): Initialized OpenGL Acceleration
(==) NVIDIA(2): Disabling shared memory pixmaps
(II) Apr 14 10:34:38 NVIDIA(2): Initialized X Rendering Acceleration
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules//libxaa.so
(**) NVIDIA(2): Option "BackingStore" "true"
(**) NVIDIA(2): Backing store enabled
(==) NVIDIA(2): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(2): DPMS enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Entity 2 shares no resources
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "dvp"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "dvp"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "dvp"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 12 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "dvp"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.

```

Is there anything else I can provide or output you need?

Thank you!

---

### Post by Cyclops_ on 2010-04-17
*bump*  :'(

---

### Post by Cyclops_ on 2010-04-28
*bump!!!!!*

Please, anyone, some help?

THANK YOU

---

