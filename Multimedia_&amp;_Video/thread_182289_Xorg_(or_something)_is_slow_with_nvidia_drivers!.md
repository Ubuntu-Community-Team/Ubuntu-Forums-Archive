---
title: "Xorg (or something) is slow with nvidia drivers!"
date: 2006-05-25
forum: Multimedia &amp; Video
---

### Post by hbweb500 on 2006-05-25
I am using a standard Dapper installation, with just the Nvidia drivers installed, and it seems like the graphics display is slow. This is especially noticeable in programs like Firefox, like it may take several seconds to switch between tabs, or to have the cursor respond when I click a text box. Im running no other programs. My system should be able to easily handle the deafult theme: Dell Intel Celeron 2.4 GHz with 768 MB RAM and 64MB PCI Nvidia card with the Nvidia drivers.

Honestly,this is the one thing holding me back from using Linux full time. With the slow performance I get, Ubuntu really doesnt feel very useable or fluid, compared to my XP desktop.

Any ideas? I know the information I provided may not be much, but if you need anymore...please, ask.

---

### Post by Teroedni on 2006-05-25
Are you sure that your 3d drivers are installed ?
What does ```
glxinfo
``` and
```
 glxgears  -printfps
```give you?

---

### Post by hbweb500 on 2006-05-25
glxinfo:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 MX 4000/PCI/SSE2
OpenGL version string: 1.5.6 NVIDIA 87.56
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
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
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
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x33 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x39 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3a 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3b 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3d 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None

```

glxgears:
```
1786 frames in 5.0 seconds = 357.033 FPS
1765 frames in 5.0 seconds = 352.919 FPS
1788 frames in 5.0 seconds = 357.583 FPS
1796 frames in 5.0 seconds = 359.007 FPS
1796 frames in 5.0 seconds = 359.097 FPS
1785 frames in 5.0 seconds = 356.955 FPS
1786 frames in 5.0 seconds = 357.007 FPS

