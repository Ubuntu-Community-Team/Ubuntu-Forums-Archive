---
title: "ati 9200 pro, fgrlx driver, videos are not running fluently"
date: 2006-10-03
forum: Multimedia &amp; Video
---

### Post by Snifffurt on 2006-10-03
Hello

I'm not shore if I may ask such a question in here, because I'm using edgy-beta-i386 on a amd64 machine. Correct me if this is not meeting the rules of this forum.

I get problems running the xorg fglrx driver on my 9200 pro ati card. In normal desktop usage I don't get any trouble so far.
But playing a divx video with Xine or mplayer does result in jitering video output. The movies run very slow and not fluent at all.

This is my xorgconf: [http://phpfi.com/159924](http://phpfi.com/159924)
and this is my X.org.0.log: [http://phpfi.com/159925](http://phpfi.com/159925)

Does any one know what I might be doing wrong?

Till today I was using X just with the normal built in ati driver instead and the playback of the videos was back on working properly. But today, when I made the updates, it stopped working with that driver, the computer completely froze and nothing exept  pushing the reset button helped. I could change the Driver "fglrx" in the single user root console, so I'm back in 2D X usage..

Thanks for your help or ideas.

Regards

Casper

---

### Post by Fass on 2006-10-03
Does adding         
```
Option      "VideoOverlay" "on"
Option      "OpenGLOverlay" "off"
```
to the device section just below "driver fglrx" help? Also, what does fglrxinfo say?

---

### Post by Snifffurt on 2006-10-03
Hello

Thanks for your answer.

```
Option      "VideoOverlay" "on"
Option      "OpenGLOverlay" "off"
```

This seems to solve the problem with the film Playback. Thank you. :-D

glxinfo says:```
~$ glxinfo 
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x3d 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

``` now...

and fglrxinfo says:```
:~$ fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

For now I'm quite happy. X is back on working and I can watch my moovies. That's the most needed stuff.

Thank you very much for you're help.

Regards

Casper

---

### Post by Fass on 2006-10-03
If you feel like getting direct rendering (i.e. 3D) to work, you might try adding ```
Section "Extensions"
        Option      "Composite" "0"
EndSection
``` to the end of your xorg.conf. In edgy the compositor is activated by default, but the fglrx drivers don't support it so it has to be turned off.

---

### Post by Snifffurt on 2006-10-04
Hello

3D is sort of working. But if I try 3D acceleration with glxgears it works first, but after maybe 5 seconds or so the gearwheel animation gets slow and jittery.

But movies work, and all the normal desktop purposes work.

Thx allot for your help

Regards

Casper

---

