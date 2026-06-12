---
title: "Problems after trying ATI driver install."
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by Nobel on 2007-05-06
Hey guys!

I've had some problems getting drivers for my X1950 to work. I've given up, and decided to postpone my project until i see more reports of it working stable in Ubuntu. As of now, some get it working, some don't. I personally think the varying success-rate is due to the special PCI-E - AGP bridging chip used on the AGP flavor of the card. However, that is the the topic of my post.

I wish to get my graphics drivers back to the state they were when i installed fresh. glxinfo is giving me some odd output, and the restricted drivers guide tells me i don't need any restricted drivers (Indicating they are already installed, even tho i am without 3d support).

Altho i have no plans to try and get the drivers working at the moment (unless one of you has a magical solution :) ), i would like a fresh and "clean" driver running.

My glxinfo outputs 

```
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  17
  Current serial number in output stream:  17

```

I assume you wan't too see part of my xorg.conf, but i'm not gonna post the whole damn thing at first, it's so large :)

Thanks in advance!

---

### Post by thelocust on 2007-05-06
Sorry for all your troubles I got this off fo this forum a few months back and I've been posting it for everyone I can find whos have trouble installing ATI drivers or resolution problems and it's work every time so far I hope you have the same luck with it:

First uninstall everything associated with ATI drivers (binary drivers, FGLRX)
then install **[COLOR=Red]xorg-driver-fglrx[/COLOR]**

Then input these in terminal:
**[COLOR=Red]sudo aticonfig --initial[/COLOR]**
**[COLOR=Red]sudo aticonfig --overlay-type=Xv[/COLOR]**

Finally, **[COLOR=Red]sudo dpkg-reconfigure xserver-xorg[/COLOR]**, selecting the **[COLOR=Red]fglrx[/COLOR]** driver and setting your monitor resolution how you want it

Then rebooted and that should do it.

---

### Post by Nobel on 2007-05-07
Is that going to work for the X1950?

I'm asking because i think my card is sort of a special case. I've seen a lot of people having problems with it, and it's not officially supported yet either (From what i've read only up to X1900 is supported).

As far as i understand, FGLRX is the ATI driver. I'd rather reverse to the default driver and wait with FGLRX stuff untill i can get full support

---

### Post by ubhpvca on 2007-06-01
Good evening.I am a new user to ubuntu OS and when i typed GLXINFO i got this on my terminal:

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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

My card is X1900 GT , so do u believe thelocust that if i do what you say ,might work for me too ?

Regards
Jimmy

---

