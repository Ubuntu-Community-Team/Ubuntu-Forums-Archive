---
title: "client glx version string: SGI with NVIDIA drivers?!?"
date: 2008-08-30
forum: Multimedia Software
---

### Post by CzaFin on 2008-08-30
Hi!

I've got  a  very annoying problem. It disallows me to use direct rendering...

I've got GeForce 7600 GT AGP card in my computer. Back in the days it worked well, but I updated my ubuntu to Hardy and installed NVIDIA drivers again. I tried to play some games but nuthing worked. I checked ```
glxinfo | grep rendering 
```
and realized that I've got no direct rendering in use. 
I removed --purge and installed NVIDIA drivers again and again, and then again, and some times again again...
But no help. 

No matter what I do, the damn SGI glx client stays there like bubblegum in your hair...** What I should do to get NVIDIA glx client there?**

Here is my glxinfo:
```

cza@cza-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
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
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_EXT_texture_from_pixmap
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE/3DNOW!
OpenGL version string: 1.4 (2.1.2 NVIDIA 169.12)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_NV_blend_square, GL_NV_copy_depth_to_color, GL_NV_depth_clamp, 
    GL_NV_fog_distance, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_light_max_exponent, 
    GL_NV_multisample_filter_hint, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_NV_vertex_program2_option, 
    GL_NV_vertex_program3, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_multi_draw_arrays, GL_SUN_slice_accum


```

ANd here is my xorg.conf
```

#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fi"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/X11R6/lib/X11/fonts/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/X11R6/lib/X11/fonts/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/X11R6/lib/X11/fonts/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/X11R6/lib/X11/fonts/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        Fontpath        "/usr/X11R6/lib/X11/fonts/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dbe"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "DRI"
        Mode    0666
EndSection



```

wHat Should I do? Man, you who can help me! You :guitar: rok!

And I know, there is a similar thread in archives of this forum, but theres a post: "I've solved it..." without any explanation how he did it :S

---

### Post by mfroeschl on 2008-11-29
Hello CzaFin,

I realize this thread has been lying idle for a while... but since I experienced exactly the same problem (client glx version string: SGI) and I wasn't able to find a solution to it anywhere else, I think it is appropriate to reply here.

In my case, I was able to resolve this issue the following way:

First, I followed glxinfo's advice to get more detailed debug information:
 
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

So I exported the debug symbol:

```
>export LIBGL_DEBUG=verbose
```

Unfortunately I don't have the detailed output anymore to paste it here, but when I ran glxinfo it showed me more detailed information: apparently **libGL** was unable to find a certain driver file in the directory "/usr/lib/dri". 

Since re-installing nvidia-glx-177 package did not solve the problem (nor did reinstalling any other related package) I figured it might be caused by a wrong or outdated libGL library or softlink.

Searching for libGL on my system revealed it was present in several locations:
```
/usr/lib/libGL.so
/usr/lib/libGL.so.1
/usr/lib/libGL.so.177.80
/usr/lib/captury/libGL.so
/usr/lib/captury/libGL.so.1
/usr/lib/debug/usr/lib/libGL.so.1.2
/usr/lib/nvidia/libGL.so.1
/usr/lib/nvidia/libGL.so.1.2.xlibmesa
```

/usr/lib/nvidia/libGL.so.1 was linked against /usr/lib/nvidia/libGL.so.1.2.xlibmesa,
whereas /usr/lib/libGL.so was eventually linked against /usr/lib/libGL.so.177.80 (which is probably the right library for the nvidia driver since it shares its version number).

So I tried changing the link /usr/lib/nvidia/libGL.so.1 to point to /usr/lib/libGL.so.177.80 :

```
>rm /usr/lib/nvidia/libGL.so.1
>ln -s /usr/lib/libGL.so.177.80 /usr/lib/nvidia/libGL.so.1
```

After a restart client glx vendor string would finally show as "NVIDIA Corporation", and direct rendering was enabled!

```
>glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: Yes**
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
**client glx vendor string: NVIDIA Corporation**
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video, 
    GLX_NV_multisample_coverage
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7900 GTX/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 177.80
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
```

Also, the solution had the nice side-effect of boosting the performance of "glxgears" from about approx. 9000 fps to 12000 fps.

Note:
I upgraded from Hardy to Intrepid, and I assume that my softlinks were somehow screwed up in the process, because on Hardy direct rendering was working fine and I for one never touched those links. After upgrading to Intrepid I had several issues related to the nvidia drivers.

I hope this information is still useful to you, or anybody else who might run into this problem.

mf

---

