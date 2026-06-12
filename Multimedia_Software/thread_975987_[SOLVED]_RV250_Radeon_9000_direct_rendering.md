---
title: "[SOLVED] RV250 Radeon 9000 direct rendering"
date: 2008-11-08
forum: Multimedia Software
---

### Post by trailofdead on 2008-11-08
I'm trying to get direct rendering to work.  

Here is the relevent info:
```
lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 02)

```

```
glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: www.mesa3d.org

```

```
glxinfo | grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

```
1$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
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
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
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
0x50 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

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
	Option		"Device" "/dev/input/mice"
	Option		"Protocol" "ImPS/2"
	Option		"Emulate3Buttons" "true"
	Option		"EmulateWheel" "true"
	Option		"EmulateWheelButton" "2"
	#Option		"ZAxisMapping" "4 5"
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
	Identifier	"Radeon 9000 RV250"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"XAANoOffscreenPixmaps"	"true"
	Option		"GARTSize"	"64"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection	"Display"
		Virtual	2680 1050
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"dbe"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

Any help would be appreciated.  Thanks

---

### Post by trailofdead on 2008-11-09
bump

---

### Post by trailofdead on 2008-11-10
anyone?

---

### Post by Yellow Pasque on 2008-11-10
A few thoughts -
Do you have the libgl1-mesa-dri package installed?
Try adding dri to the Modules section in your xorg.conf
See if running glxinfo as root shows dri enabled (i.e. sudo glxinfo)

---

### Post by trailofdead on 2008-11-11
> **Temüjin said:**
> A few thoughts -
Do you have the libgl1-mesa-dri package installed?
Try adding dri to the Modules section in your xorg.conf
See if running glxinfo as root shows dri enabled (i.e. sudo glxinfo)

I have the libgl1-mesa-dri package installed.  I just tried adding Load "dri" to the Modules section in my xorg.conf and it didnt do anything.  Running glxinfo as root shows the same output as the 4th code box in my original post.

---

### Post by zednet on 2008-11-11
I have the same gfx chip in my Dell Latitude D600.

Been scurrying the webs for answers on getting it to perfom decent, but so far Ive only been able to find OS drivers.

Posting here for a combined bump and shoutout for suggestions

---

### Post by trailofdead on 2008-11-16
bump

---

### Post by Yellow Pasque on 2008-11-16
Some things to try:
- See if LIBGL_DEBUG=verbose produces any clues:
```
export LIBGL_DEBUG=verbose
glxinfo
```

- See if glxinfo reports direct rendering with root permissions:
```
sudo glxinfo | grep direct
```

- Look through the X log to see what it says about DRI
```
gedit /var/log/Xorg.0.log
```

Have you previously tried to install fglrx drivers? I just recently had a problem where fglrx linked my programs to the wrong version of libGL.

---

### Post by Marcus Derekus on 2008-11-16
Did you go into System<Administration<Hardware Drivers and enable your graohics card?

---

### Post by Marcus Derekus on 2008-11-16
He's not using fglrx.

if you  look at his xorg.conf file under Section "Device"
the driver is "ati".

It would "fglrx" if that is what he was using.

unless, of course, the xorg.conf file is configured for the wrong driver.(but i dont think so)

but hey if im wrong change it.

btw perhaps installing fgrlx might fix the problem

(except im not sure it supports your card)

---

### Post by inigomontoya on 2008-11-16
Try adding:
Option "BusType" "PCI"
to your xorg.conf in the Device or Screen sections.

---

### Post by sharon.gmc on 2008-11-16
had the same problem,  solved with the installation of fgrlx.  thanks!!

---

### Post by trailofdead on 2008-11-16
still trying to get this to work.  i'm not using fgrlx drivers.

---

### Post by Marcus Derekus on 2008-11-16
Try installing fglrx see if it works

might want to backup xorg.conf if you do

---

### Post by Yellow Pasque on 2008-11-16
No, proprietary drivers do not support the Radeon 9000.

---

