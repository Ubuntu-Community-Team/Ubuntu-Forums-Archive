---
title: "fglrx driver + dri hard locks dapper!"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by tmilam on 2006-06-05
Wow this is frustrating....I just want to play Warcraft 3 (which runs fine if I had my video card working).

Here's the problem: anytime I run any app that uses dri with the fglrx driver loaded, my machine hard locks and the only way to get it working again is to power cycle the computer. I was getting 2400 fps in glxgears and decent speeds in fgl_glxgears. But if I run either of these for more than, say, 10 seconds (I'm not fond of experimenting just to time it cause it's annoying to have your computer lock up!), it freezes completely.

](*,) 

Here's my relevant info:

```
vitriol@solstice:~$ uname -a
Linux solstice 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
vitriol@solstice:~$ glxinfo
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
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.5814 (8.25.18)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
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
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
```

I'm using the fglrx driver provided within ubuntu. At a loss here.....any help is appreciated. Thanks!

---

### Post by tmilam on 2006-06-05
Ok, it looks like it doesn't even take 10 seconds. And if I run those opengl apps at all and then close out of them quickly - or rather, try to close out of them at all - the b0x0r still l0x0rs. :-k

---

### Post by tmilam on 2006-06-05
Weird.....

I was suicidally running Warcraft 3, even though I knew that would lock up. And suprisingly, it didn't.

It just ran ridiculously slow. So slow it was unplayable. I tried running 'glxgears -printfps'

And it didn't crash and the framerate was normal! About 2400ish. Now, I'm  betting if   I run fgl_glxgears right now, that will lock it up.

---

### Post by adrianhensler on 2006-06-05
I feel your pain. I fI disable DRI then the system runs fine.... with no proper 3d. With DRI on; I get anywhere from 1 minute to maybe a few hours beforea  hard lock. What is funny is even though it is belly up; I can ssh in and see X taking 100%; but if I try to kill or restart it I get a 'real' lock.

Does anyone know how to troubleshoot this if I can ssh in? There's nothing showing in the xorg.0.log or dmesg or anywhere; the only thing that seems to happen is that X starts taking 100% (I can still move the mouse; but the screen is hung and even the numlock key won't toggle. But I can still ssh in and sometimes even sudo shutdown -r.

This 9700-aiw is going to be tossed soon. I've had some choice words for ATI lately.

---

### Post by Frank-Hamersley on 2006-06-06
This is similar to a problem I am having with fglrx on a HP dx5150 (Radeon X200) - as soon as X starts the system locks up - after playing the "I'm in trouble drum roll".

Will drop out the "dri" module and see if things improve!

Cheers, Frank.

---

### Post by tmilam on 2006-06-06
yeah, i can ssh into my machine too. and i'm getting the very same behavior you described. ](*,) ](*,) ](*,) 

and we're all stuck with no 3d acceleration :(

---

### Post by barney_1 on 2006-06-06
I can't even log in with DRI enabled on my 9800-aiw... locks at a blank screen before login.

Please post if you find a solotion.

---

### Post by Frank-Hamersley on 2006-06-06
[QUOTE=Frank-Hamersley]This is similar to a problem I am having with fglrx on a HP dx5150 (Radeon X200).

Will drop out the "dri" module and see if things improve!

Cheers, Frank.[/QUOTE]

No dice - just some complaints in the X log about the dri module being missing!  System still locks up - interestingly the screen (LG 32X32D HDTV) insists that there is no signal on the wire.

Cheers, Frank.

---

### Post by tmilam on 2006-06-06
Are you guys using the fglrx driver included in ubuntu, or did you build install it off of the ati website?

---

### Post by adrianhensler on 2006-06-06
[QUOTE=tmilam]Are you guys using the fglrx driver included in ubuntu, or did you build install it off of the ati website?[/QUOTE]

I've tried both; I'm currently using the ubuntu included one. They both seem equally unstable in my setup with 3d enabled (IC7-G 875 chipset board with P4-2.4)

---

### Post by Frank-Hamersley on 2006-06-06
Ditto - currently trying to get the distro version to work.

