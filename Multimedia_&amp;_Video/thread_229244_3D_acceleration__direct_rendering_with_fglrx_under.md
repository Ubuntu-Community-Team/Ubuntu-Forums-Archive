---
title: "3D acceleration / direct rendering with fglrx under XGL"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by M3phista on 2006-08-04
Hey guys!
I thought it better to start a new thread for people who've got XGL/Compiz already working and are now bothering with the lack of 3D acceleration / direct rendering while running XGL-Sessions.

**My question is:**

Is this a problem with the fglrx-driver? :confused: 
If yes, may this be solved in future? (*hope* *hope*)


BTW, my **window-decoration** (titlebar with minimize, maximize, close-buttons)
isn't working, too. May that have something to do with my missing 3D Support?

**My Specs are:**
Amd64 - ATI x700 pcie - 1024RAM
Ubuntu Dapper 6.06 with kernelupgraded to 2.6.15-26-amd64-generic
fglrx-Version 8.27.10
xorg.conf-Version I don't know (how can I find out?)

**I'm using the following repositories:**

deb [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy
deb-src [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

**and applied the 'second HowTo' from** [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)
with no problems.

**fglrxinfo says:**
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5946 (8.27.10)

**glxinfo says:**
```

glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
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
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 1.2 (2.0.5946 (8.27.10))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  1 0 Ncon


```

I would be very happy if someone has a solution for that :-)

Thx and greets, M3phista

---

### Post by inkisidor on 2006-08-11
the same

---

### Post by dcherryholmes on 2006-08-17
same problem, and I've had it for a while.

---

### Post by centyx on 2006-11-12
Did anyone ever find a solution to this? I assume this is an issue w/ the fglrx driver. 

Xorg log sais "(EE) fglrx(0): Hardware has already been locked."

---

### Post by whatever on 2006-11-12
it is impossible to use direct rendering in Xgl. this is caused by the way Xgl works, not by the fglrx driver.

---

### Post by centyx on 2006-11-12
Ok, I've read on the beryl-project forum that if I use nvidia card/driver w/ xgl then direct rendering will work. Is this the case? If so, I guess I'll have to save up for an nvidia card.

EDIT: oops, I get it. Beryl will work w/ the latest nvidia drivers, xgl, or aiglx. Nvidia and aiglx allow for direct rendering, but xgl does not.

---

