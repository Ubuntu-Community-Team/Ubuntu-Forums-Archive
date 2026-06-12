---
title: "Solved DRI in XGL but still working on it! (ATI)"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by iamblahhh on 2007-05-07
I have noticed that that when i prompt: 

fglrxinfo:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.0.6458 (8.36.5)name of display: :1.0

```

it looks all nifty and working great

but when i prompt glxinfo:

```
name of display: :1.0
[B]Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No[/B]
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 1.2 (2.0.6458 (8.36.5))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```
the DRI is not enabled...
-therefore you can't play games on XGL, or do alot of rendering and stuff... not cool

however, if you put DISPLAY=:0 (for me atleast, since fglrx is using DISPLAY=:0) all DRI is working...
for example:

googleearth will not start just by default... you will get some error:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
```

typing : DISPLAY=:0 googleearth will solve that problem

my question now is... since setting it on DISPLAY=:0, is there anyway to set this as the default DISPLAY?

---

### Post by Paul S on 2007-05-07
You didn't say, but you must be running Xgl on top of your Xorg.  Xgl is running on DISPLAY :1.0 and Xorg is on DISPLAY :0.0.  So if you want to just run Xorg, you need to kill Xgl or logout and log back in without it.  Of course, if you are using Xgl to be able to run beryl, then you'll lose beryl along with Xgl.

---

### Post by iamblahhh on 2007-05-08
does that mean (for the ati's) i can't run games and beryl at the same time? without typing DISPLAY=:0?

 and yes i am running xgl and beryl is off that

---

### Post by emil.s on 2007-05-10
> **iamblahhh said:**
> does that mean (for the ati's) i can't run games and beryl at the same time? without typing DISPLAY=:0?

 and yes i am running xgl and beryl is off that

You can set the DISPLAY variable in your ~/.bashrc.
Open it with some texteditor and add "DISPLAY=:0" at the end of the file. Log out and log in. finished! :)

Or maybe, you should use "export DISPLAY=:0". I don't know the difference.

---