```

Really, all of the interface is snappy and quick, its most noticeable in Firefox. I disabled smooth-scroll, but the program still stutters when scrolling down the page, and is slow to respond to mouse clicks, etc...

Other programs are not as slow, of course they are not displaying moving images like Firefox is (esp. when scrolling), so thats why it might be an X problem, or it could just be one with Firefox being slow...

---

### Post by 23meg on 2006-05-25
I don't think this has anything to do with 3D; it's obviously a 2D performance issue. Make sure you have the line ```
Option "RenderAccel" "True"
``` in the Device section of your /etc/X11/xorg.conf file, and that your processor's speed isn't scaled down against your will. To check what speed it's running at, type ```
cat /proc/cpuinfo |grep MHz
```

---

### Post by hbweb500 on 2006-05-25
Well, on a hunch, I upgraded to LTS, and everything is nice and fast now. Thanks.

BTW, I didnt have RenderAccel in my Xorg.conf, so I added it, otherwise the processor speed was fine.

---

### Post by thero on 2006-05-25
how would you disable cpu scaling as my processor goes up and down whenever i do something.  Is that bad for it?

---

### Post by pelle.k on 2006-05-25
I belive powernowd is the "program" responsible for frequency scaling in ubuntu.

If your CPU supports frequency scaling, it's generally a good thing. And no, it's not "bad" to the CPU at all. Even if your CPU doesn't support frequency scaling, you have nothing to worry about at all.

---

### Post by 23meg on 2006-05-26
```
sudo killall powernowd
```will kill powernowd and your processor will start running at maximum speed (probably). You can then select any speed you like with the frequency scaling panel applet or cpufreq-selector.

---

### Post by tha_rainman on 2006-05-26
which nvidia PCI card are you running? Maybe you have to install the legacy drivers package instead of the current ones.

[B]
*nvidia-glx-legacy*[/B]
[I]NVIDIA binary XFree86 4.x/X.Org 'legacy' driver
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
of OpenGL applications via a direct-rendering X Server and supports the TNT,
TNT2, TNT Ultra, GeForce, and GeForce2 chipsets. AGP, TV-out and flat panel
displays are also supported.

This is the 'legacy' driver for older chipsets.  Unless your chipset is
explicitly listed in the above paragraph, please use the nvidia-glx driver,
which is much more up to date.[/I]

To enable the driver, run "sudo nvidia-glx-config enable".

---

### Post by Sukarn on 2006-05-26
Hmm... "cat /proc/cpuinfo |grep MHz" shows "cpu MHz         : 1492.379"
whereas I am on an AMD Athlon 2400+ (1998 Mhz). I remember I saw it somewhere in Dapper that it had detected my cpu to be Athlon 1800.
Any help about this or should I start a new thread?

---

### Post by pelle.k on 2006-05-27
Before you start a new thread, make sure it says XP 2400+ in bios too, becuase BIOS is the first to set your CPU frequency. If BIOS sets it to a XP 1800+, dapper can´t do very much about it...

I must admit i don´t know if dapper changes processor identification name when scaling down the frequency either. if it does, then you need not worry much. just kill powernowd. (to unistall it sudo apt-get remove powernowd...)

---

### Post by Sukarn on 2006-05-29
[QUOTE=pelle.k]Before you start a new thread, make sure it says XP 2400+ in bios too, becuase BIOS is the first to set your CPU frequency. If BIOS sets it to a XP 1800+, dapper can´t do very much about it...

I must admit i don´t know if dapper changes processor identification name when scaling down the frequency either. if it does, then you need not worry much. just kill powernowd. (to unistall it sudo apt-get remove powernowd...)[/QUOTE]
When I boot my PC, on the second screen (the one where I can press DEL to get to BIOS), I can see it mentioning Athlon XP 2400+.
I tried "sudo killall powernowd" but that just said "powernowd: no process killed".
During system shutdown, I can see something like "Stopping powernowd...        OK".
Now, before I make a new thread, I just want to make sure that I am using the correct command to stop powernowd.
But I must say one thing, Windows used to overheat my PC, but in Ubuntu, it hasn't happened even once, even though its been run continuously for many hours.

"cat /proc/cpuinfo |grep MHz" again yeilded "cpu MHz         : 1491.950"

---

### Post by pelle.k on 2006-05-29
install cpufrequtils and paste the output of cpufreq-info please...

---

### Post by Sukarn on 2006-05-30
> :~$ cpufreq-info
cpufrequtils 0.4: cpufreq-info (C) Dominik Brodowski 2004
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU

Should I make a new thread for it?

---

### Post by Sukarn on 2006-05-30
Please forgive me... I remember having seen that a few days before installing Dapper.
[quote=Sukarn]When I boot my PC, on the second screen (the one where I can press DEL to get to BIOS), I can see it mentioning Athlon XP 2400+[/quote]

I just rebooted and paused at that screen... To my surprise, it was also saying Athlon XP 1800+.
Now, please dont flame me, and tell me whether I can get some help regarding that here.

---

### Post by pelle.k on 2006-05-30
Then i guess starting another thread (and if that doesn't help you, bug report)is the way to go. if cpufreq-utils reports no cpufrew driver, then there is no scaling going on...
If you have windows installed, and it reports xp2400, then you will know for sure dapper is the one to blame. i'm not surprised... dapper currently has some serious bugs left which is a shame considering it is to be released the day after tomorrow.

@sukarn;
If it reported xp1800 at the post-boot (where you can press del to get to bios) then dapper has absolutely nothing to do with your cpu being a xp1800, but your settings in BIOS. See what your FSB (Bus frequency) is at. On many systems it should be half of what your cpu is made for (333 mhz - 166, 400 mhz - 200 or whatever)

---

### Post by ticool on 2006-05-30
[QUOTE=Sukarn]Hmm... "cat /proc/cpuinfo |grep MHz" shows "cpu MHz         : 1492.379"
whereas I am on an AMD Athlon 2400+ (1998 Mhz). I remember I saw it somewhere in Dapper that it had detected my cpu to be Athlon 1800.
Any help about this or should I start a new thread?[/QUOTE]

Be sure your bios is correct... maybe it throttled down to 100mhz FSB, looks like this because the cpu multiplier 15x at 100mhz make 1500mhz and this looks like a AMD 1800+

---

### Post by Sukarn on 2006-05-31
OK, I checked the BIOS, and the FSB was at 100 MHz, I increased it (tried to increase it to 133 MHz but I think I messed it up to 166) and now something got messed up. The CPU won't boot if the battery is left in, and if the battery is taken out, the BIOS should reset. This happens, but even after resetting the BIOS, if I boot the PC, and then try to restart it, it won't start (with default BIOS). I have to cut off the power supply and then reconnect it to make it start. And the annoying thing is that if I leave the battery in it, it wont boot at all. I can just hear my DVD Drives humming (checking for a CD/DVD) but the screen remains off (the green power indicator on the screen keeps blinking, not constantly on as it would be if the computer was on).

Any help anyone? Or did I mess everything up?

**EDIT : **This has gone really off-topic. I am strongly considering a new thread about it and linking it to this thread.

---

### Post by graabein on 2006-06-05
I have some problems with direct rendering and a XFree86 error message!??

Here's my glxinfo and glxgears:

```
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: SGI
client glx version string: 1.2
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/AGP/SSE2/forceSW
OpenGL version string: 2.0.2 NVIDIA 87.62
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_EXT_abgr,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
```

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
27619 frames in 5.0 seconds = 5515.032 FPS
27954 frames in 5.0 seconds = 5570.642 FPS
26237 frames in 5.0 seconds = 5237.619 FPS
23521 frames in 5.1 seconds = 4648.731 FPS
```

I have done "sudo apt-get install nvidia-kernel-common nvidia-glx" and xorg.conf looks like this:

```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Extensions"
	Option 	"Composite" "Enable"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"		"true"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection

Section "Monitor"
	Identifier	"photon20visi"
	Option		"DPMS"
	HorizSync	30-80
	VertRefresh	56-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Monitor		"photon20visi"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
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
```

Application windows are slow when I drag them on screen and I want to try out XGL/Compiz... I have a gigabyte ram and nVidia GeForce 6600 GT. It should be more responsive. How do I get 3D rendering turned on?

---