Cheers, Frank.

---

### Post by adrianhensler on 2006-06-06
I was wondering earlier if there is anything that I can look at - I can ssh in while X is locked; that works fine. But I don't see any interesting messages anywhere. I don't know enough about /proc to know if there is anything that I can check in there. Is doesn't seem to be a memory leak; not the kind that has X growing to use all available ram; it's more like a CPU loop. The mouse still moves around fine; I just can't do anything with it. I've tried restarting X and / or kdm while ssh'ed in; but that just causes a hard lock.

Anyone have any suggestions regarding places to look for possible errors or anything I can try while ssh'ed in? 

edit for spelling.

---

### Post by bjtuna on 2006-06-07
this is clearly a real problem, I'm finding multiple threads on this exact topic, none with solutions.  there's new drivers coming out from ATI fairly soon, hopefully that helps.

---

### Post by pascal_belron on 2006-06-07
I don t know if this is related (seems to me so but I m no expert at drivers development) but with my new setup (A64X2 and X1900XT), the fglrx driver just locks the machine during X bootup. Just a plain crash during the dri initialization (from what I see in the backtrace logged in Xorg.0.log), and the machine is locked up: have to hard reboot it. If I disable dri, everything works fine.

I don t know if ATI gives musch attention to this problem, as when you submit a ticked for Linus they say you should not expect any answer from them... So we need to find the common point in all of our machines that locks dri (actually has someone dri working with drivers 8.24 and above ?)

---

### Post by Frank-Hamersley on 2006-06-07
Removing the load of the dri module did nothing for me - except a few complaints in the X.log before it locked up.

I have now switched from fglrx to vesa which stops the lockups but the X still clags as soon as I log in.  At least the system doesn't crash now!

Cheers, Frank.

---

### Post by pascal_belron on 2006-06-07
Frank, How did u remove the loading of dri ? You got to add the line > Option "nodri" to the device section of your xorg.conf file.
It seems to work to most people here.

---

### Post by Frank-Hamersley on 2006-06-07
Good pickup - I just rem'ed it out!! Doh!  I will try the explicit approach later today.

Thanks, Frank.

---

### Post by Frank-Hamersley on 2006-06-08
No joy - just locks up - will interogate the logs later this arvo!

Cheers, Frank.

---

### Post by campnic on 2006-06-08
[QUOTE=Frank-Hamersley]No joy - just locks up - will interogate the logs later this arvo!

Cheers, Frank.[/QUOTE]

