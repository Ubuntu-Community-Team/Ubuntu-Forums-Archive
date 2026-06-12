---
title: "ATI: When I turn off my monitor, it wont come back on"
date: 2008-12-04
forum: Multimedia Software
---

### Post by avianbc on 2008-12-04
Long story short: I upgraded to 8.10 and it broke a lot of stuff. I got mad and reinstalled 8.04. I had this problem before and solved it using this link, but its not working now:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Basically, when I manually turn off my monitor using the power button on the front, I try and turn it back on and it doesn't come on. Hardy sends no signal and it cant turn back on. I turn off my monitor every night before sleep so this is really annoying having to control-alt-backspace every morning to get it back on.

I've tried the ATI drivers and the open source fglrx drivers. I've managed to solve all other video problems I've had so far so I am using the open source fglrx driver ATM. If no one knows how to fix it, would you care to assist me with what I need to search for? Is it a fglrx problem? ACPI? Power management? Resume from standby/hibernate work for me but might that be the cause?

Heres some of my info that might help:

> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 1.4 (2.1.7659 Release)


>  glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 1.4 (2.1.7659 Release)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays


> xorg.conf:
Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon 9600"
	Monitor		"Generic Monitor"
	SubSection "Display"
		Depth	24
		Modes		"1440x900"	"1024x768"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Radeon 9600"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"XAANoOffscreenPixmaps"
#	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option "TexturedVideo" "on"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


I've googled for hours so any help is greatly appreciated.

---

### Post by Cracauer on 2008-12-04
I just had this and it was a broken monitor.

Try ALT-F2ing into a text console and if that works try getting back into ALT-Fwhereveryourxserveris to the X11 server.

---

### Post by avianbc on 2008-12-04
Switching consoles does work, but it takes like 15 seconds for the console to load. This is a good workaround for the problem, but its still annoying. Anyone else know what might cause it?

---

### Post by avianbc on 2008-12-04
I was messing around with suspend and hibernate and I discovered that after I go into suspend and then resume, the monitor works correctly and comes on and off when the power button is pressed, but I am plagued with weird greenish graphical glitches all over my system.

I guess this would be a suspend related problem? Anyone know more about suspend/hibernate? Are there flags that are set once I go into suspend that I could single out?

---

### Post by avianbc on 2008-12-04
Bump?

---

### Post by Cracauer on 2008-12-04
What OpenSource firegl drivers, anyway?

As far as I can see, you aren't running any of the xorg/dri/drm stuff.

---

### Post by avianbc on 2008-12-04
Its the one that Envy installed for me. Its the ATI proprietary driver (version 8-6), I believe.

---

### Post by avianbc on 2008-12-05
Bring up my post!

---

### Post by Cracauer on 2008-12-05
Why not try the OpenSource drivers?

---

### Post by avianbc on 2008-12-06
I've tried both drivers and I have the same problem with both of them. The open source one came with a share of other problems in addition to this problem though which is why I am using the one I am currently using.

---

