---
title: "nforce nvidia nvidia-glx woes"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by spedsta on 2007-06-12
Hi, just upgraded to Feisty(very impressed at the speed!).
I tried desktop effects , which obviously installed the nvidia-glx drivers using the restricted drivers manager.
After a restart, noticed funny black squarish shapes on the login screen. After login, screen garbage is everywhere , after enabling desktop effects, the screen is totally screwed, everywhere there is unrecognisable imagery , weird stuff . Beryl just crashes, only a hard boot helps.

I uninstalled and went to synaptic and tried installing the nvidia-glx-legacy drivers. I then edited the xorg.conf file to replace "nv" with "nvidia". and restarted X. The logo came up and i thought i was in business. tried to run glxgears but got a error saying no glx loaded at screen 0:0 (sorry dont have the exact error message but it was short two liner). beryl-manager has a similiar message.

I eventually gave up, and have the nv driver running again.

Any ideas? This is driving me insane, before in Dapper evrything worked like a charm , bit slow but worked just fine.

:p

---

### Post by viciouslime on 2007-06-12
What type of card do you have?

---

### Post by spedsta on 2007-06-12
I have an old nforce motherboard, so i think it is a Geforce2 card.

---

### Post by spedsta on 2007-06-12
bump...

---

### Post by spedsta on 2007-06-12
ok , i reverted bvack to the restricted drivers manager , and it installed nvidia-glx.
this are the only drivers that actaully outputs "yes" for >  glxinfo | grep direct
I tried Envy, nvidia-glx-legacy, nvidia-glx-new, a hundred and one changes to my xorg.conf file.
This is the only one which actually enables the desktop effects(compiz). the thing is that it renders garbage all over the place, the effects of the windows are there, they wobble, etc but i cant make out any rendering on the windows. ie. the background and windows are coverd with odd colours and stuff.
The buttons and text arent all visible, until i force a window over it or rollover the button, almost forcing it to refresh.

Its also very buggy, will crash at any given time, and for no particular reason.

Hers is a print of my glxinfo command 

> glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce2 MX/AGP/SSE/3DNOW!
OpenGL version string: 1.5.8 NVIDIA 96.31
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shared_texture_palette, 
    GL_EXT_stencil_wrap, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fence, 
    GL_NV_fog_distance, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_register_combiners, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_SGIS_generate_mipmap, GL_SGIS_multitexture, GL_SGIS_texture_lod, 
    GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x39 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x3a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3d 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x42 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x43 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x44 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x45 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x46 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x47 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x48 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x49 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x4a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x4b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x4c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x4d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x4e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x4f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x50 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None

and here is my xorg.conf file

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildd@rothera)  Thu Jan  5 15:32:31 UTC 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	28.0	-	51.0
	Vertrefresh	43.0	-	60.0
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection


I at first thought i was loading the wrong driver, cause im running a Geforce card, it an onboard card running on a nforce motherboard. But since this restricted driver is actaullt the only one that works, to some degree. I think its more a config problem than a hardware driver one.

Please if anyone out here can help, show me the way  :D

---

### Post by spedsta on 2007-06-12
nobody seems to be replying, anyhow, this might help somewhat,
this is a print out of my /var/log/Xorg.0.log