I have the same problem as you. (and about 100 others apparently)  I see the boot up screen (Ubuntu with the progress bar.  It gets to the point where X should start but a cursor blinks in the top left corner, then is replaced by a black screen.  Here is the contents of my xorg.log file:

```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15-ubuntu1 x86_64
Current Operating System: Linux ncampion-desktop 2.6.15-23-amd64-generic #1 SMP PREEMPT Tue May 23 13:45:47 UTC 2006 x86_64
Build Date: 16 March 2006

...

(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:5:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x18000
(II) fglrx(0): [drm] mapped SAREA 0x18000 to 0x2aaaadeae000
(II) fglrx(0): [drm] framebuffer handle = 0x19000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.25.18
(II) fglrx(0):     Date: May 18 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.15-23-amd64-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x0001a000
(II) fglrx(0): [pcie] 65536 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x0001e000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x00954000
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,1528)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		24 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1600 x 328

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x95) [0x476fe5]
1: /lib/libc.so.6 [0x2aaaab4271b0]
2: /lib/libc.so.6(strlen+0x30) [0x2aaaab468fc0]
3: /usr/bin/X(xf86XVScreenInit+0x997) [0x487f57]
4: /usr/lib/xorg/modules/drivers/fglrx_drv.so(KaleidoscopeInitVideo+0x8a) [0x2aaaaca173ca]
5: /usr/lib/xorg/modules/drivers/fglrx_drv.so(R200ScreenInit+0xc51) [0x2aaaac9eaec1]
6: /usr/bin/X(AddScreen+0x244) [0x430984]
7: /usr/bin/X(InitOutput+0x4b2) [0x45f8c2]
8: /usr/bin/X(main+0x2fb) [0x43025b]
9: /lib/libc.so.6(__libc_start_main+0xdb) [0x2aaaab41449b]
10: /usr/bin/X(FontFileCompleteXLFD+0x9a) [0x42f90a]

Fatal server error:
Caught signal 11.  Server aborting

```

Edited for length. Maybe my results just happen to be the same and i messed something else up.

---

### Post by pascal_belron on 2006-06-08
Campnic,

From your logfile, it seems fglrx is still trying to initialize drm (see all lines containing [drm]). Are you sure you put the line > Option "nodri" in the correct Device instance ? If you ran aticonfig, it created another device instance in your xorg.conf file. In my case, the signal 11 disappeared when I added this option.

---

### Post by Frank-Hamersley on 2006-06-08
OK - double Doh - first you have to put it in the correct section!

Now the system stays up (fglrx with nodri) but the X session keeps crashing.  A bit similar to campnic's situation.

Was going to fix the SecurityPolicy error FWIW.  Still don't what the 1:5:1 device is yet.

Cheers, Frank.

--------------------------------------------------------------
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15-ubuntu1 x86_64
Current Operating System: Linux hp5150dvt 2.6.15-23-amd64-generic #1 SMP PREEMPT Tue May 23 13:45:47 UTC 2006 x86_64
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  8 21:26:11 2006
(==) Using config file: "/etc/X11/xorg.conf"
(EE) end of block range 0x1fffffff < begin 0xe0000000
(WW) fglrx: No matching Device section for instance (BusID PCI:1:5:1) found
(EE) end of block range 0x1fffffff < begin 0xe0000000
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
error opening security policy file /etc/X11/xserver/SecurityPolicy

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x95) [0x476fe5]
1: /lib/libc.so.6 [0x2aaaab4271b0]
2: /usr/lib/xorg/modules/drivers/fglrx_drv.so(R200PointerMoved+0xe4) [0x2aaaac9e7da4]
3: /usr/bin/X(ProcessInputEvents+0x3b) [0x475f9b]
4: /usr/bin/X(Dispatch+0xbf) [0x44834f]
5: /usr/bin/X(main+0x4bc) [0x43041c]
6: /lib/libc.so.6(__libc_start_main+0xdb) [0x2aaaab41449b]
7: /usr/bin/X(FontFileCompleteXLFD+0x9a) [0x42f90a]

Fatal server error:
Caught signal 11.  Server aborting

---

### Post by pascal_belron on 2006-06-08
Hey Frank,

could you post your xorg.conf file: i d like to check why X is trying to init the PCI bus located on 1:5:1. 

Thks.

---

### Post by linuksamiko on 2006-06-08
I have the same problem with my ati card.
It is not a Ubuntu problem. I hade the same problems with all kinds of distros.

It is VERY unlikely that a new version of the driver will fix it. I'm waiting for a bugfix for 1 1/2 years.

I gues that it is a hardware problem. A few month ago I put in another card (didn't change any options) and the system worked absolutly stable (I had the other ati card for a few weeks to check the stability and it didn't lock up once). In another thread somebody wrote something about a thermal problem in another thread, I don't think it helps.
A bios-update didn't work for me neither.

Another reason could be xorg itself. During those Xfree86 time I didn't had any problems whit 3d. It all started when I changed to xorg.

I read alot of threads all over the internet but there was NO solution to this problem. Alot of people would be greatfull if we could find a solution (I would be greatful too) but it is unlikely.
Hopefully you could exclude certain problems with my post and hopefully somebody finds a sollution.

An idea of mine would be: taking a closer look at AGP on the mainboard, the graphic card and the kernel

It propably helps if everyone postes his hardware to compare (maybe we find something simmilar):

- ausu av7(something)
- ati radeon 9600pro
- 1.800 Athlon xp

---

### Post by adrianhensler on 2006-06-08
Can't hurt I guess.

IC7-G (Intel 875 chipset) and P4-2.4; ATI AIW 9700

