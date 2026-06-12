---
title: "[SOLVED] ATI drivers"
date: 2008-08-27
forum: Multimedia Software
---

### Post by 73ckn797 on 2008-08-27
Will the next release of Ubuntu fix the ATI video driver problems into a simple operation or a pre-configured part of the installation?

I have performed the Wiki How-To for the ATI driver and had no success. I tried the Envy and it fails. There are several others that I have tried that fail also. When the different methods for installing a driver, except the default, are performed they all keep the system from starting up.

ATI Radeon HD 3450

Is this a problem with all of the Ubuntu distros (K, X, Studio) including the 32 bit system?

---

### Post by eldirr on 2008-08-27
If you can put your xorg.conf file(under /etc/X11/) and /var/log/Xorg.0.log file, maybe we can solve that?

---

### Post by musta78 on 2008-08-27
Hi

Just solved the ATI driver installation.

Use this link and you will be ok.  Go to method 2!

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

It works fine on Xubuntu to, just use mousepad instead of gedit.

---

### Post by 73ckn797 on 2008-08-27
> **musta78 said:**
> Hi

Just solved the ATI driver installation.

Use this link and you will be ok.  Go to method 2!

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

It works fine on Xubuntu to, just use mousepad instead of gedit.

I went through all of that. I could have screwed something up but was trying to be very careful.

Should I only use method 2? It seemed to me that I was supposed to perform some of the first steps also. Could be wrong.

---

### Post by 73ckn797 on 2008-08-27
I will get those up tomorrow evening if a redo of the How-To fails again. That is if I know how to redo the How-To! Sound like a bad poet, don't I?

---

### Post by Crafty Kisses on 2008-08-28
Don't see why Envy didn't work, post the results of > glxinfo

---

### Post by 73ckn797 on 2008-08-28
Here is the "glxinfo" you requested.

 glxinfo
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
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
0x22 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x24 16 tc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x25 16 tc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x3e 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by 73ckn797 on 2008-08-30
Re: ATI drivers
Here is the "glxinfo" you requested.

glxinfo
name of display: :0.0
display: :0 screen: 0
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
GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
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

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
0x22 16 tc 0 16 0 r y . 5 6 5 0 0 16 0 0 0 0 0 0 0 None
0x23 16 tc 0 16 0 r y . 5 6 5 0 0 16 8 16 16 16 0 0 0 None
0x24 16 tc 0 24 0 r y . 5 6 5 8 0 16 8 16 16 16 16 0 0 None
0x25 16 tc 0 24 0 r . . 5 6 5 8 0 16 8 16 16 16 16 0 0 None
0x3e 32 tc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 0 0 Ncon

---

### Post by 73ckn797 on 2008-09-01
I will consider this thread solved since everything tried has failed and I really do not care to pursue to solution since it isn't even on my computer!!

No suggested solution has remedied the issue so I will cease pursuing an answer. I just will not run Ubuntu with an ATI video card, personally, and will never suggest anyone use ATI with Ubuntu.

---

### Post by tai1spin on 2008-09-01
In Xorg.conf file type the following under the 'Drivers' section. 

Option   "TexturedVideo"    true

this will enable Xv. after rebooting re-issue xvinfo and should have the ATI card listed

---

### Post by 73ckn797 on 2008-09-02
How will that correct the "out of range" msg and no further boot process? What is out of range, the resolution or textured setting?

---

### Post by soxs on 2008-09-02
```
cat /etc/X11/xorg.conf
```
post it in code tags
and post
```
cat /var/log/Xorg.0.log|grep fglrx
```
(in code tags aswell)

I have 3 systems up and running with different ati/amd graphics products (4870,3870,Mobile_blah)

Btw. which driver do you try to install, for me 8.6 is the last really usefull, 8.8 killed ETQW (only low res 640x480 is allowed, otherwise I will suffer from screen corruption :-S )

EDIT: Out of range means your monitor can't handle a that big resolution, you have to lower res and/or frequenzy.

---

### Post by 73ckn797 on 2008-09-02
Thanks. I will check that out and get back to you.

---

### Post by 73ckn797 on 2008-09-21
I am posting the successful results for getting my ATI Radeon HD 3450 video card working in Ubuntu Hardy. I tried many recommended solutions and all but given up until I found another users solution and tried that. 

Below are the steps that worked for me. I have made several minor revisions to the steps outlined originally. Step 6 has been inserted by me. I was not trying to run a dual monitor setup.

