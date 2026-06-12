---
title: "Mouse speed jumping with ATi"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by AquaFox90 on 2006-12-25
With some games of mine (neverwinter nights and Nexuiz) the mouse, once I move out, slows down and speeds up. It keeps happening. Everytime I move it, it slows down and speeds up to its position it's supposed to be.

What's wrong?

All in all ATi is working fine with other games, but I especially enjoy Neverwinter Nights.

---

### Post by Kubunteando on 2006-12-25
I had the same problem when I was using the ATI proprietary drivers.
The version I was using was the same as Ubuntu provides: 8.28.8.

I have noticed that those drivers use a huge amount of CPU even if you are using the Direct Rendering for HW acceleration. And I think probably this is what is interfering the mouse, and sometimes may seem that the game is not so smooth when moving the angle of the camera.

I solved it by installing the Open Source  drivers for MESA 6.5.1 for Ubuntu edgy.
The performance increased. I used:

[www.mesa3d.org](www.mesa3d.org)
dri.freedesktop.org

By the way, what ATI drivers version are you using? What ATI card?
Have you noticed if NeverWinter crashes after 1 hour or so of game playing?
(or the Hard disk starts to be in heavy use and the system gets really slow and unusable?)
That was what was happening to me.

---

### Post by AquaFox90 on 2006-12-26
I remember everytime I run fglrxinfo and see MESA it means I am software rendering. I use ATi Radeon 9200. Are you sure I should shift drivers? Will my games work just as perfectly?

---

### Post by Kubunteando on 2006-12-26
It seems you are in the same situation as me. Check:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

It seems the 8.28.8 are the last drivers ATI is releasing for those cards.

I have tried the following 3D games and they work well for me:
- Enemy Territory
- NeverWinter Nights
- Cube
- Second Life
- Vendetta
- Cube 2 (Sauerbraten). These is not loading all the textures, because I ony have 32MB of Video RAM. I can play but some textures are missing. Still working on this.
- A Tale in the Dessert
- Planetshift
- Nexuiz

I still haven't found a game that does not work better than with the 8.28.8.

I am really happy with these ones.

In my case I change the drivers, not because the mouse, but because NeverWinter Nights crashes after around 1 hour playing, the memory consumption was huge.
Don't you have this problem?

I guess that if you try and you are not happy, you can always come back to fglrx...

You need Mesa 3D, but also the DRI drivers (Direct Rendering) to have 3D HW acceleration.

This is the output I get:

laptop:~/bin$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.1

laptop:~/bin$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL

As you can see Direct Rendering is enabled.
And with "glxgears -printfps" and a resolution of 1400x1050 I get more than 2000 FPS.

I get less CPU consumption, so the games run smother. The games are stable. And now the system does not hang when I shut it down.