> 
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux wells 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 12 23:47:40 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01a4 card 0000,0000 rev b2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01ac card 10de,0c11 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ad card 10de,0c11 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01aa card 10de,0c11 rev b2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,01b2 card 10de,0c11 rev c3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,01b4 card 10de,0c11 rev c1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,01c2 card 10de,0c11 rev c3 class 0c,03,10 hdr 00
(II) PCI: 00:03:0: chip 10de,01c2 card 10de,0c11 rev c3 class 0c,03,10 hdr 00
(II) PCI: 00:05:0: chip 10de,01b0 card 1043,0c11 rev c2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,01b1 card 1043,8384 rev c2 class 04,01,00 hdr 80
(II) PCI: 00:08:0: chip 10de,01b8 card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,01bc card 10de,0c11 rev c3 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01b7 card 0000,0000 rev b2 class 06,04,00 hdr 01
(II) PCI: 01:08:0: chip 10ec,8139 card 3030,5032 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 10de,01a0 card 10de,0c11 rev b1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xac800000 - 0xacffffff (0x800000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbff00000 - 0xbfffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xab000000 - 0xac7fffff (0x1800000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xaff00000 - 0xbfefffff (0x10000000) MX[B]
(--) PCI:*(2:0:0) nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] rev 177, Mem @ 0xab000000/24, 0xb0000000/27, BIOS @ 0xafff0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xdfffffff to 0xbfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xac800000 - 0xac8000ff (0x100) MX[B]
	[1] -1	0	0xad000000 - 0xad000fff (0x1000) MX[B]
	[2] -1	0	0xad800000 - 0xad87ffff (0x80000) MX[B]
	[3] -1	0	0xae800000 - 0xae800fff (0x1000) MX[B]
	[4] -1	0	0xaf000000 - 0xaf000fff (0x1000) MX[B]
	[5] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[6] -1	0	0xafff0000 - 0xafffffff (0x10000) MX[B](B)
	[7] -1	0	0xb0000000 - 0xb7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xab000000 - 0xabffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[12] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[13] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[14] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[15] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xac800000 - 0xac8000ff (0x100) MX[B]
	[1] -1	0	0xad000000 - 0xad000fff (0x1000) MX[B]
	[2] -1	0	0xad800000 - 0xad87ffff (0x80000) MX[B]
	[3] -1	0	0xae800000 - 0xae800fff (0x1000) MX[B]
	[4] -1	0	0xaf000000 - 0xaf000fff (0x1000) MX[B]
	[5] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[6] -1	0	0xafff0000 - 0xafffffff (0x10000) MX[B](B)
	[7] -1	0	0xb0000000 - 0xb7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xab000000 - 0xabffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[12] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[13] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[14] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[15] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xac800000 - 0xac8000ff (0x100) MX[B]
	[5] -1	0	0xad000000 - 0xad000fff (0x1000) MX[B]
	[6] -1	0	0xad800000 - 0xad87ffff (0x80000) MX[B]
	[7] -1	0	0xae800000 - 0xae800fff (0x1000) MX[B]
	[8] -1	0	0xaf000000 - 0xaf000fff (0x1000) MX[B]
	[9] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[10] -1	0	0xafff0000 - 0xafffffff (0x10000) MX[B](B)
	[11] -1	0	0xb0000000 - 0xb7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xab000000 - 0xabffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[18] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[19] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[20] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[21] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xac800000 - 0xac8000ff (0x100) MX[B]
	[5] -1	0	0xad000000 - 0xad000fff (0x1000) MX[B]
	[6] -1	0	0xad800000 - 0xad87ffff (0x80000) MX[B]
	[7] -1	0	0xae800000 - 0xae800fff (0x1000) MX[B]
	[8] -1	0	0xaf000000 - 0xaf000fff (0x1000) MX[B]
	[9] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[10] -1	0	0xafff0000 - 0xafffffff (0x10000) MX[B](B)
	[11] -1	0	0xb0000000 - 0xb7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xab000000 - 0xabffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[18] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[19] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[20] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[21] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xac800000 - 0xac8000ff (0x100) MX[B]
	[5] -1	0	0xad000000 - 0xad000fff (0x1000) MX[B]
	[6] -1	0	0xad800000 - 0xad87ffff (0x80000) MX[B]
	[7] -1	0	0xae800000 - 0xae800fff (0x1000) MX[B]
	[8] -1	0	0xaf000000 - 0xaf000fff (0x1000) MX[B]
	[9] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[10] -1	0	0xafff0000 - 0xafffffff (0x10000) MX[B](B)
	[11] -1	0	0xb0000000 - 0xb7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xab000000 - 0xabffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[21] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[22] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[23] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[24] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "RenderAccel" "True"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "True"
(**) NVIDIA(0): Option "TripleBuffer" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce2 Integrated GPU at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 03.1a.01.03.02
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce2 Integrated GPU at
(--) NVIDIA(0):     PCI:2:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(0): Samsung SyncMaster (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): Insufficient memory bandwidth for MetaMode "800x512";
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): No valid modes for "800x512"; removing.
(--) NVIDIA(0): DPI set to (101, 108); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xb0000000 - 0xb7ffffff (0x8000000) MX[B]
	[1] 0	0	0xab000000 - 0xabffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xac800000 - 0xac8000ff (0x100) MX[B]
	[7] -1	0	0xad000000 - 0xad000fff (0x1000) MX[B]
	[8] -1	0	0xad800000 - 0xad87ffff (0x80000) MX[B]
	[9] -1	0	0xae800000 - 0xae800fff (0x1000) MX[B]
	[10] -1	0	0xaf000000 - 0xaf000fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[12] -1	0	0xafff0000 - 0xafffffff (0x10000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xb7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xab000000 - 0xabffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[23] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[24] -1	0	0x00005100 - 0x0000511f (0x20) IX[B]
	[25] -1	0	0x00005500 - 0x0000550f (0x10) IX[B]
	[26] -1	0	0x00005000 - 0x0000500f (0x10) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(**) NVIDIA(0): Option "BackingStore" "True"
(**) NVIDIA(0): Backing store enabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(WW) NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
(WW) NVIDIA(0):     back to legacy PCI mode.
(II) NVIDIA(0): Setting mode "1024x768_70"
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***

---

### Post by bapoumba on 2007-06-13
Thread moved to "Multimedia & Video", as requested.

---

### Post by spedsta on 2007-06-13
thanks for moving it!

Hi , i tried installing via Envy but same thing, after reboot, i might get to log in , after which i get weird stuff on my desktop, like refreshes not happening, text disappearing, buttons disappearing then appearing later.

I tried installing, uninstalling, clean up after install, nothing seems to work, anybody got any sort of clue, I can only deduce that the nvidia-glx drivers are the correct ones installed but my xorg.conf file needs to be edited correctly to use the driver.

If its any help, before i ran the drivers no problem before as well as beryl and composite, that was when i was running dapper.

Anyone??? ;)

