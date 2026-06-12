---
title: "blender freezes GNOME"
date: 2009-04-03
forum: Multimedia Software
---

### Post by miscellanyous on 2009-04-03
I have a reproducible problem running Blender 2.45 on ubuntu 8.04 (GNOME 2.22.3). The program is loaded using the command ```
:~$ blender -w -p 0 0 1200 800
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
``` Everything loads up nicely but the mouse pointer immediately changes to a filled in black pointer. Once in the program I select 'Edit mode' and then everything freezes: keyboard, shortcut keys, system monitor... The only exception is the mouse which still moves around the screen. Then I must restart the computer.

There are [some reports]("http://www.blender.org/forum/viewtopic.php?t=12086&postdays=0&postorder=asc&start=0") of problems with blender running compiz window manager, however, I believe I am running metacity.

If it is important, my graphics card is ATI Technologies Inc Rage 128 Pro Ultra TF.

---

### Post by miscellanyous on 2009-04-04
Here is a line from the system log file: /var/log/syslog . It appears when Blender freezes the OS. ```
*cpuname* kernel: [279821.794124] [drm:drm_lock_take] *ERROR* 3 holds heavyweight lock
``` I also have opengl installed correctly (I believe)```
user@cpu:~$ glxinfo
name of display: unix:1165.0
display: unix:1165  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
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
    GLX_ARB_get_proc_address, GLX_EXT_import_context, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_draw_range_elements, 
    GL_EXT_multi_draw_arrays, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_SGIS_texture_border_clamp, 
    GL_SUN_multi_draw_arrays

....

``` I hope this may be helpful to a smart person who can advise me!

---

