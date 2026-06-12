---
title: "The once and for all: &quot;Couldn't find matching GLX visual (Success)&quot; topic"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by warjowuch on 2006-11-13
**Hi everyone,**
This is once more a videocard 'howto 3d' topic, but I discovered many people have problems with this issue, but post them into other topics, or name their topics like the problem is something it's not. At least for me it is. So I decided to give this error a topic to cover it all (I hope the result will be like it! :-))

**Ok, here's the thing:**
I have had 3d accelleration working on my Ati 9200SE card (allthough this problem has, I think, nothing to do with ati itself, but more with other system-things, because the problem also appeared to nvidea-users) with both fglrx-drivers, xorg-xserver-video-ati drivers. Both on dapper as on Edgy (after dist-upgrade it still worked).

Now, I wanted to try the xorg-xserver-video-ati driver package. I installed it, changed my fglrx in xorg.conf to radeon and voilà, it worked. How nice. I have to say, it worked not so good as fglrx, but hey, aiglx sounds nice, does it not?
So, after a while I tried to add some lines to my xorg.conf in the device-section, some option-lines. This broke my screen-display,so I removed all of them, but it seemed to be related to AGPfastwrite/AGPmode 8x lines. So, I got my screen back. But, what the heck? My 3d stopped working?
I reïnstalled fglrx, removed xserver-xorg-video-ati and changed back my xorg.conf. Still nothing. I removed the 'radeon'modules from the kernel with rmmod in textmode and still: nothing.
Then I tried glxgears: they work pretty well with fps around 900. But the thing the problem occurred with was ppracer and just hit the spot:
******ppracer Error: Couldn't initialize video: Couldn't find matching GLX visual (Success)***

It seems to not being able to locate the glx-stuff. But still, when I do locate 'libglx' it finds it.
My xorg.conf loads glx and dri. In linux-restricted-modules-common I entered 'radeon' as disabled but nothing to solving the problem happens.

I followed quite some relevant guides, but still no luck. Some talk about a driver-upgrade resolved their problem, but I use the most uptodate driver from the repos (which I reinstalled several times): 8.28.

**Here is some glxinfo:**
> 
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
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)
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


**xorg.conf:**
> 
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

       # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "glx"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "GLcore"
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
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Modes"

    # 1400x1050 @ 85.00 Hz (GTF) hsync: 93.76 kHz; pclk: 179.26 MHz
	Identifier     "custom"
	ModeLine     "1400x1050_85.00" 179.3 1400 1504 1656 1912 1050 1051 1054 1103 -hsync +vsync
    # 1280x960 @ 85.00 Hz (GTF) hsync: 85.68 kHz; pclk: 149.43 MHz
	ModeLine     "1280x960_85.00" 149.4 1280 1376 1512 1744 960 961 964 1008 -hsync +vsync
EndSection

Section "Monitor"
	Identifier   "Philips 107P"
	UseModes     "custom"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "EnablePageFlip" "True"
	Option	    "RenderAccel" "True"
	Option	    "BackingStore" "True"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Graphics Adapter 0"
	Monitor    "Philips 107P"
	DefaultDepth     24
	SubSection "Display"
		Depth     4
		Modes    "1400x1050_85.00" "1280x960_85.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050_85.00" "1280x960_85.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050_85.00" "1280x960_85.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050_85.00" "1280x960_85.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050_85.00" "1280x960_85.00" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

From which the composite-thing has been enabled, disabled '0-ed' and removed from the thing, nothing does anything. load glx has been moved along the list in case loading order matters here.
If someone likes my xorg.0.log or something (don't know the exact name I think) I can post it also.
SO, here goes nothing: has anyone a really good idea how to solve this? Please, don't link me to threads or guides, I have seen them all but they seem to not handle this problem. I don't think it has something to do with the driver itself, it seems to be on another level.
Thanks in advance, good luck, enjoy and shoot me with questions!

---

### Post by warjowuch on 2006-11-14
*BUMP* I'd appreciate some reactions/usefull information :-) Thanks in advance!

---

### Post by warjowuch on 2006-11-15
Sorry, but an other Bump again...

---

### Post by warjowuch on 2006-11-16
allright... I tried a totally other course: I installed supertux-racer and that worked. So, direct rendering must have worked. So I decided to try to totally, completely remove ppracer and its configuration.
Guess what: it worked suddenly. This gave me another problem: how on earth could my ppracer be borked while changing video-drivers??? But well, it seems the problem is gone. Weird though, but lucky me!
So anyone who has this problem, I hope this information helps you!

---

