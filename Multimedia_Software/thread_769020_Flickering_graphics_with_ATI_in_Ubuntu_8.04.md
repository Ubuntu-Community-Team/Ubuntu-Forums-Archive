---
title: "Flickering graphics with ATI in Ubuntu 8.04"
date: 2008-04-26
forum: Multimedia Software
---

### Post by pmalvr on 2008-04-26
Hi, I had installed the new Ubuntu 8.04 from scratch, then i installed the proprietary ATI drivers. After that, i enabled the desktop effects, everything works great until i run a program that uses OpenGL. For example, when i run Google Earth the graphics starts to flicker or even when i choose a screen saver. In Ubuntu 7.10 with proprietary ATI Drivers + XGL everything worked great, but now i have this problem. Can someone help me, please ?

Thanks from Portugal

---

### Post by oldjimsteele on 2008-04-26
I'm having the same problem.  Compiz works fine, I can run 3D applications like Urban Terror with no slowdown but about every second or so, it flickers.  Without compiz in gutsy it worked fine.  Card is ATI Radeon Xpress 200M on the 64-bit desktop edition of 8.04.

---

### Post by pmalvr on 2008-04-26
I forgot to say, my card is an ATI Mobility Radeon X700!! Can someone help in this issue...
By the way i have another question... if we install the proprietary ATI Driver from Ubuntu repositories, thus they automatically update to a new release or we have to allways re-install the drivers?

Thanks

---

### Post by CamboCambo on 2008-04-26
I have exactly the same issue radeon x1400 mobility anything that uses open gl screensaver, google earth, tuxracer etc...

The screen flickers really bad, and black lines come across it.

cambo@cambo:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7415 Release

I dont have compiz enabled.

This previously worked perfect in 7.1

Cheers

---

