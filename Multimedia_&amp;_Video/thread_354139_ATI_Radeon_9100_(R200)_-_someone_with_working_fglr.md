---
title: "ATI Radeon 9100 (R200) - someone with working fglrx on Edgy?"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by kharl on 2007-02-05
I am sorry to say I am not able to get my ati card working with 3d hw acceleration. I would like to use it with Beryl.

I have tried many howtos but without success. So I would like to know if there is someone with same card working correctly without freezing in 3d, screensavers, etc. 

Installation according to [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") leads to black screen after Ubuntu splash logo (on DVI) or freeze (on D-SUB) after a while.

Maybe it is the same problem when I use 3d screensavers. Even when I use "ati" driver i xorg.conf it freezes sooner or later. 

This machine is stable under Win, memtest passed and so on.

The card: ATI Radeon 9100 (R200 chip) 128 MB
Ubuntu/edgy (6.10)
ViewSonic VP930 LCD panel
AMD Athlon XP on ABIT NF7-S

---

### Post by Waappu on 2007-02-05
Hi

Have you looked this already?
[http://ubuntuforums.org/showthread.php?t=338771](http://ubuntuforums.org/showthread.php?t=338771)

---

### Post by nunomiguelmota on 2007-02-05
hi, 
 i think fglrx does not support that card anymore. You should try using the opensource radeon driver and AIGLX to run beryl.

good luck

---

### Post by barney_1 on 2007-02-05
Make sure you have the most up-to-date version of your motherboard bios.  I had a heck of a time tracing my fglrx problems to an older bios version.

---

### Post by kharl on 2007-02-06
Thank you for your suggestions. 

First of all I flashed the latest BIOS (2 years old). Unfortunately it didn't help.

Then I tried "radeon" driver with Waappu's [script]("http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html"). It should be the solution because radeon driver [supports 3D]("https://help.ubuntu.com/community/RadeonDriver#head-839ea46a1da3bee0839b28a9595722a9cdf07797") with R200 cards. So I installed it.

But... :( 

When I start beryl, gnome panel disappears. When I start beryl-manager, gnome is here but nothing works. It is possible to restart X with Ctrl-Alt-Backspace.

glxinfo says: 
> name of display: :0.0
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)
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
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x4b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


---

### Post by barney_1 on 2007-02-06
You need to have direct rendering enabled before you try to run beryl.  That means getting either the Radeon drivers or the FGLRX drivers to work for you.

I don't know if you card is supported by the radeon driver, but here is a thread that might help if it is.  Read post #7:
[http://ubuntuforums.org/showthread.php?t=265678](http://ubuntuforums.org/showthread.php?t=265678)

---

### Post by kharl on 2007-02-07
OK, direct rendering must be enabled. I would like to use Radeon driver.

My card is supported (chip and model listed) on [this page]("http://dri.freedesktop.org/wiki/ATIRadeon#head-7528b1c267d9e6f91e260a66975c28d1866fab2d") (linked from post you have mentioned, thanks for it). 

I am not sure which packages related to fglrx I should uninstall. It is recommended in that post but there is no package "fglrx". Maybe xorg-driver-flgrx is that bad guy but there were some actions connected with disabling the driver in Waappu's script.

In my case, fglrx driver is not loaded:> 
sudo modprobe -r fglrx
FATAL: Module fglrx not found.

---

### Post by kharl on 2007-02-07
I am not sure about settings in xorg.conf for ATI Radeon 9100 with "Radeon" driver. My current xorg.conf (direct rendering: no - in glxinfo) and xorg log are attached to this post.

---

### Post by kharl on 2007-02-09
Please post your xorg.conf and tips if you have Radeon 9100 or Radeon 8500 with 3d direct rendering working on Edgy.

---

