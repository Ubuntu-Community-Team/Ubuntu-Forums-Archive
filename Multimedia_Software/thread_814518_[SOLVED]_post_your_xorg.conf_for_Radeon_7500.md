---
title: "[SOLVED] post your xorg.conf for Radeon 7500"
date: 2008-05-31
forum: Multimedia Software
---

### Post by xfceuser on 2008-05-31
HI, are you able to use accelerated 3D graphics (direct rendering) with ATI Radeon 7500 (mobility).
could you please post your xorg.conf find it at /etc/X11/xorg.conf

output of these two commands will be also helpful:

glxinfo | grep "direct rendering"

and
glxinfo | grep vendor 


these will help me and others to setup own 3D graphics that could not by reading the posts so far.

---

### Post by xfceuser on 2008-06-01
so this means nobody can use 3D acceleration with 7500 ?

---

### Post by xfceuser on 2008-06-01
OK, my situation, 
```
$ glxinfo | grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```
and
```
$ glxinfo | grep vendor 
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org) 
```
here is my xorg.conf
```

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
#	Load		"dri"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection


Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection


Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by Rocket2DMn on 2008-06-01
Try using a generic xorg.conf by running
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE.  The new version of X relies on autodetection more than xorg.conf, so configuration files left from 7.10 sometimes cause problems.  It says you are using the "vesa" driver, which is bad, it should be "ati" or "radeon" (the default xorg.conf won't show the Driver at all, which is OK).
After you have the correct driver running (i.e. 3d rendering works), you can use compiz by following this: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by xfceuser on 2008-06-01
thanks. but still not working:
i run 
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
then restart X and also ubuntu.
 my new xorg.conf 
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	InputDevice	"Synaptics Touchpad"
EndSection

```

there some changes after i did your suggestion, graphics are much slower (like in glxgears frame rate) also like in firefox, when i try to scroll the cpu become 100% and it jumping, seems now there is no hardware acceleration while before there was a bit.

more info: the result of running now
```

LIBGL_DEBUG=verbose, glxinfo

```
 
is

 ```

name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


```

---

### Post by Rocket2DMn on 2008-06-01
Is it running compiz or are you in metacity?  Many people have complained about very slow responsiveness when running compiz, but you should be OK when in metacity
```
metacity --replace
```
Also, in case xserver-xgl is installed, you should remove that
```
sudo apt-get remove xserver-xgl
```
You may need to restart X again.

---

### Post by xfceuser on 2008-06-01
WOOOW , it is working, thanks very much ...

i not yet using compiz, but needed 3D for design and game and maybe compiz and even 2D was so slow in every aspect ...

the trick was to remove xserver-xgl , can you a bit explain what it is about?

:guitar:

---

### Post by Rocket2DMn on 2008-06-01
Hey, you don't need to PM me when you respond, I am subscribed to the thread :)

I don't recall exactly why xserver-xgl causes problems, but I think it conflicts with the rendering provided by certain drivers, including the open source ati drivers.  It's not a problem for people who do fresh installs of Hardy, just those who upgrade from Gutsy.  It may have something to do with the new version of X that Hardy is using.

---

### Post by xfceuser on 2008-06-01
result now
```

$ glxinfo | grep "direct rendering"
direct rendering: Yes

```

```

$ glxinfo | grep "vendor"
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

```

and xorg.conf is the same as the last post.

---

### Post by Rocket2DMn on 2008-06-01
Cool, you can enable Compiz Fusion by following the link in post #4.  Post back if you still have problems.

---

### Post by Zeaon on 2008-06-06
Thank you Rocket2DMn!  

I am a 100% newbie.  I have a ThinkPad T42 with an ATI Radeon 7500.  I installed ubuntu 7.10 on it this morning and would get a back screen on startup.  I used your code below and rebooted and it booted right up into GNOME.

Thank you!

-Z


> **Rocket2DMn said:**
> Try using a generic xorg.conf by running
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE.  The new version of X relies on autodetection more than xorg.conf, so configuration files left from 7.10 sometimes cause problems.  It says you are using the "vesa" driver, which is bad, it should be "ati" or "radeon" (the default xorg.conf won't show the Driver at all, which is OK).
After you have the correct driver running (i.e. 3d rendering works), you can use compiz by following this: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by jefnert on 2008-11-14
I have been trying without any success to get direct rendering working on my thinkpad T30.  When I run glxinfo |grep vendor I get the following:

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

I noticed your OpenGL Vendor string says Tungsten Graphics, Inc.

Do I need to install a different driver?  I currently am running xserver-xorg-video-ati 1:6.8.0-1ubuntu1.

Thanks for any advice you can provide.

---

