---
title: "Gutsy still without 3D support - ATI"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by Jerzya on 2007-12-24
I have Radeon 9550 (ATI) an I am still getting 
```
jerzy@jerzy-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```
under Gutsy.
I tried everything. Yes, ENVY too and [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide). I've lost any hope. 
EDIT: I DO NOT have installed  xserver-xgl and  xserver-xorg-video-all.

**xorg:**
```
Section "Module"
	Load  "dri"
	Load  "v4l"
	Load  "glx"
EndSection
```
```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection
```
```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection
```

**LIBGL_DEBUG=verbose glxinfo**
```
jerzy@jerzy-desktop:~$ LIBGL_DEBUG=verbose glxinfoname of display: :0.0
libGL error: XF86DRIQueryDirectRenderingCapable returned false
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
```

**/etc/default/linux-restricted-modules-common**
```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="fglrx"
```


PLEASE help, i'm begging you :)
George

---

### Post by Jerzya on 2007-12-25
Bump!

---

### Post by peter07 on 2007-12-27
The same problem with the newest ATI drivers and x200 :/

 HELP!!!!

---

### Post by terminal on 2007-12-27
Ok here are few instructions i can give here . 
1) Follow complete guide over here .
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Here's my xorg.conf if anybody is interested . I do not load glx module  and also have composite disabled  still my compiz runs great .

Btq mine is Radeon HD2600 Pro , it doesnt work with open source radeon driver and the fglrx in ubuntu was also not of any help so compiling driver was only thing that worked for me . I still have video flickering problem though .



> 
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
#Section "Monitor"
#	Identifier   "aticonfig-Monitor[0]"
#	Option	    "VendorName" "ATI Proprietary Driver"
#	Option	    "ModelName" "Generic Autodetecting Monitor"
#	Option	    "DPMS" "true"
#EndSection
#Section "Device"
#	Identifier  "ATI Technologies Inc ATI Default Card"
#	Driver      "vesa"
#	BusID       "PCI:3:0:0"
#EndSection
#Section "Screen"
#	Identifier "aticonfig-Screen[0]"
#	Device     "aticonfig-Device[0]"
#	Monitor    "aticonfig-Monitor[0]"
#	DefaultDepth     24
#	SubSection "Display"
#		Viewport   0 0
#		Depth     24
#	EndSubSection
#EndSection

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "On"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "S/M 550v"
	HorizSync    28.0 - 49.0
	VertRefresh  43.0 - 72.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option "XaaNoOffscreenPixmaps"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "S/M 550v"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

#Section "Extensions"
#	Option	    "Composite" "Enable"
#EndSection


---

### Post by Jerzya on 2007-12-27
I HAVE already followed these instructions - and still not warking.

---

### Post by Drikus on 2007-12-27
Got also an HD2600PRO and needed the envy 7.1/ 8.443 drivers to get things going. Had it installed correctly once but somehow things went wrong.. glxinfo shows direct rendering is not enabled and firing glxgears crashes the server. Had it working before. I  saw glxgears flying at 4500FPS or something. But now on the second screen I seems to have mesa again. 
  
```
:~$ fglrxinfo -display :0 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 Pro
OpenGL version string: 2.1.7170 Release

:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)


```

Screen 0 is usable though, compiz enabled etc. vids are a bit choppy. 

