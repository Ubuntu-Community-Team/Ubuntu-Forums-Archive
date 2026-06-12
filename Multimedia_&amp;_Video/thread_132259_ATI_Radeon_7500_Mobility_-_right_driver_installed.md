---
title: "ATI Radeon 7500 Mobility - right driver installed?"
date: 2006-02-17
forum: Multimedia &amp; Video
---

### Post by mogliii on 2006-02-17
Hi everybody.

I have an IBM T40 with ATI Radeon 7500 Mobility.
I installed Kubuntu Breezy (5.10) from scratch. Everything works nice. But what still urges me is: graphic card driver.

The problem is 
a) I dont know if I have the "best" driver for my card installed

here some information:
the glxgears-"itsnotabenchmarkthing" gives me 380 fps.
<glxgears -info> gives the following output:

==========
GL_RENDERER   = Mesa DRI Radeon 20050528 AGP 1x TCL
GL_VERSION    = 1.2 Mesa 6.3.2
GL_VENDOR     = Tungsten Graphics, Inc.
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
===========

So can anyone determine from this information if the driver is Ok?

And if this is "not" OK, heres my second question
b) how to install driver for the Radeon 7500. I already read a lots of different threads, and all I found out is, that there are many HOWTO for ATIs from 8000 upwards, and that the 7500 sucks. And I found 3 different HOWTOs for the 7500.

I am just scared that if I start trying around, I will have screwed up my system in less then an hour.

Thank you very much for any help.[COLOR="Lime"][/COLOR]

---

### Post by Mr Frosti on 2006-02-18
Please let me caution you from experience that the hassle probably isn't worth the upgrade troubles. I know because I have a Radeon 7500 Mobility.

Unless you do games, or very heavy video applications. Even if you manage to get the official ATI drivers, or the DRI drivers installed, they won't fully support all the functions of Xorg such as suspend, or hibernate.

---

### Post by DoorGunner on 2006-02-18
what does fglrxinfo say?

If it says mesa rather than Radeon you havnt finished installing your driver. Please post and we can help

---

### Post by mogliii on 2006-02-18
[QUOTE=DoorGunner]what does fglrxinfo say?[/QUOTE]

Hi,

I am not sure if it is installed on my computer. When I type it into the console, it says "command not found". 

I just performed 
```
apt-cache search fglrxinfo
```
but it didnt give me any results.

So if its not automatically installed with breezy or not content of the repositories, I dont have it.

---

### Post by NeoChaosX on 2006-02-18
What you want to do is run glxinfo, not fglrxinfo. Specifically, do this:

```
glxinfo | grep Mesa
``` and tell us what is produced.

---

### Post by mogliii on 2006-02-18
Ok, here is the result:

```
sizeof(RADEONDRIRec) == 100, devPrivSize 100
OpenGL renderer string: Mesa DRI Radeon 20050528 AGP 1x TCL
OpenGL version string: 1.2 Mesa 6.3.2

```

---

### Post by NeoChaosX on 2006-02-18
Then you have the right driver (DRI driver for older ATi chipsets) installed. If you want to increase performance, then you want to tweak your X server settings a bit. [Here](http://ubuntuforums.org/showthread.php?t=29990&highlight=mobility+radeon+7500) is one thread that has some X tweaking tips.

Also, the command line argument to get an FPS reader for glxgears is trying to tell you something. ;) It's a very piss poor tool for benchmarking; you're better off measuring how your video chip performs in actual games and not a synthetic benchmark like glxgears.

---

### Post by mogliii on 2006-02-18
First of all: Thank you very much to all of you for clearing it up. I am kind of relieved that I dont have to do anything about the video driver.

[QUOTE=NeoChaosX]Also, the command line argument to get an FPS reader for glxgears is trying to tell you something. ;) It's a very piss poor tool for benchmarking; you're better off measuring how your video chip performs in actual games and not a synthetic benchmark like glxgears.[/QUOTE]

Question:
1) What linux program/game (best would be in the Kubuntu Repository) do you suggest to test the 3d speed of my configuration?

2) So DRI Mesa driver are some third party drivers? And I really dont have to care about it never, because for the Radeon 7500 they are not further developed and they will be implemented in all further Kubuntu Versions?
 Its just that I want to collect information und understand my linux.

---

