---
title: "Horrible Opengl performance"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by Staesys on 2006-06-17
I have the same 3D app installed on both kubuntu and windows xp (dual boot), and in windows xp I get smooth frame rates and good performance. In kubuntu, I get speed ups and slow downs, inconsistent frame rates and generally poor performance.

My card is an ATI Radeon 9250 with 256MB RAM, system RAM is 256MB and I have a 2 GHz Celeron processor. In windows xp I'm using the latest catalyst driver and in kubuntu, I'm running fglrx. Here's some info:

GLXINFO
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_ATI_element_array,
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object,
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3,
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
```

XORG.CONF
```

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

  # path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "glx"
	Load  "dbe"
	Load  "v4l"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	ModelName    "Custom 1"
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1152x768@54" 65.0 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
	ModeLine     "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
EndSection

Section "Monitor"
 # 
	Identifier   "monitor1"
	Gamma        1
EndSection

Section "Monitor"
 # 
	Identifier   "monitor2"
	Gamma        1
EndSection

Section "Device"
	Identifier  "ATI Radeon 9250"
	Driver      "fglrx"
	BoardName   "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:11:0"
	VideoRAM    262144
EndSection

Section "Device"
 # 
	Identifier  "device1"
	Driver      "i810"
	VendorName  "Intel"
	BoardName   "Intel 845"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
 # 
	Identifier  "device2"
	Driver      "fglrx"
	BoardName   "ati"
	BusID       "PCI:1:11:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Radeon 9250"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Virtual   1280 854
		Depth     24
		Modes    "1024x768@60" "1152x768@54" "800x600@60" "1280x854" "800x600@56"
	EndSubSection
EndSection

Section "Screen"
 # 
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
EndSection

Section "Screen"
 # 
	Identifier "screen2"
	Device     "device2"
	Monitor    "monitor2"
	DefaultDepth     24
EndSection

Section "DRI"
	Mode         0666
EndSection
```

---

### Post by Staesys on 2006-06-29
Apparently noone has anything to contribute.

Here is my glxgears fps in case anyone is curious

```
paul@ubuntu:~$ glxgears -printfps
6710 frames in 5.0 seconds = 1341.908 FPS
6929 frames in 5.0 seconds = 1385.782 FPS
6969 frames in 5.0 seconds = 1393.765 FPS
6962 frames in 5.0 seconds = 1392.360 FPS
6968 frames in 5.0 seconds = 1393.440 FPS
```

Any help would be vastly appreciated!

---

### Post by David Valentine on 2006-06-30
I'm using Ubuntu (gnome), and having the same problem.  

It appears that I've installed everything correctly:  > $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200 Series Generic
OpenGL version string: 2.0.5879 (8.26.18)
and> $ glxinfo | grep direct
direct rendering: Yes
yet my 3d performance is terrible at full screen (e.g. screensaver), especially compared with how it was under Breezy.
> $ glxgears -printfps
244 frames in 5.0 seconds = 48.607 FPS
244 frames in 5.0 seconds = 48.645 FPS
243 frames in 5.0 seconds = 48.472 FPS
234 frames in 6.0 seconds = 39.313 FPS
203 frames in 5.0 seconds = 40.459 FPS
I'm using fglrx v. 8.26.18

---

### Post by hygraed on 2006-07-09
From what I've read elsewhere, the problem lies with your server glx string being set to SGI. However, I haven't the slightest clue what it means or how to change it.

---

### Post by tommohawk on 2006-07-09
> **David Valentine said:**
> 
I'm using fglrx v. 8.26.18

Your problem is that you are using the 8.26.18 drivers with an Xpress200M card.

There are known problems with these drivers and this card - see the Ubuntu Wiki (Dapper Installation Guide) and it clearly states there are issues.

The best way to solve your problem is to revert to the 8.24.8 drivers.

```
5731 frames in 5.0 seconds = 1146.121 FPS
6285 frames in 5.0 seconds = 1256.950 FPS
6339 frames in 5.0 seconds = 1267.717 FPS
6371 frames in 5.0 seconds = 1274.109 FPS

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)


```
You can get it running with 8.26.18 but you will always have problems. :cool:

---

### Post by jazzgossen on 2006-07-09
Try adding ```
Option "RenderAccel" "true"
``` to the Device section of your xorg.conf. I use an nVidia card, but it worked for me.

---

### Post by David Valentine on 2006-07-11
Thanks for the suggestions.  I've downgraded to fglrx ver. 8.24.8 using the instructions for Method 2 at [the Wiki page]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") and added the renderaccel option to xorg.conf.  Thus I get> $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200 Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)
and> $ glxinfo | grep direct
direct rendering: Yesbut still my OpenGL performance is terrible (reported at full screen):> $ glxgears -printfps
246 frames in 5.0 seconds = 49.110 FPS
247 frames in 5.0 seconds = 49.318 FPS
247 frames in 5.0 seconds = 49.320 FPS
247 frames in 5.0 seconds = 49.288 FPS
247 frames in 5.0 seconds = 49.311 FPS
What am I doing wrong?

---

### Post by David Valentine on 2006-07-15
Just by way of comparison, here's what I get on an nvidia card built in a much older motherboard (also full screen):
```
~$ glxgears -printfps
736 frames in 5.0 seconds = 147.153 FPS
735 frames in 5.0 seconds = 146.934 FPS
734 frames in 5.0 seconds = 146.767 FPS
746 frames in 5.0 seconds = 149.170 FPS
735 frames in 5.0 seconds = 146.967 FPS
735 frames in 5.0 seconds = 146.971 FPS
```My ATI Xpress 200 card should do at least as well as that, but instead it's 3x slower.  Ideas?

---