Symptoms are that when 3d is enabled; random hard locks occur. It doesn't even matter if 3d is running; even if I just boot it and leave it at the logon screen it may lock. Sometimes I am good for hours; other times only for a few minutes. I can ssh in afterwards; but I can't find anything related to the error - just X taking up 100% of the CPU.

From dmesg everything looks normal except:

[4310490.632000] [fglrx:firegl_rmmap] *ERROR* map 0xc2a89750 still in use (map_count=1)
[4310490.632000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xc2a89740 still mapped


and

[4294785.286000] [fglrx:drm_parse_option] *ERROR* "agplock" is not a valid option
 (It's in my xorg.conf from before; I guess it's not valid anymore)

In Xorg.).log this stands out:

less /var/log/Xorg.0.log | grep WW

(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/local/" does not exist.
(WW) The directory "/usr/share/X11/fonts/Speedo/" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): Specified desktop setup not supported: 8
(WW) fglrx(0): Option "DynamicClocks" is not used


hm - not sure where that dynamicclocks is coming from; it's not in my xorg.conf?

Adrian

---

### Post by Frank-Hamersley on 2006-06-08
[QUOTE=pascal_belron]Hey Frank,

could you post your xorg.conf file: i d like to check why X is trying to init the PCI bus located on 1:5:1. 

Thks.[/QUOTE]

Here it is ... you will see an entry mentioning the 1:5:1 device - it was put there by me after I noticed it in the log.  I was hoping to give it a stub entry to associate with the device to make it happy, but I haven't connected it into a Screen.

Anyway the log reports are still as before.

Cheers, Frank.

---

### Post by pascal_belron on 2006-06-09
Specs can t hurt, this would be IMHO the first thing to do : try to find a similar pattern to understand on which hardware the drivers lock the machine. It would provide devs with a clue of where to look.

So my specs are as follows : Abit AT8 (chipset ATI RD480), A64X2 4400+ OCed to 2.3GHz (very conservative), Rad X1900XT (PCI-Express x16).

I submitted a ticked to ATI. Let s hope that if they receive many similar ticket their only resource working on the ATI drivers will spend some time working on this problem...

---

### Post by linuksamiko on 2006-06-10
[QUOTE=pascal_belron]
I submitted a ticked to ATI. Let s hope that if they receive many similar ticket their only resource working on the ATI drivers will spend some time working on this problem...[/QUOTE]

Let's hope so. I started a ticket about this issue almost one year ago and never got an answer or could see any progress in the driver. With more then one user complaining about it, it's a little more likely that they will do something. But don't expect toooo much.

---

### Post by L2wis on 2006-06-14
I've also got this problem with random lock ups, it's incredibly annoying. If you guys find a solution please let me know.

---

### Post by Eversmann on 2006-07-04
Sorry for bumping..

Could be this the problem? I found it here: [http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00789.html](http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00789.html)

, it's a bit old, but maybe that's the problem with our current kernel on ubuntu:

> I fixed the problem myself.
The problem was my kernelconfiguration. I compiled in "Support for frame
buffer devices -> ATI Radeon Display support". Apperently this was the
problem, because fglrx works well after I builded a new kernel without
this option.

---

### Post by Kephren on 2006-07-26
I am also having the same problem with a Radeon X700 Pro. It only happens if I intialize a 3D application. If I just use X then it will run with out any problems I have had it on for a week and have had no problems.

radeonFB will can mess up fglrx drivers, but Ubuntu loads vesafb and this does not effect this freezing problem.

---

### Post by tjennings on 2006-08-01
I have this problem as well, but I have noticed that it isn't an issue when I'm running a 386 kernel.  Not a solution, but it will save you a bit of frustration.

Specs:
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]

glxinfo reads:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
...
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 1.2 (2.0.5814 (8.25.18))

Kernel:
2.6.15-26-686 #1 SMP PREEMPT

Potentially related errors (although I only see these under Xgl):
[fglrx:firegl_pcie_lock_pages] *ERROR* unlocking pcie memory !
[fglrx:firegl_pcie_lock_pages] *ERROR* unlocking memory at 0xf3b0f680 for 16384 bytes

---