@ Jerzya. Could you post the output of fglrxinfo -display :0 and fglrxinfo -display :1 and ls -la /usr/lib/* | grep libGL to compare the output. 

TIA

---

### Post by xeth_delta on 2007-12-27
What does a simple "glxinfo | grep -i direct" and "glxinfo | grep -i open" return?

---

### Post by Yellow Pasque on 2007-12-27
Here's my xorg.conf from when I still used fglrx (I've since moved to radeonHD and am just waiting for AMD to release the specs this week so that the open-source community can build a good driver):

[http://ubuntuforums.org/showpost.php?p=3720763&postcount=93](http://ubuntuforums.org/showpost.php?p=3720763&postcount=93)

Notice the DRI section at the end. Make sure you have that so that non-root processes have permissions for direct rendering.

---

### Post by Drikus on 2007-12-27
not sure to whom you are referring to but

[CODE ]
~$ glxinfo | grep -i direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

~$ glxinfo | grep -i open
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
OpenGL extensions:  [/CODE]

just for reference my xorg.conf 
```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        Screen      1  "aticonfig-Screen[1]" Above "aticonfig-Screen[0]"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "fglrx"
        Load            "dbe"
        Load            "extmod"
        Load            "fbdevhw"
        Load            "glx"
        Load            "record"
        Load            "freetype"
        Load            "type1"
        Load            "dri"
        Load            "i2c"
        Load            "vbe"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "Off"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"

        #  modeline  "1280x1024@60"  108.00 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        Identifier   "aticonfig-Monitor[0]"
        VendorName   "Acer"
        ModelName    "Acer AL1931"
        HorizSync    24.0 - 80.0
        VertRefresh  56.0 - 75.0
        Gamma        1
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        VendorName   "Plug 'n' Play"
        ModelName    "Plug 'n' Play"
        Gamma        1
        ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
        ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
        ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
        ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
        ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
        ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
        ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
        ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
        ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
        ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
        ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
        ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
        ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        BoardName   "ati"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "XaaNoOffscreenPixmaps"  
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BoardName   "ati"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Virtual   1280 1024
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "640x480@60" "640x480@72" "640x480@75" "800x600@56" "800x600@72" "800x600@75" "800x600@60" "832x624@75" "1024x768@75" "1024x768@70" "1024x768@60" "1280x960@60" "1280x1024@60"
        EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

Section "DRI"
        Group   0
        Mode    0666
EndSection

```

But good to hear there is an radeonHD project going on. Didn't know that. Gonna check that out. ;-)

---

### Post by xeth_delta on 2007-12-27
Drikus, the output seems to indicate you don't have direct rendering enabled. Is giving the Open Source drive a try an option for you? To do so, first back-up your /etc/X11/xorg.conf file and then change fglrx to radeon. That way we would be able to trace the problem to how the proprietary driver is configured. If it does not work, replace /etc/X11/xorg.conf with the backup you just made.

Xeth

---

### Post by Drikus on 2007-12-27
Yeah, i will give to opensource driver a try. All that binary stuff and generating conf scripts with ati-config is not my kind of thing. I like to see what i'm doing and using. I will look into radeonHD tomorrow. And from reading up I see Luc Verhaegen is involved with that driver, hopefully we will not see another spin-off radeon opensource driver in the future... I've seen him doing that before... ;-)

---

### Post by Jerzya on 2007-12-28
Wow, I didn't suspected so many people will answer.
Posting requested comands results in a minute..
```
jerzy@jerzy:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

jerzy@jerzy:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

jerzy@jerzy:~$ fglrxinfo -display :1
Error: unable to open display :1
jerzy@jerzy:~$ ls -la /usr/lib/* | grep libGL
-rw-r--r--  1 root root   485888 2007-12-28 06:10 /usr/lib/FGL.renamed.libGL.so.1.2
lrwxrwxrwx  1 root root       16 2007-12-28 02:11 /usr/lib/libGLEW.so.1.4 -> libGLEW.so.1.4.0
-rw-r--r--  1 root root   220932 2007-07-09 19:56 /usr/lib/libGLEW.so.1.4.0
lrwxrwxrwx  1 root root       26 2007-12-28 07:02 /usr/lib/libGL.so -> /usr/lib/xorg/libGL.so.1.2
lrwxrwxrwx  1 root root       12 2007-12-28 07:22 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rw-r--r--  1 root root   485888 2007-12-28 07:21 /usr/lib/libGL.so.1.2
lrwxrwxrwx  1 root root       20 2007-12-28 02:11 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.070001
-rw-r--r--  1 root root   533352 2007-10-13 02:38 /usr/lib/libGLU.so.1.3.070001
-rw-r--r--   1 root root 386556 2007-10-13 02:38 libGL.so.1.2.xlibmesa
-rw-r--r--   1 root root      0 2007-12-28 06:18 FGL.renamed.libGL.so.1.2
lrwxrwxrwx   1 root root     26 2007-12-28 07:02 libGL.so -> /usr/lib/xorg/libGL.so.1.2
lrwxrwxrwx   1 root root     26 2007-12-28 07:02 libGL.so.1 -> /usr/lib/xorg/libGL.so.1.2
-rw-r--r--   1 root root 601405 2007-12-28 07:02 libGL.so.1.2
jerzy@jerzy:~$ glxinfo | grep -i direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
jerzy@jerzy:~$ glxinfo | grep -i open
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
jerzy@jerzy:~$ 

```

---

### Post by silviur on 2007-12-28
Jerzya, i have also the 9550. Desktop effects work for me only with Restricted drivers and XGL installed by me.

---

### Post by Jerzya on 2007-12-28
We will se.. I don't think that xgl will change anything..
reboot.
**EDIT**:xgl installed, everything is hm.. "too slow". Strange, my ubuntu uses FGLRX but direct rendering by MESA. WHY?

---

### Post by Praill on 2007-12-29
You dont have DR because the running xgl process disables it
```
sudo apt-get remove xserver-xgl
```
then reboot
If you still dont have 3d support then download and run alberto milone's script: [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
It always works for me.

---

### Post by Drikus on 2008-01-08
Switched to radeonhd driver for a while but it's still in it's early development. No 2d and 3d accel and xrandr was giving me problems. So switched back to 7.12 ati driver fglrx again. Installed envy and removed the previous fglrx driver with envy, reinstalled Mesa again and i think the latter iis the key for succes fixing up broken links in /usr/lib/libGL*. Iinstalled gflrx 7.12 again with envy. Direct Rendering is enabled again !!

---