This is from a previously solved thread:
                                 **[http://ubuntuforums.org/showthread.php?t=821173](http://ubuntuforums.org/showthread.php?t=821173) **
  

[LIST=1]
[*]Re-install Ubuntu 8.04 from the     CD, overwriting the previous version *(annyoing but worth it,     since it worked)*.
[*]Login to user account, and ignore     *(for now)* all update notifications
[*]Click on the main menu     "**Applications** / **Add/Remove...**"
[*]Get **ATI binary X.Org driver**     and also get **ATI Catalyst Control Center**
[*]Once they are installed, close     "Add/Remove..." *(I might have been asked to reboot at     this point, if so I did and re-logged in)*
[*][I]_Installed restricted ATI driver from icon in task bar. Initially ignore this until step 5 had been performed. **edit:** reboot system for driver to take effect._
[/I]
[*]Click on the main menu     "**Applications** / **Other** / **ATI Catalyst Control     Center**"and make necessary adjustments.
[*]At this point, I click on the Update Notification icon and let it update everything.
[*]*_Other steps not used from original post that applied to dual monitor usage._*
[/LIST]
I give full credit to MaxMax for this basic procedure that he posted and have thanked him accordingly.

---

### Post by VanHammersly on 2008-10-10
Thank you, 73ckn797.  This worked perfectly for me.  Like you, I was pulling my hair out trying to figure it out.  One odd thing was that after step 6 I got an Over Range warning and black screen at log in.  I typed in my username and password, though, and was logged in and able to see my desktop.  I then made adjustments as stated in your post.  Thanks again.

---

### Post by 73ckn797 on 2008-10-10
> **VanHammersly said:**
> Thank you, 73ckn797.  This worked perfectly for me.  Like you, I was pulling my hair out trying to figure it out.  One odd thing was that after step 6 I got an Over Range warning and black screen at log in.  I typed in my username and password, though, and was logged in and able to see my desktop.  I then made adjustments as stated in your post.  Thanks again.

You are welcome and I am glad it worked out for you. I think each of us will have different results due to hardware differences.

---

### Post by SaddaGocaraRupa on 2008-10-30
> **soxs said:**
> ```
cat /etc/X11/xorg.conf
```
post it in code tags
and post
```
cat /var/log/Xorg.0.log|grep fglrx
```
(in code tags aswell)

I have 3 systems up and running with different ati/amd graphics products (4870,3870,Mobile_blah)

Btw. which driver do you try to install, for me 8.6 is the last really usefull, 8.8 killed ETQW (only low res 640x480 is allowed, otherwise I will suffer from screen corruption :-S )

EDIT: Out of range means your monitor can't handle a that big resolution, you have to lower res and/or frequenzy.

xorg.conf:
```
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

cat /var/log/Xorg.0.log|grep fglrx

```
(WW) fglrx: Force AIGLX enabled
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) Falling back to old probe method for fglrx
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0xc83460
(II) fglrx(0): === [atiddxPreInit] === begin
(II) fglrx(0): PCI bus 1 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon HD 4800 Series" (Chipset = 0x9440)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0502)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xe5000000
(--) fglrx(0): I/O port at 0x00009000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 11.3
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV770
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
(--) fglrx(0): Video RAM: 524288 kByte, Type: GDDR5
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000008, disabled=0x00000000
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: ACI  Model: 22a2  Serial#: 16843009
(II) fglrx(0): Year: 2008  Week: 14
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
(II) fglrx(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 31 H max: 81 kHz, PixClock max 170 MHz
(II) fglrx(0): Monitor name: VW222
(II) fglrx(0): Serial No: 83LMQS105145
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff000469a22201010101
(II) fglrx(0): 	0e120103802f1e78eec4f6a3574a9c23
(II) fglrx(0): 	114f54bfef00714f818081409500a940
(II) fglrx(0): 	b3000101010121399030621a274068b0
(II) fglrx(0): 	3600d9281100001c000000fd00384b1f
(II) fglrx(0): 	5111000a202020202020000000fc0056
(II) fglrx(0): 	573232320a20202020202020000000ff
(II) fglrx(0): 	0038334c4d51533130353134350a0056
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(**) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 37 modes found for primary display.
(--) fglrx(0): Virtual size is 1680x1050 (pitch 0)
(**) fglrx(0): *Mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 (75.0 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"x60.0   21.07  640 648 712 784  432 433 436 448 +hsync (26.9 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (470, 300) mm
(--) fglrx(0): DPI set to (90, 88)
(--) fglrx(0): Virtual size is 1680x1050 (pitch 1728)
(**) fglrx(0): *Mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 (75.0 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"x60.0   21.07  640 648 712 784  432 433 436 448 +hsync (26.9 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): Finished Initialize PPLIB!
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): detected X.org 7.4.2.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0x7fe4c6ffe000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.54.3
(II) fglrx(0):     Date: Oct 10 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.27-7-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01008000
(II) fglrx(0): FBMM initialized for area (0,0)-(1728,2432)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1050) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1728 x 1382
(==) fglrx(0): Backing store disabled
(II) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) fglrx(0): GLESX enableFlags = 26
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): UVD2 feature is available 
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) fglrx(0): Enable the clock gating!
```

??

---

### Post by Chainz on 2009-01-04
@ 73ckn797
Unfortunatelly your suggestions didn't help me, I still get terible performance (nearly lockups). :(

---

### Post by 73ckn797 on 2009-01-04
I had to perform a later re-install on the same machine and my original solution completely failed. I understand your dilemma. I abandoned further Ubuntu installation on that machine. My son was not real impressed with that issue, to say the least and wants nothing to do with Ubuntu. He is a gamer so Windows wins anyway for him. I will also say for me too, since I do not have to be messing around trying to get it (ATI) to work on his machine.

---

### Post by Chainz on 2009-01-06
Some how I just managed, after compiling and installing ATI Catalyst 8.12. 
But It didn't worked just like that, many reboots, driver and even xorg installations, turning proprietary drivers on and off, etc.

Totally not possible to reproduce - But finally! :D

---

### Post by Enrique Rocha on 2009-05-26
Help me i have a Diamond ATI Radeon X1550 Graphic Card that didn work in ubuntu 9.04 Jaunty 64 -bit.

---

### Post by 73ckn797 on 2009-05-26
> **Enrique Rocha said:**
> Help me i have a Diamond ATI Radeon X1550 Graphic Card that didn work in ubuntu 9.04 Jaunty 64 -bit.

I have not pursued configuring any ATI graphics cards since my earlier postings. I assume you tried any recommended drivers in System/Administration/Hardware Drivers?

---

