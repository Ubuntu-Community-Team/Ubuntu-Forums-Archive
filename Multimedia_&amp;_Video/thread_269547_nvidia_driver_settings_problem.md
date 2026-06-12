---
title: "nvidia driver settings problem"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by bored4 on 2006-10-01
im wondering why i dont have anything settings being displayed. i cant do anything but check and uncheck those few boxes.  what happen to my nvidia settings manager??? plz help if anyone knows why its like this

---

### Post by tseliot on 2006-10-02
post the output of this command:
```
glxinfo
```

---

### Post by wheezart on 2006-10-07
OK, i have the same problem, *nvidia-settings* gives me only the nvidia-settings configuration tab, no actual driver settings to change... What should i do? Here's the dump from 

```
gnu@gnu-desktop:~$ glxinfo
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
OpenGL renderer string: GeForce4 MX 440/AGP/SSE/3DNOW!
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

```

---

### Post by tseliot on 2006-10-07
Do you use XGL?

---

### Post by CostasX2 on 2006-10-07
Open xorg.conf (/etc/X11/xorg.conf) and check if the Driver entry under the section "Device" is set to "nvidia" and not "nv".

---

### Post by Bear Knuckle on 2006-10-25
> **tseliot said:**
> Do you use XGL?
I am having the same problem as the original poster and yes, I am using xgl. I am pretty sure it has something to do with it, so anyone knows how to enable nvidia-settings with using xgl?

---

### Post by tseliot on 2006-10-25
Try asking here (or use the search function there):
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by seanUSXIII on 2006-11-09
nvidia-settings doesn't work under XGL. I don't recall why, but when I switched to the new Nvidia drivers and dumped XGL (but not beryl, still using that :) ), the settings returned.

---