### Post by Marcus Derekus on 2008-11-16
try going to [http://ati.amd.com](http://ati.amd.com) and get the linux drver for your card

---

### Post by trailofdead on 2008-11-17
> **Marcus Derekus said:**
> try going to [http://ati.amd.com](http://ati.amd.com) and get the linux drver for your card

they only have drivers from aug 2006 that are for Xorg 6.8.  should i even try to use them?

---

### Post by automaton26 on 2008-11-17
Latest ATI Catalyst (8.11) .pdf shows that proprietary drivers (fglrx) don't work for the old RV250 Mobility FireGL 9000.

You have to use the open source ones - more info here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Although the open source drivers were all present and working OK on my Dell Inspiron 8200, after a standard default installation of intrepid.

And my xorg.conf is just the default one (most of that is just detected by xserver now ?)

Doing "glxinfo | grep direct" seems to show me that direct rendering is on, anyway.

---

### Post by Marcus Derekus on 2008-11-17
Wouldn't hurt to try.

Otherwise i'm not sure

---

### Post by trailofdead on 2008-11-19
i'm using the open source drivers now, as you can see in my xorg.conf in my first post.  bump.

---

### Post by inigomontoya on 2008-11-20
Did you try my suggestion by adding 
Option "BusType" "PCI" to your xorg.conf?  I have a Radeon 9600 and that option enabled direct rendering for me.

---

### Post by automaton26 on 2008-11-21
I have a fresh install of intrepid, using your chipset, but if I do "glxinfo | grep vendor", the OpenGL vendor string is "Tungsten Graphics" instead.

Also, I'm able to remove my xorg.conf completely, and Direct Rendering still works.

So you could try that **_if_** you're confident about being able to restore your original xorg.conf afterwards outside gdm/kdm.

Finally, if the machine has ever had *fglrx* on it, you could try those "Removing the proprietary fglrx driver" instructions, from the link that I posted earlier.

---

### Post by trailofdead on 2008-12-01
> **inigomontoya said:**
> Did you try my suggestion by adding 
Option "BusType" "PCI" to your xorg.conf?  I have a Radeon 9600 and that option enabled direct rendering for me.

I tried it.  Didnt change anything.
Any other suggestions?

---

### Post by Yellow Pasque on 2008-12-01
> **Temüjin said:**
> Some things to try:
- See if LIBGL_DEBUG=verbose produces any clues:
```
export LIBGL_DEBUG=verbose
glxinfo
```

- See if glxinfo reports direct rendering with root permissions:
```
sudo glxinfo | grep direct
```

- Look through the X log to see what it says about DRI
```
gedit /var/log/Xorg.0.log
```

Have you previously tried to install fglrx drivers? I just recently had a problem where fglrx linked my programs to the wrong version of libGL.

Did you try any of these

---

### Post by trailofdead on 2008-12-01
> **Temüjin said:**
> Did you try any of these

I did.

export LIBGL_DEBUG=verbose
glxinfo
```
name of display: :0.0
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
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
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
0x61 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

sudo glxinfo | grep direct
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

not really sure what I'm looking for in the log...
gedit /var/log/Xorg.0.log
```
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
```
```
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
```
```
(--) RADEON(0): Chipset: "ATI Radeon Mobility 9000 (M9) Lf (AGP)" (ChipID = 0x4c66)
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(II) RADEON(0): AGP card detected
(**) RADEON(0): Forced into PCI mode
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=32768K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 32768 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default

```

```
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 35044 kB of video memory needed at this resolution and depth.
disable montype: 2
```

Just a note, DRI didnt work even before I added SubSection "Display"
Virtual	2680 1050 EndSubSection

Any suggestions?

---

### Post by Yellow Pasque on 2008-12-01
Comment out or delete the Virtual line and then post your Xorg.0.log after starting X.

---

### Post by trailofdead on 2008-12-01
> **Temüjin said:**
> Comment out or delete the Virtual line and then post your Xorg.0.log after starting X.

It's working now after commenting out Virtual.  I guess one of the things I tried since I originally posted this worked.  Thanks.

---

