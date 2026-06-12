---
title: "Open-Source RadeonHD 3D"
date: 2009-12-14
forum: Multimedia Software
---

### Post by Yellow Pasque on 2009-12-14
This is for Ubuntu 9.10 (maybe 10.04) only right now. A lot of people are asking about this and I wanted a thread I could link to.

Make sure you've purged all of the proprietary fglrx/Catalyst stuff you installed: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

Install a 2.6.32 kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/) (Install the appropriate image package for your architecture as well as the appropriate headers package and the "headers-all" package. The source package is probably not needed unless you like to customize your kernel or need to patch some kernel module).

Boot into your new kernel and make sure all of your hardware works. It may not. For example, I needed to build the ndiswrapper kernel module for my wireless card. (If you're unsatisfied with how the system works with the new kernel and want to abort this procedure, reboot your system and press 'Esc' after the system screen. Boot into the regular 2.6.31-ubuntu kernel and uninstall the 2.6.32 packages you installed.)

Now add the xorg-edgers PPA to your 3rd-party Software Sources (System -> Administration -> Software Sources): [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) and update/upgrade your packages. Restart X (i.e. log out and back in).

Check some commands, like:
```
LIBGL_DEBUG=verbose glxinfo
glxgears
```
You should have Mesa DRI R600 as your OpenGL renderer. If you have 'Software Rasterizer', the r600_dri.so module failed to load. If glxgears complains about a command stream, you're probably using the old kernel.

What should work: Compiz, although some specific effects may not work
Various 3D apps that only require OpenGL 1.5 or earlier

What won't work: Some oddball cards like 3870X2 Most gaming in WINE, OpenGL 2.x apps (support for OpenGL 2.x is under development)

More info: [http://wiki.x.org/wiki/radeonhd%3Aexperimental_3D](http://wiki.x.org/wiki/radeonhd%3Aexperimental_3D)

---

### Post by n3had on 2009-12-28
```
$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

```

Here's my Xorg

```
Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "LG W2261"
	HorizSync       30.0 - 83.0
	VertRefresh     56.0 - 75.0
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	Option         "TwinView" "0"
	Option         "metamodes"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "dbe"
	Load           "extmod"
	Load           "type1"
	Load           "freetype"
	Load           "glx"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier	"Default Device"
        Driver          "radeonhd"
        Option          "DRI" "on"   #this is the default in recent radeonhd versions
        Option          "AccelMethod" "EXA" #this is the default in recent radeonhd versions
EndSection

```

adn lastly my desktop resolution is at 1680x1050. how can i move back to the native 1920x1080?

Thanks in advaace.

---

### Post by n3had on 2009-12-29
```
$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 4.3.0 r600 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tls/r600_dri.so
libGL: OpenDriver: trying /usr/lib/dri/r600_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/tru3m0sl3m/.drirc: No such file or directory.
IRQ's not enabled, falling back to busy waits: 2 0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: Mesa Project and SGI
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
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RS880 9710) 20090101  TCL
OpenGL version string: 1.5 Mesa 7.7
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_depth_clamp, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_provoking_vertex, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_MESAX_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_depth_clamp, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

8 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x61 32 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon

8 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x62  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x63  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x64  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x65  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x66  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x67  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x68  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

I could run some 3d applications and glxgears running fine but enabling compiz makes system unresponsive.

---

### Post by Yellow Pasque on 2009-12-29
Are you sure you don't have ATI's proprietary version of libglx.so hanging around on your system somewhere?

---

### Post by n3had on 2009-12-29
> **Temüjin said:**
> Are you sure you don't have ATI's proprietary version of libglx.so hanging around on your system somewhere?

I've two over here
```

/usr/lib/xorg/modules/extensions/FGL.renamed.libglx.so
/usr/lib/xorg/modules/extensions/libglx.so

```

i think i have cleanly uninstalled it using ati uninstall utility and also synaptic

---

### Post by Yellow Pasque on 2009-12-30
Just to be sure:
```
sudo apt-get --reinstall install xserver-xorg-core
```

If you still have issues, try starting compiz from terminal.

---

### Post by RodGer GR on 2009-12-31
I installed the new kernel as you suggested and it worked fine. Thanks for that. Also, as you predicted, some things don't work. For me it's the bluetooth device that is not recognized. If there is not much to discuss (so I should maybe start a new thread) could you please give me an idea on how to fix this. Thanks a lot even if you don't have the time to answer. You've already helped.

---

### Post by RodGer GR on 2009-12-31
> **RodGer GR said:**
> I installed the new kernel as you suggested and it worked fine. Thanks for that. Also, as you predicted, some things don't work. For me it's the bluetooth device that is not recognized. If there is not much to discuss (so I should maybe start a new thread) could you please give me an idea on how to fix this. Thanks a lot even if you don't have the time to answer. You've already helped.
 
Except this, as I have a problem with waking up after suspending (an unresponsive black screen comes up), can you please tell me what should be the content of xorg.conf?
I have an xorg.conf.failsafe as I had my old (containing the fglrx driver) xorg.conf renamed so that I could boot my system again.

The current content of xorg.conf.failsafe is:
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```
As now I use the xorg edgers driver, do you think that xorg.conf is as it should be?

---

### Post by hlitz on 2009-12-31
Hi thanks Temujin,

your description worked flawlessly. glsxgears works, however I have only 1000 frames (Tp x31 with Radeon 7000)

The great thing with the RadeonHD 3D driver is that now my suspend/hibernate modes work with 9.10 the machine actually wakes up and everything works.

While 3D performance is ok, I have a BIG problem with 2 D. Scolling in firefox lags and flash movies perform very bad. The default ubuntu driver did much better, both compiz and flash worked much better. Any ideas?

---

### Post by Yellow Pasque on 2009-12-31
hlitz, this procedure was for Radeon**HD** cards. The updated kernel may have fixed suspend/resume.
> While 3D performance is ok, I have a BIG problem with 2 D. Any ideas?
Maybe try forcing XAA 2D in the Device section of your xorg.conf:
```
Option "AccelMethod" "XAA"
```

---

### Post by Yellow Pasque on 2009-12-31
RodGer: I'm not too educated on suspend/resume stuff. I have a power-efficient desktop and the suspend/resume never worked (maybe when kernel 2.6.33 matures). :\

As for the bluetooth device, you probably need to build a kernel module for it. You wouldn't happen to know what driver it uses, would you? A LiveCD might show you if you run:
```
lspci -vv
```

---

### Post by hlitz on 2010-01-04
Thanks temujin, yes you might be right with the standby/suspend issues.

I know this sounds dumb, but can you tell me as well how I cleanly deinstall the RadeonHD driver and revert back to the default ubuntu driver?

thanks, Heiner

---

### Post by Yellow Pasque on 2010-01-04
Boot into the stock UBuntu kernel (whatever you were using before installing 2.6.32 kernel).
Now go into Synaptic and remove the 2.6.32 kernel packaged you installed.
While in Synaptic, install the ppa-purge package. Close Synaptic.
In terminal:
```
sudo ppa-purge xorg-edgers
```

---

### Post by hlitz on 2010-01-05
Hi
if I want to keep kernel 2.6.32 should I just install the ppa-purge package and then:
```

sudo ppa-purge xorg-edgers

```
???

---

### Post by Yellow Pasque on 2010-01-05
^Yes.

---

### Post by hlitz on 2010-01-13
thanks all runs smoothly now, including hibernate and standby

---

