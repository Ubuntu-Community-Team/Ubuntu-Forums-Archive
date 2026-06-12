---
title: "X freezes when doing direct rendering"
date: 2006-01-19
forum: Multimedia &amp; Video
---

### Post by PatrickMay16 on 2006-01-19
Hello,

For a while now I've had this problem. X freezes when I try to use direct rendering (like some 3D screensavers, or using Mupen64). When that happens, I can't switch to any virtual consoles or kill X with alt+ctrl+backspace. But strangely, I can still move the mouse pointer around, though that's all I can do. The only way to get out of this situation is to hard reboot.

My video card is an ATI Radeon 9000, and I'm using the free xorg driver.

Here are some outputs that could help.

dmesg | grep agp
> 
[4294702.252000] Linux agpgart interface v0.101 (c) Dave Jones
[4294702.258000] agpgart: Detected AGP bridge 0
[4294702.273000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294724.494000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294724.494000] agpgart: Device is in legacy mode, falling back to 2.x
[4294724.494000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4294724.494000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode


dmesg | grep drm
> 
[4294724.489000] [drm] Initialized drm 1.0.0 20040925
[4294724.493000] [drm] Initialized radeon 1.16.0 20050311 on minor 0: ATI Technologies Inc Radeon RV250 If [Radeon 9000]
[4294724.597000] [drm] Loading R200 Microcode


glxinfo
> 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20041207 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.3.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow


xdriinfo
> 
Screen 0: r200


When I tried using fglrx, I had odd graphical distortion problems. So I'd prefer not to use fglrx. 

In case it helps, here is the contents of my xorg.conf file:
> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9000 Pro (RV250 If)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9000 Pro (RV250 If)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection



I'd really appreciate any help. 
Thanks in advance.

---

### Post by WilliamAnderson on 2006-01-19
Hi Patrick,

I am having what may be the same problem using an ATI Radeon 9550 card.  There seems to be a lot of people having this kind of problem with ATI grphic cards. 

I am using the ATI fglrx driver. See the <a href="http://ubuntuforums.org/showthread.php?t=79787"> thread</a> for a description of what I have tried so far. Some of this might help.

Do you have another computer that you can try to log in to the failing computer via ssh over the network? If so you may find that only X is freezing  and you may be able to kill the x session and be able to log back in. With the fglrx driver; however, killing the X process or anything that will cause X to reset freezes the computer hard. 

Hope this helps, 

William

---

### Post by WilliamAnderson on 2006-01-20
Hi Patrick,

I think I have found a solution for this lockup problem. Go into your computer's BIOS setup and disable AGP Fast writes, save the change, and see if that helps. Let us know if it does.

William

---

### Post by b0r0da on 2006-01-26
I have the same problem with ATI 8500 & Breezy but no AGP Fast Writes option in my BIOS :)

---

### Post by WilliamAnderson on 2006-01-31
Hi B0r0da,

Are you sure? The AGP Fast Writes parameter was located two menus deep within my motherboard's BIOS setup. It was located under “chip settings”, or something like that (I do not want to reboot to find out as my system has now been up trouble free for over 11 days). This setting might be a feature of my Asus motherboard? 

 The other thing to try might be AGP strength, but I do not know exactly what this setting does.

Hope that this helps,

William

---

### Post by PatrickMay16 on 2006-01-31
[QUOTE=WilliamAnderson]Hi Patrick,

I think I have found a solution for this lockup problem. Go into your computer's BIOS setup and disable AGP Fast writes, save the change, and see if that helps. Let us know if it does.

William[/QUOTE]
Hello, William.
First, I would like to say thanks for replying to this thread. 

I entered the BIOS and disabled AGP fast write. I haven't tested things very extensively yet, but I tried out the screensaver which causes the lockup the most (the one called "endgame") and it caused the lockup just like before.
Fortunately, I was able to reboot the computer normally by logging in from my other computer using ssh, like you said before.

Could you try using the "endgame" screensaver and see if it causes the lockup for you, too?

Thanks.
- Patrick

EDIT: I tried testing some things out, and it seems like the lockup still occurs.

---

### Post by PatrickMay16 on 2006-04-26
My friends, feel the pow0r!!!!! For I have found something which seems to have fixed this problem. So far I've done a LOAD of 3D stuff which has run nice and smoothly, and the lockup has not occurred yet. I did a whole load of stuff that would make the lockup occurr almost right away, and it still didn't happen. I'm not entirely sure this has stopped the lockup for good, but it's a definite improvement.

My solution was to add a line to the "Device" section of the xorg.conf file. The line I added is in bold:
```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9000 Pro (RV250 If)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	**Option "AGPMode" "4"**
EndSection

```

If anyone else was having this problem with their ATI card and the free driver, let me know if this helps you.

---

### Post by airdrawndagger on 2006-06-21
I can verify that this also works on an ATI Radeon 9800 Pro.

Edit: It works insofar as it stops certain screen savers from crashing. Certain others continue to do so. But I guess you could logically say it's better than it was.

---

### Post by airdrawndagger on 2006-06-21
I've found a solution that seems to prevent the lockup. I changed the driver to "vesa" instead of "ati". I'm not sure if it adversely affects performance, but it at least stops things from crashing.

---

### Post by mcwitt on 2006-06-28
Hi all,

I too am experiencing this problem with a Radeon 9700 Pro and the fglrx driver. I am relatively new to Linux, but I have had the same issue running WinXP and have verified that it is caused solely by fast writes being enabled; decreasing the AGP speed has no effect for me.

Disabling fast writes in the Windows ATI driver immediately fixed the problem, but it seems there is no easy way to do this in fglrx. Following the instructions in [this thread]("http://www.rage3d.com/board/showthread.php?t=33793288"), I tried to disable FW via the "AGPMask" and "AGPv3Mask" options in my xorg.conf, but to no avail. It seems that these options are deliberately ignored, as is discussed later in the thread.

My motherboard, an Asus P4G8X, has no BIOS setting for fast writes, so my only option is to disable them via the driver.

---

### Post by PatrickMay16 on 2006-06-29
> **mcwitt]Hi all,

I too am experiencing this problem with a Radeon 9700 Pro and the fglrx driver. I am relatively new to Linux, but I have had the same issue running WinXP and have verified that it is caused solely by fast writes being enabled said:**
> this thread[/URL], I tried to disable FW via the "AGPMask" and "AGPv3Mask" options in my xorg.conf, but to no avail. It seems that these options are deliberately ignored, as is discussed later in the thread.

My motherboard, an Asus P4G8X, has no BIOS setting for fast writes, so my only option is to disable them via the driver.
Is there a manpage for the fglrx driver? Try "man fglrx".
Sorry to be going "READ THE MANUALS!!11111", but I found that the manual page for the free-opensource driver helped me a lot in my problem.

Good luck.

---

