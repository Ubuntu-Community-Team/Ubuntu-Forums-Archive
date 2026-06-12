---
title: "openGL is reported to not be running"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by Gangus on 2007-11-05
hi guys, i'm having problems getting openGL to run, and i'm thinking it's to do with the Direct Rendering showing as No or that my glx server is showing as SGI and not nVidia Corporation.

All desktop enhancements are working fine, but i've switched them off to see if it helps to no avail. :'(

here's the output of a glxinfo, hope somebody can help.


gangus@Valgur:~$ glxinfo
name of display: :2.0
display: :2  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8600 GTS/PCI/SSE2
OpenGL version string: 1.2 (2.1.1 NVIDIA 100.14.19)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_program, 
    GL_ARB_fragment_program, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_ATI_texture_mirror_once, GL_IBM_texture_mirrored_repeat, 
    GL_NV_blend_square, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_NV_texture_env_combine4, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by khughitt on 2007-11-05
Hey,

First, what driver are you using? Did you enable the proprietary driver under the restricted drivers manager? What driver is shown as being used under the "screen and graphics card" settings manager?

---

### Post by Gangus on 2007-11-05
I'm using the restricted driver, and it's listed in xorg.conf as nvidia

I'll post the relevant section of xorg.conf


Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600 GTS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"G810-5"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GTS]"
	Monitor		"G810-5"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection


My apologies that i don't yet know how to post into a neat little text box.

EDIT: if i remember rightly, it was nvidia-glx-new that was installed

---

### Post by khughitt on 2007-11-05
I don't have an NVIDIA card, so I don't know exactly how you want to configure your xorg.conf file, but a couple things you could try would be to uninstall and reinstall the driver, and if that doesn't help perhaps using a newer version of the driver via Envy.

Anybody else with an [NVIDIA]("http://albertomilone.com/nvidia_scripts1.html") card have any suggestions?

---

### Post by Gangus on 2007-11-05
neither seems to have worked, getting exactly the same responses that were originally worrying me from running glxinfo

i'm wondering about the line

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

how do i get an output of LIBGL_DEBUG?

---

### Post by khughitt on 2007-11-05
Try:

```
export LIBGL_DEBUG=verbose
```

---

### Post by Gangus on 2007-11-05
that gave no response at all... was it supposed to?

---

### Post by khughitt on 2007-11-05
It should set the environmental variable to "verbose." Check out [http://ubuntuforums.org/showthread.php?t=591717]("http://ubuntuforums.org/showthread.php?t=591717") too, some people who were having similar trouble were able to fix the problem by removing xgl:

```
sudo aptitude remove xserver-xgl
```

You would need to restart X afterwards to see if it helped.

Goodluck!

---

### Post by Gangus on 2007-11-05
That seems to have done it!

thank you very much for your help :)

---

### Post by khughitt on 2007-11-05
No problem! Glad I could help :)

---

