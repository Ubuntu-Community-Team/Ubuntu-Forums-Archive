---
title: "direct rendering turning on and off"
date: 2008-05-10
forum: Multimedia Software
---

### Post by Dragonfi on 2008-05-10
I have a Radeon 9200 video card , and using the xorg drivers ,because my card is too old for the other alternatives.
And the following strange thing happening: 
at reboot the direct rendering randomly turns on or off and I can't find the reason behind this. 

I have a dual boot WinXP/ Ubuntu64 install, and my card isn1t work flawlwessly under WinXP with the latest drivers from Ati, can it be hardware related or some problem with the setup files ?

I tried reinstalling the drivers adn that most of the time solves the problem ( although maybe it's only because I need to restart after it).
glxinfo output when working:
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 8x TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x65 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by ajmorris on 2008-05-11
hi there, 
can you please post the output of:
```
less /etc/X11/xorg.conf
```
and
```
sudo update-alternatives --config gl_conf
```

AJ

---

### Post by Dragonfi on 2008-05-12
this is my xorg.conf:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"hu"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

output of sudo update-alternatives --config gl_conf
```
nincs kiválasztás erre: gl_conf. (  translated as: "No alternatives for gl_conf")
``` 
and if needed I can now show the output of glx_info when not working( I saved it to a file).

---

### Post by Dragonfi on 2008-05-19
comeon sombody help me, it's not serious but annoying..

---

### Post by N.N. on 2008-05-19
I'm not very knowledgeable about this subject, but your xorg.conf file looks conspicuously generic. It doesn't even mention that you have an ATI graphics card, nor does it specify which driver to use for your graphics card.

Try specifying the name of the driver manually: First backup your current /etc/X11/xorg.conf file: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` Then issue the following command to edit the /etc/X11/xorg.conf file: ```
sudo gedit /etc/X11/xorg.conf
``` Under the "Device" section add the following: ```
	Driver	"fglrx"
``` after the "identifier" line. Then save and press CTRL+ALT+BACKSPACE to see if things are still working.

If things go awry, you can just revert to the previous version of /etc/X11/xorg.conf by issuing the following command: ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by russo.mic on 2008-05-19
> **N.N. said:**
> I'm not very knowledgeable about this subject, but your xorg.conf file looks conspicuously generic. It doesn't even mention that you have an ATI graphics card, nor does it specify which driver to use for your graphics card.

Try specifying the name of the driver manually: First backup your current /etc/X11/xorg.conf file: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` Then issue the following command to edit the /etc/X11/xorg.conf file: ```
sudo gedit /etc/X11/xorg.conf
``` Under the "Device" section add the following: ```
	Driver	"fglrx"
``` after the "identifier" line. Then save and press CTRL+ALT+BACKSPACE to see if things are still working.

If things go awry, you can just revert to the previous version of /etc/X11/xorg.conf by issuing the following command: ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Just pull a 
sudo aticonfig --initial 

from the command line.  if you've got the fglrx driver installed correctly (which right now you DON'T, looking at your xorg.conf), it will setup xorg.conf for you.

Russo

---

### Post by Dragonfi on 2008-05-20
the fglrx drivrs does not support the Radeon 9200 card , it's only from 9600 and up..

So I'm using the xorg-video-ati drivers ,since it's the only driver that works and I know of.

The strange thing is despite this "Default" settings it works perfectly, the other day when I turn on the comp, it didn't.( and I can see the difference in glxinfo.)

---

### Post by Dragonfi on 2008-08-21
Maybe I shoudl start a new topic instead, but I find out something new( yes it's quite a time), I have found that in /var/log/Xorg.0.log, when it is not working it complains about "agpgart sould be loaded [before ... ]", this time it's working and the error does not shows up in the lo file.
I'm not entireley sure what should I do, and I don't want to screw up my system.

---