If still interested you can follow the guide in:
[http://dri.freedesktop.org/wiki/Building#head-18dc229f35ef85098e2f2d76427eca910221ebcf](http://dri.freedesktop.org/wiki/Building#head-18dc229f35ef85098e2f2d76427eca910221ebcf)

As you can see you need to do some work, and compile from the source some Mesa 3D.
In my case it went really well. If you are using edgy download Mesa 6.5.1 and not the 6.5.2 (if you use 6.5.2 it generally works but not as well as with 6.5.1, since edgy is using 6.5.1)

If you go for the driver migration, I can give you some more tips to increase the performance.

---

### Post by AquaFox90 on 2006-12-27
Can I have those tips to increase performance? And I can't get DRI working.

```

qusai@qusai-pc:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


```

---

### Post by Kubunteando on 2006-12-27
Yes, it seems you don't have yet the DRI drivers working.

Did you compile successfully the DRM libs and MESA 3D 6.5.1?
After compiling it, did you got all the libGL* and the r200_dri.so files?
The files in the mesa/lib/ folder you have to copy as follows:
the libGL* you have to copy them to /usr/lib/
the r200_dri.so you have to copy it to /usr/lib/dri/

You also need to be sure that in the /etc/X11/xorg.org you are not using "fglrx" but "radeon" instead. So in: <Section "Device"> must say: <Driver "radeon"> and not <Driver "fglrx">

I am using Kubuntu (Ubuntu with KDE), and it uses Xorg Xserver. And the configuration file is /etc/X11/xorg.org. So in your Xserver you have to select to use the Driver RADEON instead of the FGLRX.

This is my output for "lsmod | grep -i radeon":
laptop:~/bin$ lsmod | grep -i radeon
radeon                117920  1
drm                    72340  2 radeon

So the "radeon" driver and the "drm" Direct Rendering Manager modules are loaded.

Here you have the output of my xorg.org file:

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
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"dri"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
  	Option     	"AGPMode" 	"4"
	Option 		"AGPSize" "64" # default: 8
	Option 		"RingSize" "8"
	Option 		"BufferSize" "2"
	Option 		"EnablePageFlip" "true"
	Option 		"EnableDepthMoves" "true"
	Option 		"RenderAccel" "true"
#  	Option		"AGPFastWrite" 	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
        Option "AIGLX" "off"
EndSection

Section "Extensions"
	Option "Composite" 	    "false"
	Option "RENDER" 	    "Enable"
#	Option "UseInternalAGPGART" "yes"
#	Option "KernelModuleParm"   "agplock=0;agp_try_unsupported=1"
EndSection


----------------------------------------------------

In the Section Device are the more important ones, related to the AGP bus.
Also you can disable the "AIGLX" in the <Section "ServerFlags">

Once you have the DRI running you can get some more tips to tweak the performance on:

[http://www.gentoo.org/doc/en/dri-howto.xml](http://www.gentoo.org/doc/en/dri-howto.xml)

Check the section Tweak the performance. I think it is specially interesting to enable the Fast Writes if your HW supports it (mine hangs, so I have it disable).

Also you can enable the ATI HyperZ functionality, using the "driconf" utility. You can install it from the Ubuntu repositories. Then execute /usr/bin/driconf and in the Performance tab, say YES to the HyperZ. That boosted my "glxgears -printfps" by more than 50%.

Have a look, and if still does not work. Let me at which stage is the thing (what is the output of your "lsmod | grep -i radeon". All the compilation went ok? Are you using Xorg as Xserver?...)

---

### Post by AquaFox90 on 2006-12-28
r200_dri? I didn't compile that. I compiled radeon_dri.so... I have a 9200 SE. Do I need the r200 :s?

---

### Post by Kubunteando on 2006-12-28
Check:

[http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)

The 9200 model belongs to R200. So you need to compile r200_dri.so.

Also in that link you have more tips about the performance.
I am trying those out as well.

---

### Post by Kubunteando on 2006-12-28
If you still don't get the acceleration, post your /var/log/Xorg.0.log, after a clean boot.
That can give some hints what is the issue.

Once you have the acceleration, your AGP bus speed is x8. So in xorg.org you can congigure the AGPMode as 8.

---

### Post by AquaFox90 on 2006-12-28
I get "input not support" from my monitor when I change from "fglrx" to "radeon" in xorg.conf. Why?

---

### Post by Kubunteando on 2006-12-28
That is usually a mismatch between the settings in the monitor (usually the Refresh Hz) and the driver. You can use the Ubuntu Graphical tool to select the "Radeon" driver and the settings of the monitor. You can play around with the resolution as well. That should clear up that problem.

It seems that Xorg on Kubuntu may be more flexible with those settings.
That is why I have not seen that problem.

I think I am close to the top performance  of the graphic card. I get 2370 FPS with "glxgears -printfps" with a resolution of 1400x1050 and the default window size of "glxgears".
I was getting around 1278 FPS with the 8.28.8 ATI drivers.
I will be trying some new 3D Games.

---

### Post by AquaFox90 on 2006-12-28
I'm glad you're getting better performance. I plan to do so as well.

But this isn't Ubuntu. It's Xorg itself. I didn't even log in to GNOME, so no need to comment about KDE. I'm using XFCE anyway, if you're wondering.

---

### Post by AquaFox90 on 2006-12-28
Maybe it's because I havn't compiled DRM yet and I can't seem to check it out from the git tree.
```

/usr/bin/gitfm: fatal error: `chdir' failed: permission denied.

```

---

### Post by Kubunteando on 2006-12-28
You can check:
[http://www.linuxcompatible.org/thread27341-1.html](http://www.linuxcompatible.org/thread27341-1.html)

maybe you can get some ideas. But I have not seen that problem.

You need to build the libdrm, but I did not need to build the DRM.
With the latest kernel versions, it seems it comes already built.

If you type "lsmod | grep -i radeon", and you see the "radeon" and "drm" modules, then that should be enough, no need to perform the DRM compilation. So the module is loaded, you need to have selected <Driver "radeon"> in xorg.conf.

You can post the file /var/log/Xorg.0.log. That can give some hints.
Specially it can be seen if it loads the r200_dri.so library and the DRI status.

---

### Post by AquaFox90 on 2006-12-28
When I type: sudo dpkg-reconfigure xserver-xorg

I get many drivers to choose from but radeon is not in the list. FGLRX is. Do you know why? Is there any settings in which i have to add :(?

I'm stuck with choosing "ati" for software rendering, or "fglrx" for indirect hardware rendering :(.

---

### Post by Kubunteando on 2006-12-28
You can select "ati". In my case I have the same result as "radeon".
You can check if the xorg.conf shows now <Driver "ati">.

What output do you get for "lsmod | grep -i radeon"?
Post the /var/log/Xorg.0.log file.

---

### Post by AquaFox90 on 2006-12-28
```
qusai@qusai-pc:~$ lsmod | grep -i radeon
qusai@qusai-pc:~$

```

Xorg.0.log
[http://rafb.net/p/5HIxnh46.html](http://rafb.net/p/5HIxnh46.html)

I will try to switch to "ati" now.

---

### Post by AquaFox90 on 2006-12-28
I ran depmod -a and this is what I get for glxinfo:
```

qusai@qusai-pc:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram,
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

and for my Xorg.0.log:
[http://rafb.net/p/LQgAvF86.html](http://rafb.net/p/LQgAvF86.html)

---

### Post by Kubunteando on 2006-12-28
It seems good news. You have already "Direct Render" as "yes".
So you have already HW acceleration.

But according to the Xorg.0.log, there is still some work to be done, to optimize the performance.

Make a backup copy of your current file xorg.conf.
Now check the "Device" section of my xorg.conf I posted earlier.
Add the same parameters on that section. And also add (as I have in mine):
Section "ServerFlags"
        Option "AIGLX" "off"
 
It is important that the "lsmod | grep -i radeon" shows "radeon" and "drm", but I guess it does now since you have Direct Rendering enabled.

In the same "Device" section you can try to see if you are lucky and set "AGPMode" to "8" and enable the "FastWrites", so can do one change at a time, and if the Xserver does not start, revert to the last good configuration.

By the way, another good thing about the MESA DRI driver is that GoogleEarth works with it.
But it does not work with the ATI 8.28.8 driver.

It seems you are quite close now. Even you could give already a try to NeverWinter Nights, just simply after changing the "AGPMode" and see how it goes.

---

### Post by AquaFox90 on 2006-12-28
I still feel it is slow. This is my glxinfo:
```


name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram,
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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

```

---

### Post by AquaFox90 on 2006-12-28
This is ridiculous. I was getting something in lsmod | grep -i radeon. Now that I switched "ati" to "fglrx" it's gone. What the hell is happening. I have to keep running depmod -a? This is a real big hassle and I'm surprised you've gotten this working so easily.

I am really tired and wish to go back to my fglrx, but simply changing "ati" to "fglrx" won't do. I have to reinstall the fglrx drivers.

Now I have to miss the role playing I did in Neverwinter Nights and get that dreaded Windows on my laptop so I can play it.

Thanks for helping.

---

### Post by Kubunteando on 2006-12-28
The "glxinfo" looks good. I get the same. Also the ATI proprietary drivers show "slow" on the visuals in the "glxinfo"

Post your xorg,conf and the Xorg.0.log to see if there are any errors.

You can Install the "driconf" from Ubuntu repositories (you can use your normal package manager). Execute "/usr/bin/driconf" and enable the HyperZ on the performance tab (set it to "yes"). This will boost the performance.

What is the FPS value you get on "glxgears -printfps" (close any other programs to get the highest value)? Better than with ATI drivers? This will give a good hint about the level of your performance.

How about NeverWinter Nights? After installing the MESA DRI I was even able to set the Graphic Quality to "best", enable the grass effects,... Does the mouse work better now?

---

### Post by Kubunteando on 2006-12-28
If you want to go back to fglrx, just reinstall it.
If you just set back the <Driver "fglrx"> the radeon module is no loaded, the fglrx module will be loaded instead, and that is why you don't get anything in "lsmod | grep -i radeon". 

For me it took some investigation, but now is working really nicely.
For sure I am not going back to the ATI 8.28.8 drivers. With those several of my 3D games crash or go choppy after a while. And some applications like googleearth don't even start. 

If you find any better solution,let the community know. So we can enjoy better the gaming.

---

### Post by AquaFox90 on 2006-12-29
dri seems to be disabled again :(.

```
qusai@qusai-pc:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

```
qusai@qusai-pc:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
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
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_logic_op,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_NV_blend_square, GL_NV_point_sprite, GL_NV_texgen_reflection,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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

/var/log/Xorg.0.log:
[http://rafb.net/p/KTrW7Z19.html](http://rafb.net/p/KTrW7Z19.html)

---

### Post by Kubunteando on 2006-12-29
You have to install fglrx, same as you did the first time:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2)

Both ways, using the repositories, or ATI binaries have the same result.

---

### Post by sorry_name_taken_already2 on 2007-01-06
I found this in my xorg.conf hope it helps:confused: 

Section "DRI"
        Mode    0666
EndSection

> **AquaFox90 said:**
> Can I have those tips to increase performance? And I can't get DRI working.

```

qusai@qusai-pc:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


```

Can anyone help me install ATI propriety drivers! I even tried installing XGL, if that helps?! I have read many forums and edited xorg.conf to suit; turned off dri, tried ot load glx and dbe, changed  to fr

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "dbe"
EndSection

Section "Device"
        Identifier      "ATI Radeon 9500"
:evil:         Driver          "gflrx":evil: 
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "DRI"
        Mode    0666
EndSection

#to RUN fglrx disable
Section "Extensions"
        Option      "Composite" "0"
EndSection


This is my Xorg.log
](*,) I reboot with the new xorg.conf and get a xserver error? I should be using XGL and Ati DRIVERS!](*,) 


Dreaded edgy...and also if anyone knows how to set up wireless or driver for IBM t42

Much appreciated newbie since 2005!

---

