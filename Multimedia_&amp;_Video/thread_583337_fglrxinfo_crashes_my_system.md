---
title: "fglrxinfo crashes my system"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by mithbuntu on 2007-10-20
I have been struggling to get my system to run properly after upgrading to 7.10.   My main problems are stemming from a difunctional setup of my ATI card that is resulting in rather strange behavior on my computer.   I have a radeon x1800 card and recently re-installed my drivers using envy.

Right now it seems that any time my computer tries to access any function calls that invoke the use of my graphics card, including the harmless fglrxinfo, I crash and are brought back to the log in screen.  Beryl and compiz are not working and moving windows around my screen is slow and choppy.

Any help is appreciated and I will post any necessary info to help with my issue.

---

### Post by mithbuntu on 2007-10-20
Bump.... still crashing with fglrxinfo.

---

### Post by mithbuntu on 2007-10-20
Upon examinig my syslog I have found this many times:

```

Oct 20 10:36:49 mithbuntu gdm[5393]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Oct 20 10:36:50 mithbuntu kernel: [  105.079564] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Oct 20 10:36:50 mithbuntu kernel: [  105.083201] [fglrx] Maximum main memory to use for locked dma buffers: 2889 MBytes.
Oct 20 10:36:50 mithbuntu kernel: [  105.083219] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0

```


Could the Fatal X error be the problem?  If so, how would I work with it to determine a solution

glxinfo | grep direct results:
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

Okay, Im still pretty new to nix, but I know that i dont want MESA as my renderer.


I can run glxgears but it is VERY slow and choppy (much like ubuntu itself).  FPS were ~100fps.  In 7.04 I was reaching several (6-7000) or so.


glxinfo :
```

drew@mithbuntu:~$ glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.4 (2.1 Mesa 7.0.1))
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
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 16  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by mithbuntu on 2007-10-20
help =(

---

### Post by mithbuntu on 2007-10-21
bump

---

### Post by mithbuntu on 2007-10-22
bump.  still stuck.  will keep trying till i get some help

---

### Post by mithbuntu on 2007-10-23
Alright.   I gave up and reformatted/did a clean install -- everything is working fine now.  Weird, but I am happy now.

It was worth the two hours to get everything back the way I had it.

---

### Post by styxie on 2007-12-17
I have the same problem, is there any other fix than a clean re-install?

---

### Post by Tarmael on 2007-12-17
I know what the problem IS, but not quite how to fix it.

The problem is you don't have the ATi drivers properly installed.

I followed the [http://wiki.cchtml.com](http://wiki.cchtml.com) how-to to install it properly but I'm still having some problems.

If you ever try installing the drivers again try running glxinfo and you'll be surprised, it'll tell you Mesa drivers are in use even if fglrx is written in your xorg.conf.

As I said, follow that wiki, it's the unofficial wiki listed on the ATi site so I trust it.

Cheers,
Basil.

---

### Post by mithbuntu on 2008-02-26
I installed new ATI drivers and this is happening again...  I really don't want to format again.

Anyone know why this might be happening?

glxinfo
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
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


And my xorg.conf (which may be messed up)
```

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us\"
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
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Radeon X1800XT"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Samsung 226bw"
	Option		"DPMS"
	Horizsync	30-90
	Vertrefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon X1800XT"
	Monitor		"Samsung 226bw"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1920x1440"	"1920x1200"	"1680x1050"	"1440x900"	"1280x1024"	"1280x800"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

---

### Post by WFGeppetto on 2008-03-18
I don't think I can help at all, but currently I am very pissed, with a similar, but worse problem.

I ran Envy also.  Screw Envy!  I had everything working well, but atlantis plugin for compiz was very slow, so I thought I'd try to get a better driver installed.  I should have just let good enough alone.

I found a post saying "use envy! its the easy way!" Yeah, right!  The easy way to crash!  I ran it, and now, Ubuntu seems to boot properly, but it never even shows the login screen.  Once the boot processes finish running, I just have a black screen, no graphics at all.

I can boot to recovery mode, but I'm one of those "if it's not in synaptics, I don't know how to remove it properly" guys.  I can sudo, and apt-get all day, and dpkg, and all that, but I don't know what envy changed in my setup, and I don't know how to change it back at a command prompt.

This sux horribly.  I finally had absolutely everything working, and I just wanted to improve my graphics performance, and now I'm screwed.

---

### Post by Tarmael on 2008-03-19
This is in reply to Mythbuntu's previous post.


I've had this a few times.

If when you type

```
fglrxinfo -display :0
```

And it returns something like this:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.1.7412 Release
```

but when you type

```
fglrxinfo -display :1
```

it comes with something to do with the Mesa driver, then you have XGL running.
The easiest way to stop it running is to uninstall it as the new drivers (8.42-ish) onwards use AIGLX instead of XGL.

This is showing the different displays present on the xserver. There won't be anything returned from -display :2 and onwards, cause they don't exist.

Ubuntu uses XGL by default, which you don't want (obviously :P)

Go to Synaptics Package Manager

Search for xgl and uninstall the xserver-xgl (Pretty sure that's what it's called. There are only two results, so the one resembling my wording of it is the one you want.)

Obvious action now, is to restart xserver and then check for the driver to be working by typing any of these:

glxinfo
fglrxinfo
fglrxinfo -display :0

typing fglrxinfo -display :1 should NOW return nothing as there is no second display running, which means AIGLX is now running and XGL is no longer apart of your computer.


I had to work this out the hard way, as it wasn't posted on ANY support forums and no one knew the answer to my heavily asked question.

Now, if don't get the result of what I asked you right at the beginning, then you've wasted time reading this, and I, typing this.

I hope this helps!!!

Bas.

---

