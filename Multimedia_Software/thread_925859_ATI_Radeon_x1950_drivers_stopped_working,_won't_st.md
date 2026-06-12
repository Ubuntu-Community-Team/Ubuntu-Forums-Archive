---
title: "ATI Radeon x1950 drivers stopped working, won't start again"
date: 2008-09-21
forum: Multimedia Software
---

### Post by rewbs on 2008-09-21
Hi all,

I'm having trouble with the drivers for my ATI Radeon x1950 on Ubuntu 8.04.1.

I switched to Ubuntu a few months ago, and was happily running Gnome+Compiz with great performance. I had installed graphics drivers using Envy-NG. Then a few weeks ago, Ubuntu recommended some updates which I installed (including kernel update 2.6.24-19 - I was previously on 2.6.24-16), and after rebooting, my monitor just displayed "no signal". I tried booting into previous kernel levels, but to no avail.

I eventually got going again by running xfix via failsafe mode. I think this just disabled the graphics drivers, given that:
[LIST]
[*]I just get a white screen if I try to run Gnome+Compiz, presumably because it can't cope without 3d drivers; fortunately I also have kubuntu installed, so I'm using that instead. 
[*]"glxgears -info" displays "GL_RENDERER = Mesa GLX Indirect" and yields terrible FPS.
[*]Video performance is generally aweful.
[/LIST]

Anyway, I finally have a bit of spare time so I'm now trying to get the graphics drivers running again.
I have tried uninstalling and re-installing with Envy-NG, but I just get "no signal" and have to run xfix again.

I have also tried to follow dozens of ATI related suggestions on these forums and others, but haven't got anywhere. The truth is I don't know what I'm doing and don't know how to diagnose the issue properly.


Any help would be greatly appreciated.
I'm dumping some stuff here, let me know if there's any other info I should gather to help understand what's going on.


**lspci | grep ATI**
```

01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
01:00.1 Display controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary) (rev 9a)

```

**Working xorg.conf as restored by xfix:**
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


**xorg.conf that produces "no signal":**
```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Driver          "fglrx"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

```


**glxgears -info**
```

GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.4 (2.1 Mesa 7.0.3-rc2)
GL_VENDOR     = Mesa project: www.mesa3d.org
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_fragment_program GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays 
598 frames in 5.0 seconds = 119.401 FPS
580 frames in 5.1 seconds = 113.353 FPS
580 frames in 5.1 seconds = 112.683 FPS

```

---

### Post by Nettoyer on 2008-09-21
I was having a problem with my drivers.  I tried all the walkthroughs & even used EnvyNG, which all of it led to a whitescreen. This is my conclucion as to how I got them to work.

Step 1: Ok, you goto the ATI Site and download the latest linux driver (in my case, x86_64bit)

Step 2: I opened a terminal and ran the file via sudo sh ./longfilename_x86_64bit.run

Step 3: Follow the terminal style interface.
Step 4: Reboot & win.

I forgot to go into the directory and "Set this to run as a program" which I believe allowed this to work perfectly.  Best of luck!

---

### Post by rewbs on 2008-09-21
Thanks for the suggestion... but no luck - once the driver is installed properly, rebooting just leads to the monitor getting "no signal".

I tried booting to Windows XP. Interestingly, while everything appears to work fine at first, as soon as I try to do anything remotely graphically intensive (e.g. run Google Earth), the system locks up and I get "no signal". So perhaps there's something fundamentally broken about my graphics cards or mother board... :(

---

