---
title: "Graphics Issues with my Acer Laptop w/ Integrated Intel GMA 4500MHD"
date: 2009-02-27
forum: Multimedia Software
---

### Post by Neostar2119 on 2009-02-27
Hey there Ubuntu;

I'm having some issues with my Acer Extensa 4630Z Laptop.

I'm 90% sure the laptop has a Integrated Intel Graphics Media Accelerator 4500MHD card, but my sysinfo is detecting it as a Intel Corp. Mobile 4 Series Chipset Integrated Graphics Controller (rev 07).

Dunno if that's normal behavior, but I know the performance I'm getting out of this machine is definitely below par.

When I run GLX gears, I get an average of 461 FPS. Anything 3D on my desktop is rendered slow, choppy, and very glitched. It's a wonder my screensaver even runs. And if I ever attempt to run a 3D game (such as NWN Linux client or the omvviewer for Second Life) The game is either too glitched to play or just crashes my desktop.

I've tried several compiz and x-server related steps to get things running correctly but nothing seems to be giving me any boost in graphics power and I'm getting to the stage where I feel over my head and have the notion that I'm breaking it more than it was broken to begin with, so I'm looking for some help from those of you more savvy at this than me.

Is there a way I can get my laptop up to speed on it's 3D rendering? Inquiring minds want to know.

Thanks for your time :)

---

### Post by mttman on 2009-02-27
hello, please post the output of ```
glxinfo
```

thank you

---

### Post by wolfen69 on 2009-02-27
.

---

### Post by Neostar2119 on 2009-02-27
Too easy.

```
neostar@DreathusMain:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 20061102 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x53 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

36 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x54  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x55  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x56  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x57  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x58  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x59  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x5a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5b  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5c  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x60  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x62  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x63  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x64  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x65  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x66  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x67  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x68  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x69  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6a  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6b  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6d  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6e  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x70  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x71  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x72  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x73  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x74  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x75  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x76  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x77  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

---

### Post by Neostar2119 on 2009-02-27
> **wolfen69 said:**
> .

```
neostar@DreathusMain:~$ glxgears
2358 frames in 5.0 seconds = 468.615 FPS
2480 frames in 5.0 seconds = 492.943 FPS
2460 frames in 5.0 seconds = 489.216 FPS
2480 frames in 5.0 seconds = 493.629 FPS
2458 frames in 5.0 seconds = 489.201 FPS
2340 frames in 5.0 seconds = 467.449 FPS
^C

```

---

### Post by mttman on 2009-02-27
If you are currently running compiz try going through your ccsm and disableing all your plugins, then add them back in one by one. it's possible that some of the plugins have compatibility issues and are causeing the problem. also it is very likely the game problems can be attributed to running compiz at the same time you are trying to run the game (that is of course if you are running compiz).

something else you could try (this is a more drastic solution, Last resort kind of thing) would be to upgrade to the development drivers for your card and hope that the problem has been fixed. I have done this with my intel card and posted a how to in the forums at [http://ubuntuforums.org/showthread.php?t=1061331]("http://ubuntuforums.org/showthread.php?t=1061331")
Know this if you decide to upgrade to the development drivers, they are unstable and could cause more problems then they provide solutions.

---

### Post by Neostar2119 on 2009-02-28
We're making some progress.


I killed Expo in Compiz, and installed the development drivers, and glxgears now runs without visible glitches, it also reports a small jump in FPS...

```
neostar@DreathusMain:~$ glxgears
2625 frames in 5.0 seconds = 524.962 FPS
2776 frames in 5.0 seconds = 554.762 FPS
2787 frames in 5.0 seconds = 557.264 FPS
2766 frames in 5.0 seconds = 553.169 FPS
2765 frames in 5.0 seconds = 552.980 FPS
^C

```

However, I'm still getting some pretty nasty glitches in other 3D programs. My current test game of choice is Brutal Chess, which is still very choppy and glitched to play, and the omvviewer program for Second Life glitches badly and displays a warning saying my video card is not up to spec.

Maybe it's not, I don't have the exact specs for the card on hand, but I imagine it could push a little more graphics power than it is.

---

### Post by mttman on 2009-03-02
are you trying to run the 3d games at the same time you are running compiz or are you turning compiz off when you run them. typically you need to turn of compiz so that the game can use the full power of your graphics card. to make this easier the compiz team created fusion-icon which allows you to switch between metacity and compiz easily.

---

### Post by Beholder87 on 2010-06-26
Hi, I recently installed Ubuntu 10.04 LTS here. And I have been experiencing a few problems with the video.

When I try to open 3D games like Alien Arena, the screen goes black and it seems that it tries to go back to normal, but it can't... Every time I open the game the same thing happens and I have to restart the computer.

In this machine I don't have the Xorg.conf installed. This is some of my config:

- CPU ULV 8U7300 (64bit) - Laptop / Notebook
- VGA Intel Int. GMA 4500MHD Graphics
- Memory 4Gb

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

```
glxinfo | grep direct
direct rendering: Yes

```

```
sudo lshw -C video
[sudo] password for *****: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:fe400000-fe7fffff memory:d0000000-dfffffff(prefetchable) ioport:dc00(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fe800000-fe8fffff

```

Update: I turned off the Visual Effects and I opened the game again: Alien Arena, then I went to video options and set it to the lowest configuration and then when I started the game, it worked! But when I tried to to set it to the highest quality, the same thing happened and the screen went black again and I had to restart the computer. I think that with the integrated graphics card which I have, it should be able to work with the best quality or at least go without freezing the computer.

Also I can play Warcraft III - Dota-Allstars in this machine, but it seems that the graphics are a little bit slow as well.

Can someone help me?
Thanks

---

