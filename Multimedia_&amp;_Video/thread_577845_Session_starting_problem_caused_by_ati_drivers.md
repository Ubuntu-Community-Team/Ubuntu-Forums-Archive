---
title: "Session starting problem caused by ati drivers"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by aGoY on 2007-10-16
Hello everybody,

This afternoon I was bored, so I upgrade Ubuntu from Feisty to Gutsy.. all works good the first time, but the second one when I tried to start my session I get this error:

```

/etc/gdm/Xsession: Beginning session setup...
.: 20: Can't open /etc/ati/ati-fglrx.sh

```

This was because I tried to unistall the ati driver to install it by the Ubuntu way.. 

Any idea on how to solve the problem? How to unistall this drivers (it doens't work for me :/)?


Cheers, aGoY!

---

### Post by aGoY on 2007-10-17
Sorry for the double post, but... any idea? :-k:-|

**EDIT:** I read that envy is now avaible for Ubuntu Gutsy Gibbon, so trying to install the ati drivers :P.

[COLOR=Black]**EDIT 2:** Ok it seems something wrong when I installed the ATI drivers via Envy.. when I do "glxinfo" I get: [/COLOR]

```
agoy@agoy-pc:~$ glxinfo
name of display: :1.0
** Xlib:  extension "XFree86-DRI" missing on display ":1.0".**
display: :1  screen: 0
** direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)**
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
[B][I]OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 / X1550 Series
OpenGL version string: 1.2 (2.0.6747 (8.40.4))[/I][/B]
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

```

agoy@agoy-pc:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
4099 frames in 5.3 seconds = 770.216 FPS
1582 frames in 5.1 seconds = 307.578 FPS
1483 frames in 5.0 seconds = 294.351 FPS
1808 frames in 5.3 seconds = 339.941 FPS
1695 frames in 5.0 seconds = 336.429 FPS
etc...

```

So I don't know where is the problem, the drivers seems to recognize my video card (ATI Radeon X1300 Series), but it says: [COLOR="DarkOrange"] ** direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)**[/COLOR]. How to do this?


[COLOR=Red]** Xlib:  extension "XFree86-DRI" missing on display ":1.0".**[COLOR=Black]-> How to solve this? I searched on Google but I didn't get a good answer :/.[/COLOR][/COLOR] 


And I observed that some program is using everytime the 100% power of the CPU. I looked up in the System Monitor but there aren't any that use 100%, so if someone could tell me a command to watch it in the terminal or... :)


Sorry, I'm not an advanced user..and sorry for my English!

**EDIT 3:**

When I use "top" command on a termianl the udevd process uses almost all the CPU, any idea on how to solve this?
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2856 root      21  -4 45524  42m  500 R 87.2  2.1  45:17.53 udevd  
```

See you!

---