### Post by pmalvr on 2008-04-26
I think this is a major bug... i hope they find a solution soon and  post here a solution !! :(

---

### Post by spuck on 2008-04-26
Same thing here, integrated x1250..

---

### Post by pmalvr on 2008-04-27
Google Earth flickers, screen savers flickers too, games like Urban Terror are impossible to play, videos in full screen are difficult to watch... can someone post here a solution if possible ?!

Thanks in advance

---

### Post by pmalvr on 2008-04-27
Here is the output i get with this 2 commands...

**sudo glxinfo:**

name of display: :0.0
display: :0 screen: 0
direct rendering: Yes
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
GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.1.7412 Release
OpenGL extensions:
GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers,
GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample,
GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object,
GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects,
GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient,
GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
GL_ARB_texture_env_dot3, GL_ARB_texture_float,
GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,
GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc,
GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr,
GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,
GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters,
GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil,
GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
GL_EXT_secondary_color, GL_EXT_separate_specular_color,
GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture,
GL_EXT_texgen_reflection, GL_EXT_texture3D,
GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array,
GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection,
GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod,
GL_WIN_swap_hint, WGL_EXT_swap_control

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
0x23 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x24 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x25 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x26 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x27 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x28 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x29 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 0 0 None
0x2a 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 0 0 None
0x2b 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x2c 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x2d 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x2e 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x2f 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 2 1 None
0x30 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 2 1 None
0x31 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 2 1 None
0x32 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 2 1 None
0x33 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x34 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x35 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x36 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x37 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 4 1 None
0x38 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 4 1 None
0x39 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 4 1 None
0x3a 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 4 1 None
0x3b 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x3c 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x3d 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x3e 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x3f 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 6 1 None
0x40 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 6 1 None
0x41 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 6 1 None
0x42 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 6 1 None
0x43 24 tc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x44 24 tc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x45 24 tc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x46 24 tc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x47 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x48 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x49 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x4a 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x4b 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x4c 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x4d 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x4e 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x4f 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x50 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 0 0 None
0x51 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 0 0 None
0x52 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 0 0 None
0x53 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x54 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x55 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x56 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x57 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 2 1 None
0x58 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 2 1 None
0x59 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 2 1 None
0x5a 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 2 1 None
0x5b 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x5c 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x5d 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x5e 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x5f 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 4 1 None
0x60 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 4 1 None
0x61 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 4 1 None
0x62 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 4 1 None
0x63 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x64 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x65 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x66 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x67 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 0 0 0 0 6 1 None
0x68 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 0 0 0 0 6 1 None
0x69 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 0 0 0 0 6 1 None
0x6a 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 0 0 0 0 6 1 None
0x6b 24 dc 0 32 0 r y . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x6c 24 dc 0 32 0 r . . 8 8 8 8 0 24 8 16 16 16 16 0 0 None
0x6d 24 dc 0 32 0 r y . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x6e 24 dc 0 32 0 r . . 8 8 8 8 0 24 0 16 16 16 16 0 0 None
0x6f 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x70 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x71 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x72 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
0x85 32 tc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 8 1 Ncon


**less /etc/X11/xorg.conf:**

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "pt"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "fglrx"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Defaultdepth 24
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen "Default Screen"
Inputdevice "Synaptics Touchpad"
EndSection
Section "Module"
Load "glx"
EndSection


**Thanks**

---

### Post by Melcar on 2008-04-27
It's not a bug of the driver, but a limitation of DRI and the current X.  DRI2 will address this issue, whenever it comes out.

---

### Post by pmalvr on 2008-04-27
> **Melcar said:**
> It's not a bug of the driver, but a limitation of DRI and the current X.  DRI2 will address this issue, whenever it comes out.
And do you know a date for that to happend ?... because this problem is very annoying :(

---

### Post by pmalvr on 2008-04-27
I've found that if we install xserver-xgl the problem in the flickering in OpenGL programs disappears, but unfortunately the rest gets to much slow... this problem is getting me nuts :S

---

### Post by Mad_Gouki on 2008-04-28
I also have a problem with my X1250(it might be X1200, it has been labeled as both on retailer sites), i get that problem pmalvr talks about, where it slows down with xserver-xgl.
I installed the xserver-radeonHD, which supposedly supports the x#### video cards, i don't know if that will fix it at all or if you have to install it.  I hope somebody who knows more is able to help.

i found a wiki article on how to fix it, it said to uninstall xserver-xgl.  Compiz works without it, the xserver-xgl driver will run mesa drivers, which cause slowdowns.

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers)

That is the wiki enry on installing the drivers, I hope this helps someone out there.

---

### Post by jaaap on 2008-04-30
I have also the problem with my ATI videocard, but when I disable the Visual Effects in "Appearence", the screen doesn't flicker in Google Earth! Maybe it's a solution...

---

### Post by pmalvr on 2008-04-30
> **jaaap said:**
> I have also the problem with my ATI videocard, but when I disable the Visual Effects in "Appearence", the screen doesn't flicker in Google Earth! Maybe it's a solution...

Thanks but i cannot consider that a solution, only a temporary remedy... Can someone help us in this problem ?

---

### Post by Melcar on 2008-04-30
Someone should really sticky an information thread on this.  Currently, you can't use any form of desktop composition effect (KDE/XFCE transparency included) with any form of 3D/2D accelerated rendering.  DRI2 fixes this, but it's not officially out yet.  The only real option one has if he really wants to keep using Compiz and still be able to render with opengl and/or Xv is to get an nvidia card and use the proprietary drivers, since the nvidia drivers act differently.  Again, this is not an ATI problem; every single driver out there (be it proprietary or open source) is affected by this (with different degrees of severity).

---

### Post by psayre23 on 2008-05-01
Same issue on a 9700 mobile. I installed fusion-icon and change the window manager to metacity when I want to run a 3d app. If you are gaming, you'll most likely want to turn off compiz anyways, so it is handy.

Agreed, this is a workaround...but it is better then having flickering in-game, and should boost your frame rates a bit. And stick_request++;

sudo apt-get install fusion-icon

fusion-icon

---

### Post by CarpKing on 2008-05-01
Try installing compiz-config-settings-manager and selecting "Unredirect Fullscreen Windows" in "General Options."

It might not help windowed programs like Google Earth, but it should help the fullscreen ones.

---

### Post by Bastaard on 2008-05-02
same problem, ATI Radeon x550, proprietary drivers, any OpenGL application

---

### Post by mikexgough on 2008-05-06
Same here with X600 on Elonex laptop, worked 100% in Gutsy.........

---

### Post by Pépou on 2008-05-06
Same problem : i cannot appreciate hardy because it's very difficult to watch videos : very bad quality and very slow + CPU utilization is 100%.
I have an ATI radeon mobility x1400.

Any solutions ??
Thank you in advance.

---

### Post by st0nedpenguin on 2008-05-06
> **Melcar said:**
> Someone should really sticky an information thread on this.  Currently, you can't use any form of desktop composition effect (KDE/XFCE transparency included) with any form of 3D/2D accelerated rendering.  DRI2 fixes this, but it's not officially out yet.  The only real option one has if he really wants to keep using Compiz and still be able to render with opengl and/or Xv is to get an nvidia card and use the proprietary drivers, since the nvidia drivers act differently.  Again, this is not an ATI problem; every single driver out there (be it proprietary or open source) is affected by this (with different degrees of severity).

I'm completely flicker free in 3d and video using the open source ati driver.

Windowed or fullscreen.

---

### Post by Der Pate on 2008-05-06
Besides turning us green with envy, do you have any suggestions for us to take part in your enlightenment?

---

### Post by Melcar on 2008-05-06
> **st0nedpenguin said:**
> I'm completely flicker free in 3d and video using the open source ati driver.

Windowed or fullscreen.



I'm guessing you mean the older ati driver.  RadeonHD doesn't have 3D acceleration and just recently got 2D.

---

### Post by Melcar on 2008-05-06
[http://www.phoronix.com/forums/showthread.php?t=7889&highlight=compiz+implies]("http://www.phoronix.com/forums/showthread.php?t=7889&highlight=compiz+implies")

[http://www.phoronix.com/forums/showthread.php?t=8671]("http://www.phoronix.com/forums/showthread.php?t=8671")

[http://www.phoronix.com/forums/showthread.php?t=9159]("http://www.phoronix.com/forums/showthread.php?t=9159")

---

### Post by st0nedpenguin on 2008-05-07
> **Der Pate said:**
> Besides turning us green with envy, do you have any suggestions for us to take part in your enlightenment?

I did nothing special whatsoever, fresh Hardy install and everything was working out of the box since the X800 is a pretty old GPU.


> **Melcar said:**
> I'm guessing you mean the older ati driver.  RadeonHD doesn't have 3D acceleration and just recently got 2D.

Yeah, it's worth looking into for anyone with an older card, obviously if you're running a newer card it's not gonna be much help though.

---

### Post by Xavier Oddmon on 2008-05-18
I've got this problem as well. I've got a Radeon HD 2600. The only solution i've found is that if I disable compiz, the flicker goes away. It's a shame though, compiz is just so awesome...

---

### Post by markbuntu on 2008-05-18
The problem is between compiz and the ATI driver. It has to do with a compiz call to GL_pixmaps... that is not recognized and so compiz defaults to indirect rendering which uses a lot of cpu resources and causes a vastly reduced frame rate. This in turn causes ANY process that needs a rapid frame rate to flicker if compiz is running. One solution is to switch to metacity when using Google Earth or any other ap that flickers in compiz.

There is no immediate alternative short of replacing the card.

On my machine glx_gears reports ~4-5000FPS, fgl_glxgears reports ~1400FPS while compiz benchmark reports ~108FPS. 

Do you see the problem here?

We who have ATI cards must wait until either ATI or Compiz fix this problem but Compiz has taken the position of not providing support for these types of problems so we must pressure ATI by giving them lots of feedback.

This is really the only gripe I have about the ATI drivers.


HP 1330n Media Center (modified)
ASUS A8AE-LE motherboard (OEM)
AMD Athlon64 3800+ 2.9GHZ 939 socket
3GB 3200 DDR RAM
ATI Radeon Express 200M (disabled in bios)
ATI HD3650 1GB DDR2  PCI Express
AC97 on board sound
Realtek 810L

SOYO 24 inch LCD wide screen monitor 1920x 1200
Samsung 930B 19 inch LCD 1280x1024


Release 8.04
Kernel Linux 2.6.24-16-generic
Gnome 2.22.1
ATI Proprietary Linux Driver Version Identifier:8.47.3

---

### Post by stoer on 2008-05-19
I got the same problem, flickering display in games.
Using an ATI radeon mobility 9700, Driver installed using EnvyNg.
Same problem using Kubunt and Linux Mint 5 beta (Elyssa).

Hope something comes up soon, sort of detracts from using Linux for anything other than office, which wasn't my goal.

---

### Post by johnthomson on 2008-05-23
I had (almost) endless problems with flickering screen or not visible at all screen in Hardy,also with ATI card. The problem was that the xorg file
created by Hardy was more or less empty. In the end I installed Xandros
and took the xorg from that which works (sort off) OK. There is a mystery
though. Preferences, screen resolution offers a resolution 1152*864 which is not in xorg.conf and is missing most of the resolutions which are in xorg. Does anyone know where these other resolutions are kept, I suppose in a Gnome file somewhere.

thanks,john

---

### Post by 47_MasoN_47 on 2008-05-23
> **CarpKing said:**
> Try installing compiz-config-settings-manager and selecting "Unredirect Fullscreen Windows" in "General Options."

This one didn't work for me.  I tried Xmoto in windowed and full screen mode and it still flickered.  I'm using a HIS Radeon HD 2600.

---

### Post by zgornel on 2008-05-24
The only solution is to disable visual effects or use the 'x11' driver for videos and disable compiz before running opengl apps.

---

### Post by warbler on 2008-05-26
> **zgornel said:**
> The only solution is to disable visual effects or use the 'x11' driver for videos and disable compiz before running opengl apps.

This seems to work for me.

Using VLC Media Player I have not had any flicker problems anyway with video playback.

In order to avoid flicker in other applications I can simply right click the desktop and disable the visual effects, then enable them again when I am finished. I lose my AWN launchpad during this, but it comes back as I left it.

James

---

### Post by Ohwii on 2008-05-28
I can only quote mr. markbuntu

> 
We who have ATI cards must wait until either ATI or Compiz fix this problem but Compiz has taken the position of not providing support for these types of problems so we must pressure ATI by giving them lots of feedback.


After 3 month of enabling this and that, installing and deleting here and there. I came to the conclusion that I have live without compiz until ATI improves their drivers. 

It is impossible to have the best of both worlds. I mean having a very nice OS without flickering AND nice desktop effects. therefore no compiz and waiting until ATI brings out the super nice driver with no flickering. 

So for all those that are still looking for an answer: just > [...] to switch to metacity when using Google Earth or any other ap that flickers in compiz 

Cheers 

oh Wii

PS: it is a shame

---

### Post by zgornel on 2008-05-28
I cannot be too sure but maybe the open source drivers should be tried in a few months. Already, according to phoronix, games and compiz run pretty fine. It would be great if they would surpass both in performance and functionality the proprietary ones :D :D. Just a quick preview:
[http://www.phoronix.com/vr.php?view=12402](http://www.phoronix.com/vr.php?view=12402)

---

### Post by PoopyTheJ on 2008-06-02
This fix works for me in watching video, for games just turn off visual effects in appearance while playing and turn them back on when you're done. Anyways to fix the flickering video with ATI cards turn off textured video. Edit your etc/X11/xorg.conf file with this in the fglrx device section,

Option		"TexturedVideo"	"off" 

Restart X and you're watching flicker free video.

I'm running a 3850HD with the Catalyst 8.5's

---

### Post by beN..87 on 2008-06-09
come on people - get emailing - [email]tech.support@amd.com[/email]  - make em get the message that all solutions are failing and we need help - just let them know that its all the users of their shiny new  high end stuff - that could be showing their freinds a 3d desktop with an ATI sticker next to the blazing glory

[email]tech.support@amd.com[/email] - if enough of us email i'm sure theyll allocate some time - do it now! 

(p.s. if somebody wants to turn this into a poll thingy plaese do - im not forum savvy enough)

---

### Post by seagull man on 2008-06-09
Ok I emailed amd tech support saying I feel I will have no choice but to return my HD3870 if a solution is not provided soon.

Anyway, disabling compiz removes the problem completely yeah? How do I disable it? (i'm new to linux)

---

### Post by B3Nji on 2008-06-09
> **seagull man said:**
> Ok I emailed amd tech support saying I feel I will have no choice but to return my HD3870 if a solution is not provided soon.

Anyway, disabling compiz removes the problem completely yeah? How do I disable it? (i'm new to linux)

Hey mate, 

What you need to do for quick disable of compiz is install fusion icon. 
Go to System > Administration > Synaptic Package Manager. Type in your password if it asks. 

Then click the search button. type in 'fusion' when its done serarching click fusion-icon, choose 'mark for installation'. Then click apply, then again if it asks. Wait for it to download and install. 

Now you will find 'Compiz Fusion Icon' under Applications > System Tools. Run that, you will get fusion icon running in your system tray by your clock. To disable compiz simply right click the icon, choose 'select window manager' then click 'metacity'. To turn it back on just choose 'compiz' instead. 

Sorted =)

---

### Post by markbuntu on 2008-06-09
The easiest way to disable compiz is to right click on your desktop and choose Change Desktop Background. Then choose Visual Effects and pick none. After viewing your video you can reenable your Visual Effects the same way and compiz will return to what you had before.

---

### Post by seagull man on 2008-06-10
thanks boys, both answers help. for the moment i've set it to metacity like B3Nji said. This actually sort of got 2 birds with 1 stone because I wanted to get the solid and snappy window resizing back (i didn't like the semi-transparent window resizing compiz was using).

beN..87, i'm not sure [email]tech.support@amd.com[/email] is correct. they sent back an email saying:

> For all PC processor inquiries, the subject line must contain
"CPU-Support".

For all Embedded product inquiries, the subject line must contain
"Embedded-Support".

For all AMD Core Math Library inquiries, the subject line must contain
"ACML-Support".

For all AMD Performance Library inquiries, the subject line must contain
"APL-Support".

For all AMD Developer inquiries, the subject line must contain
"Developer-Support".
****

dunno what those things are. i think you have to go to: [http://support.ati.com]("http://support.ati.com"), register, and submit a ticket.

---

### Post by blar321 on 2008-06-22
Thanks disabling visual effects stopped the flickering and made Eternal Lands bearable.

---

### Post by toppknott on 2008-06-26
> **jaaap said:**
> I have also the problem with my ATI videocard, but when I disable the Visual Effects in "Appearence", the screen doesn't flicker in Google Earth! Maybe it's a solution...

This also fixed my flickering problem completely and I am happy with the solution.

---

### Post by seagull man on 2008-09-11
Has this problem been solved? I'm considering installing Catalyst again.

---

### Post by at0mic on 2008-09-11
source of my flickering was the desktop effects. turn them off .

---

### Post by domib on 2008-09-12
Anybody know...

How to disable desktop effects in Xubuntu? 
How to even tell if they're on?
How to tell if I'm running compiz?

---

### Post by domib on 2008-09-12
After some more reading I found compositor settings under 
Settings > Settings Manager > Window Tweaks > Compositor.
Compositor is disabled.

So any ideas why i'm getting flickering? (with nvidia!)

---

### Post by Naiki Muliaina on 2008-09-20
> **Melcar said:**
>  you can't use any form of desktop composition effect (KDE/XFCE transparency included) 

Havent had any XFCE compiz style problems scince i started using it 6 months ago. Its why i use it, i can have a pretty screen without fussing with Compiz. :) Its been fine with a Radeon x1950 and the notorious HD2400.

---

### Post by kslat3r on 2008-09-27
> **PoopyTheJ said:**
> This fix works for me in watching video, for games just turn off visual effects in appearance while playing and turn them back on when you're done. Anyways to fix the flickering video with ATI cards turn off textured video. Edit your etc/X11/xorg.conf file with this in the fglrx device section,

Option		"TexturedVideo"	"off" 

Restart X and you're watching flicker free video.

I'm running a 3850HD with the Catalyst 8.5's

This fix worked fantastically for me, thanks alot! Can even use Compiz whilst watching full-screen video with no flicker.

Hardware is: ATI Mobility Radeon X1100, Acer Aspire 5100

Thanks again..

---

### Post by Kinnison on 2008-09-29
**-short intro-**
Hello all! I am new in these forums and in this OS. This is my third day of experiencing any form of Linux, with Ubuntu 8.04. I have been using windows for a very long time, starting with windows 3.11 then moved on to win millenium and lastly windows xp. Now its been 3 days that I have succesfully set-up a dual boot of windows xp and ubuntu. Luckily, I faced no problems with the installation. In fact it felt more user-friendly and simple to do when compared to windows xp. 

**-my prob-**
However there was one problem. Shortly after I entered the ubuntu desktop for the first time, a notification appeared on the upper right asking me to install proprietary ati drivers for my video card. I was thinking I would have to  download them and install them manually as in Windows but I was (positively) surprised to see the OS was actually able to get them for me, which is impressive! However, after restarting for the drivers to work, the dreaded "black screen of death"came up. I had to restart the computer, but I coundnt find a way to solve the problem. 

I decided to reinstall the os by deleting the partition it was on and recreating it, then installing again. Not a good thing to happen to a first-time user, surely... but I had already found the new inteface actually nicer than windows... so I just had to give it a go.

This time the notification for restricted ati drivers didn't show up, not sure why, but I made sure to read up on as much info on the net as I could, this time around. Of help was the knowledge that if you get black screen you can use the repair options at startup to restore the system to a usable state.

So, this time I installed the ati driver as is available on their website, and got black screen again. repairing things back to a useable state, I ended up with a low resolution (which is strange because there was a higher res after a freshly installed ubuntu). This time I followed another posted solution, about using an "EnvyNG" utility, and it managed to make the drivers work! 

However, the flickering issue appeared. I read this thread, disabled effects in the desktop and the flicker in 3d screensavers, videos etc. disappeared. So I can say I am "sorted out" for now.

Since I am a gamer, I will be trying out a few 3d games but I expect them to work well since the problem seems sorted out.

It does seem that all is not perfect, though, because if i type in terminal:"fglrxinfo" then I get "Segmentation Fault".
I thought this command was supposed to give info on the video drivers. Anyway, I guess you'll see noob  questions from me sooner or later, altough I usually get by just by googling for answers and reading forum thread after forum thread.

:popcorn:

**->edit**
I just tried to install and play Alien Arena, a well known freeware fps game, to see how 3d acceleration is working. The game worked, but the framerates were very low.

After that, I downloaded the Enemy Territory: Quake Wars demo to see how that did. I managed to get it started at first, but as soon as I changed the resolution from the options my picture messed up and I coudlnt see anything. Almost like it was an unsupported resolution, even though I chose a supported one.

Next time I tried to start this demo, I got the following message and was unable to start the game.
...
...
execing 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
execing 'etqwbinds.cfg'
execing 'autoexec.cfg'
TODO: Sys_GetGfxDeviceIdentification
Vendor: Device:
thread priority set to 1
Opening IP socket: localhost:-1
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1280x1024
SDL_ListModes:
1280x1024 1280x960 1280x768 1280x720 1152x864 1024x768 800x600 640x480 640x400 400x300 320x240 
320x200 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
------- Initializing renderSystem --------
----- R_InitOpenGL -----
signal caught: 'Segmentation fault', si_code 1
callstack:
0x0
[0x082cc6d1]
[0x082bc82f]
[0xb7f8a440]
Trying to exit gracefully..
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()

---

### Post by ft23002 on 2008-10-13
> **PoopyTheJ said:**
> This fix works for me in watching video, for games just turn off visual effects in appearance while playing and turn them back on when you're done. Anyways to fix the flickering video with ATI cards turn off textured video. Edit your etc/X11/xorg.conf file with this in the fglrx device section,

Option		"TexturedVideo"	"off" 

Restart X and you're watching flicker free video.

I'm running a 3850HD with the Catalyst 8.5's

Thanks, this worked for me!!!
Video with compiz & emerald enabled ...awesome.

I wanted to give you your first "thank you" but the thank you button's aren't showing in this thread.

Running on Ubuntu Hardy, ATI X1400, on a dell E1505, with ATI 8.9 drivers.

---

### Post by hwttdz on 2009-09-15
I just wanted to give fair warning, this did not work for me, in fact it broke my x-server.  

ATI RV610, Radeon 2400HD pro

---

