---
title: "ATI Radeon Mobility 9000 Laptop drivers and instalation"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by oraste on 2007-11-12
Hello,

Here is how I got my "Ati radeon 9000 mobility" to work on my old old Amilo laptop. I know there is still ppl who use this ainchent junk and Im one of them. I have been told serval times that there is no change to get this to work and ones again the amilo makes comeback!. Runned 100 lines of commands and messed my computer up. This "Tutorial" does not need even console.

1. installed Ubuntu.
2. Downloaded all updates.
3. Installed Envy --> [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) or Google
4. Used Envy to remove ATI drivers.
5. Installed Ati Drivers manually and choose the oldest version u have there!
6. Reboot and I should work.

I had some problems on this, After I removed the ATI drivers my Ubunty tryed to use VESA drivers. Just look that your xorg.conf has ther ATI on the driver. 

Hope this helps I was looking for this answer for sometime. Now my Cedega and Wine runs games and 3D soft... yay

Copy of GLXINFO: Before this is was like "empty" now it works a real prove that Amilo can do it, you can do it and your ATI mobility 9000 can do it :D

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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x5b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by swoop_ubu on 2007-11-12
mate,

you could be my saviour man! I have very old DELL Latitude 600 with ATI Radeon 9000.
I couldn't make it work (spent only one evening). I hope this is going to work.

I'll keep you (all) posted.

cheers
swoop

---

### Post by swoop_ubu on 2007-11-13
> **oraste said:**
> 
1. installed Ubuntu.
2. Downloaded all updates.
3. Installed Envy --> [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) or Google
4. Used Envy to remove ATI drivers.
5. Installed Ati Drivers manually and choose the oldest version u have there!
6. Reboot and I should work.


mate,

I followed your instructions and what I got was:
"ENVY ERROR: Legacy driver is not supported by your system version".

I do not remember the message exactly. Thus NO SUCCESS!

does anyone have any suggestions? I'm using Ubuntu 7.10 on Dell Latitude 600.

thanks in advance

cheers

---

### Post by Bablefish on 2007-11-13
You can get the lastest ATI Linux driver from  here

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by Hachi on 2007-11-13
> **swoop_ubu said:**
> mate,

I followed your instructions and what I got was:
"ENVY ERROR: Legacy driver is not supported by your system version".


cheers

I'm getting the same error, here's what my log contains:
```

python pulse.py ati oldest
root@external:/usr/share/envy# python pulse.py ati oldest
Envy - Version 0.9.8
Ubuntu Gutsy 32bit
ENVY ERROR: ATI's legacy driver does not support your operating system
```

Any ideas? I'd really like to get 3D working on my Thinkpad again - it stopped working on Feisty because of the newer driver dropping support for some older cards, and it still doesn't seem to be supported in Gutsy.

Thanks.

---

### Post by Olivaw on 2007-11-15
> **Bablefish said:**
> You can get the lastest ATI Linux driver from  here

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

Well, I tried getting the ATI Linux driver for the Radeon Mobility 9000 and when I went to install I got another error  


```

olivaw@Aurora:~/ati$ sudo sh ./ati-driver-installer-8.28.8.run --install
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.........................................................................................................
...........................................................................................................................
...........................................................................................................................
......................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 1.3.0

Detected version of X does not have a matching 'x130' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        Unknown X Window
    x710_64a    Unknown X Window
Removing temporary directory: fglrx-install
olivaw@Aurora:~/ati$ 

```

Any thoughts?

---

### Post by oraste on 2007-11-16
> **swoop_ubu said:**
> mate,

I followed your instructions and what I got was:
"ENVY ERROR: Legacy driver is not supported by your system version".

I do not remember the message exactly. Thus NO SUCCESS!

does anyone have any suggestions? I'm using Ubuntu 7.10 on Dell Latitude 600.

thanks in advance

cheers

Yes I got this too, but then I selected the Instal drivers manually. I dont have this DELL cpu. but I have seen em on the forum, I think the its almost the same than my Amilo. 

The manual driver instalation should work, even its not supported.

---

### Post by natrium on 2008-02-21
i had the same problem
i tried with this command

   X_VERSION=x680 sudo ./ati-driver-installer-8.28.8.run --install

and got the graphical install gui

---

### Post by waldorf on 2008-02-26
I got a "bad substitution" error and never got beyond that any thoughts

---

