---
title: "ATI/AIGLX open source driver video playback issues"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by pormogo on 2007-05-01
hey guys I recently moved this box onto feisty and decided that I would go with the open source drivers and AIGLX in opposed to the tried and true XGL+fglrx method I have used in the past. Everything is up and running pretty well currently. However anytime I try and view a video (in totem, mplayer, or vlc) I get sound but no video. If I grab onto the player and "wiggle" it with my mouse video returns. Video does not work at all in full screen mode, and rarely plays in expose, or within the pager when I am on another desktop. Below is the "devices" section of my xorg.conf. 

```
Section "Device"
        Identifier      "ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "AGPMode" "8"
        Option          "AGPFastWrite" "true"
        Option          "DisableGLXRootClipping" "true"
        Option          "AddARGBGLXVisuals" "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "EnablePageFlip" "true"
EndSection

```

I also added these lines to my xorg.conf, but I don't think it makes much difference. A friend of mine is having the same issue with an ati9600 card and these drivers and he has a bare bones "device" and "server" section in his xorg.conf. 

```
Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#        InputDevice     "stylus"        "SendCoreEvents"
#        InputDevice     "cursor"        "SendCoreEvents"
#        InputDevice     "eraser"        "SendCoreEvents"
#        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

Here is my glxinfo if it can be of any help

```
[ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_gpu_program_parameters, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

```

EDIT: And the only thing that VLC ever seems to complain about is 
*No accelerated IMDCT transform found*

Which according to a google search is "just normal output" (people with intel macs seem to get it as well).

---

### Post by seensegal on 2007-05-01
I am also having the same issue with playback in Totem and VLC.  I currently have a ATI 9600 AllinWonder.  I installed the drivers from the ATI website but that didn't seem to fix this problem.

---

### Post by dodgePT on 2007-05-04
It seems to be a problem with ATI linux driver, and believe me, there's no solution (at least an easy one).
We have to wait for "all mighty ATI" to improve ATI support in linux, otherwise just go buy yourself a brand new NVidia graphics adapter and solve all your problems :)

---

### Post by pormogo on 2007-05-05
I'm not using ATI's fglrx driver I am using the open source experimental driver.

[i]OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2[/i]

There are plenty of other threads where people are using this drvier with AIGLX without issue. I find it kinda hard to believe that no one is reporting that they can't watch ANY video. There has to be either a fix, which I have been unable to locate, a reported bug in the libgl-mesa-dri driver, which I haven't been able to find either. Or there is something wrong perhaps with my xorg.conf file?

---

### Post by pormogo on 2007-05-05
I'm a total goober, just FYI for anyone who has this issue all you have to do to fix VLC is go into settings>preferences(tick the advanced box)>video>Ouput Module>X11 video output

viola video playback working with mesa-dri

---

### Post by thepossiblehuman on 2007-05-09
Interesting.  I tried the same fix, and I only have 4 small test videos here, but 3 of them are working now.  Embarassingly simple.  :)

Movie Player still doesn't work, but there is a reason why I installed VLC!

---