---

### Post by Bruegger on 2007-06-13
Spedsta,
I have the exact on-board graphics card and have faced my share of problems installing the nvidia-glx drivers. So i can understand exactly your frustration.
I am using 9639 drivers and have a usable screen with minor glitches.Havent tried beryl on feisty yet.

Try to remove any instances of nvidia-glx-new and nvidia-glx-legacy from /lib/linux-restricted-modules/.
Then download the 9639 drivers or 9631 drivers from the nvidia site and run the nvidia- installer to install the drivers. Do this in the terminal( close your gdm session) and you should be on.
I have posted my xorg.conf on tseliots thread on installing nvidia drivers on feisty fawn.
Will send you detailed address of my post on it once i reach home.

If you need any detailed help let me know.

Cheers!

---

### Post by spedsta on 2007-06-13
thanks for the reply, 

ok, i will do this during lunchtime, so will post back in about hours time.
Once agin thanks for the reply, for a moment there i thought i was in this all alone :p

---

### Post by spedsta on 2007-06-13
Bruegger,
I think i totally screwed my install, well almost. I followed the instructions from this howto:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty]("http://doc.gwos.org/index.php/Latest_nvidia_feisty")
I did a 
> dpkg-reconfigure -phigh xserver-xorg
I answered with the default answers each time and carried on.

and then proceeded to install the 9639 drivers which seemed to go well.
I rebooted just to be met by command line, i thought if i chan ge the xorg.conf file from "nvidia" to "nv" all will be cool, it wasnt :(

I then panicked and installed the nvidia-glx and nvidia-xconfig packages,and finally a > startx
I could hear my login but a monitor message said something about the vertical refresh rate was out of sync. this isnt the exact message but this was a monitor message.

Seems i messed up with the> dpkg-reconfigure -phigh xserver-xorg .

Anyone know how to get back without a fresh install???

---

### Post by Bruegger on 2007-06-14
Spedsta,
Are you able to log in terminal mode or your monitor is not starting at all??
If you can log in terminal mode, you can try to change your vertical refresh rate to the correct values by editing your xorg.cong file or through dpkg-reconfigure xserver-xorg.
You can know these values from either your monitor manual or if you dont have one ,you can google through a friends pc and search for the horizantal and vertical refresh rates values for your specific model.

If your monitor can be reset to default values through their console button or menu button , that should set you on too.

Dont panic. You are almost there.

Cheers!

---

