---
title: "Problems with VLC, Mplayer, and Totem"
date: 2010-03-03
forum: Multimedia Software
---

### Post by InsaneMonkey02 on 2010-03-03
I can't seem to find a multimedia player that works well for me. With VLC, the screen with freeze up and then update itself later to the correct time but it changes to lots of strange colors. With Mplayer, the video will freeze and then catch up later, like VLC does. With Totem, I can't seem to get the subtitles to work correctly. It replaces the subtitles with a font of it's own. I always used Media Player Classic on Windows and it worked really well. When I say "freeze up and catch up later" I mean that the video and subtitles will freeze, but the sound will keep going. The video and subtitles correct themselves a few seconds later.So my questions are...

1. Is there a way to make it so VLC doesn't freeze up and catch up later with strange colors?
2. A way to make VLC and Mplayer not freeze and catch up later?
3. Get Totem to display the correct subtitle font?

I really appreciate any help. Thanks!

---

### Post by Yellow Pasque on 2010-03-03
Could be a problem with your video driver. Can you post output of:
```
glxinfo
```

---

### Post by InsaneMonkey02 on 2010-03-03
> **Temüjin said:**
> Could be a problem with your video driver. Can you post output of:
```
glxinfo
```

Here is the output of glxinfo:

```
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RS400 5954) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.5 Mesa 7.6
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

8 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x63 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x64 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x65 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5a 32 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon

8 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x5b  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5f  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x61  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x62  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

---

### Post by Yellow Pasque on 2010-03-03
Maybe you'll have better luck with updated video drivers from:  [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by clark_b on 2010-03-04
> **Temüjin said:**
> Maybe you'll have better luck with updated video drivers from:  [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

I'd try the drivers from [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") first. If those don't help then try those.

Just add this to your Software Sources-  [B]ppa:ubuntu-x-swat/x-updates
[/B]

---

### Post by InsaneMonkey02 on 2010-03-06
[http://paste.ubuntu.com/389666/](http://paste.ubuntu.com/389666/)

When I did that, I got errors at the end of downloading. It said it failed to fetch them items. I then did sudo apt-get install to try to install them, but it said at the bottom that there was 0 newly-install items, so I don't think I did it correctly. What do I do? Thanks!

---

### Post by InsaneMonkey02 on 2010-03-06
Sorry for double posting but the thread needed bumped. I installed and tried both of the ppa's in the links and neither were able to make it so videos didn't lag, skip, and make strange colors. I know my computer is capable of playing these videos smoothly because using Media Player Classic in Windows does the job perfectly. Here is my /var/log/Xorg.0.log. [http://paste.ubuntu.com/389835/](http://paste.ubuntu.com/389835/) My graphics card is the ATI Radeon Xpress 200. Thanks!

---

### Post by InsaneMonkey02 on 2010-03-15
Does anyone know what to do? Bump.

---

### Post by mc4man on 2010-03-15
Don't have any ati cards (well actually do have an old laptop with the ati 200m card but wouldn't use on any recent ubuntu - too old, not enough ram

Maybe try vlc or mplayer with a different video output - can be set in the preferences or tested from command line

x11 or opengl may be better (apperently opengl is not supported so only x11 maybe 

To test vlc, open vlc from a terminal as such and then try a video

vlc --vout x11
or
vlc --vout opengl

or for either
vlc --vout opengl /path/to/filename

for mplayer, again from terminal

mplayer -vo x11 /path/to/filename
or 
mplayer -vo gl2 /path/to/filename

---

### Post by Yellow Pasque on 2010-03-16
mc4man, just FYI, the open-source radeon drivers don't do opengl video output (only X11/Xv).

---

### Post by mc4man on 2010-03-16
> ...just FYI, the open-source radeon drivers don't do opengl video output

Thanks - haven't used that laptop (or ati) since gutsy or feisty

---

### Post by InsaneMonkey02 on 2010-03-19
> **mc4man said:**
> Don't have any ati cards (well actually do have an old laptop with the ati 200m card but wouldn't use on any recent ubuntu - too old, not enough ram

Maybe try vlc or mplayer with a different video output - can be set in the preferences or tested from command line

x11 or opengl may be better (apperently opengl is not supported so only x11 maybe 

To test vlc, open vlc from a terminal as such and then try a video

vlc --vout x11
or
vlc --vout opengl

or for either
vlc --vout opengl /path/to/filename

for mplayer, again from terminal

mplayer -vo x11 /path/to/filename
or 
mplayer -vo gl2 /path/to/filename

I tried that and VLC ran slower and had more color mess-up's and skips.

---

