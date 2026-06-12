---
title: "Problems with video playback using compiz under Nvidia"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by leoscuro on 2006-10-01
Hi, first of all I am a newbie that has learned a lot from this community.
Thanks to all the different posts and discussions on this forum I manage to install compiz on my Compaq Presario R3000.

I have and AMD 64 processor but I am running the i386 version to get more compatibility on the distro. 

After installing the compiz using the following tutorial:
[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

Compiz is running great , but when I started a dvd movie on full screen i could notice the video was running a tad bit slow. (this on the Totem-xine "movie" player that is my default dvd and video player).

I got some video issues, and I read this guide that adreesed my problems:
[http://ubuntuforums.org/showthread.php?t=239617&highlight=dvd+playback+compiz](http://ubuntuforums.org/showthread.php?t=239617&highlight=dvd+playback+compiz)

After following the steps the full screen video problems I had went away..but they have been replaced by the video being interrputed with a flash every two seconds. 
Its basically a white flicker...this one second white flicker really ruined my triumph.

What you guys and gals think this can be?

---

### Post by leoscuro on 2006-10-01
Help anybody?

Do you need more information?

Tell me what I should post to let you guys help me on this one!

---

### Post by leoscuro on 2006-10-01
I just realized that this "white flicker" is appearing on my GL screensavers as well...might this mean this is an open GL configuration problem?

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_SGIX_fbconfig, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 440 Go 64M/AGP/SSE2/3DNOW!
OpenGL version string: 1.2 (1.5.6 NVIDIA 87.62)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_vertex_program, GL_ARB_window_pos,
    GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod, GL_EXT_texture_lod_bias,
    GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square,
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by leoscuro on 2006-10-01
I just switched to berryl and I am still having the same video issues...please I need a kind soul to point me to what might be my problem...

---

### Post by leoscuro on 2006-10-02
...well...the firefox mplayer plug in is working well too...the problem seems to be between totem and the opengl and some of the gl screensavers (like GL matrix wich was my screensaver of choice but now is not working, it runs but the screens remains black).

Please, I need help, this is the only thing betwen me and a perfectly functional ubuntu desktop with sweet berryl...

---

### Post by leoscuro on 2006-10-02
....:-(

no help?

---

