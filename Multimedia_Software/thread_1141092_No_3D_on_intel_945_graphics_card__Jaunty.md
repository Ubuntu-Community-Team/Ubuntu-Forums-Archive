---
title: "No 3D on intel 945 graphics card / Jaunty"
date: 2009-04-28
forum: Multimedia Software
---

### Post by Monkey_Tales on 2009-04-28
Hello,
Can anybody help me to enable 3D on my intel 945GM card in Kubuntu?
Direct rendering is enabled, but 3D rasterization not.
Here is some information about my system:

:~$ glxinfo | grep direct
libGL: XF86DRIGetClientDriverName: 1.9.0 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tls/i915_dri.so
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
get fences failed: -1
param: 6, val: 0
disabling 3D rasterization
direct rendering: Yes


:~$ glxinfo
name of display: :0.0    
get fences failed: -1    
param: 6, val: 0         
disabling 3D rasterization
display: :0  screen: 0    
direct rendering: Yes     
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:        
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,     
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control,     
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group     
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,    
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync,      
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group     
OpenGL vendor string: Tungsten Graphics, Inc                                  
OpenGL renderer string: Mesa DRI Intel(R) 945GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.4                                                 
OpenGL extensions:                                                                  
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_multisample,              
    GL_ARB_multitexture, GL_ARB_pixel_buffer_object, GL_ARB_point_parameters,       
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,         
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,                                
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,                        
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,                                                                                                                        
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle,                                                                                                                      
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,                                                                                                                           
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,                                                                                                             
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,                                                                                                                             
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax,                                                                                                         
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, GL_EXT_cull_vertex,                                                                                                             
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture,                                                                                                                              
    GL_EXT_draw_range_elements, GL_EXT_framebuffer_object, GL_EXT_fog_coord,                                                                                                        
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil,                                                                                                                          
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters,                                                                                                      
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,                                                                                                           
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,                                                                                                       
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,                                                                                                                            
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,                                                                                                                              
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,                                                                                                                            
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,                                                                                                                     
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,                                                                                                           
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage,                                                                                                                      
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,                                                                                                                         
    GL_ATI_texture_env_combine3, GL_IBM_rasterpos_clip,                                                                                                                             
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,                                                                                                                    
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,                                                                                                                 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_point_sprite,                                                                                                               
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,                                                                                                         
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGIS_generate_mipmap,                                                                                                           
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,                                                                                                                       
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays                                                                                                            

36 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x7e 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x7f 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x80 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x81 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x82 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x83 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x84 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x85 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x86 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x87 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x88 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x89 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8d 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x8e 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x8f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x90 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x91 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x92 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x93 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x94 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x95 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x96 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x97 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x98 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x99 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x9a 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x9b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x9c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x9d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x58 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

36 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x59  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x5a  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x5b  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x5c  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x5d  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x5e  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x5f  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x61  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x62  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x63  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x64  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x65  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x66  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x67  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x69  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6b  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6c  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6d  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6e  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6f  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x70  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x71  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x72  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x73  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x74  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x75  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x76  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x77  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x78  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x79  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7a  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7c  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

:~$ ls -al /usr/lib/dri                                                                                         
totaal 36060                                                                                                       drwxr-xr-x   2 root root    4096 2009-04-20 20:25 .                                              drwxr-xr-x 323 root root  135168 2009-04-28 02:29 ..                                                 -rw-r--r--   1 root root 2249300 2009-04-18 00:01 i810_dri.so                                      -rw-r--r--   1 root root 2474740 2009-04-18 00:01 i915_dri.so                                 -rw-r--r--   1 root root 2512372 2009-04-18 00:01 i965_dri.so                                 -rw-r--r--   1 root root 2310712 2009-04-18 00:01 mach64_dri.so                           -rw-r--r--   1 root root 2364052 2009-04-18 00:01 mga_dri.so                                      -rw-r--r--   1 root root 2241076 2009-04-18 00:01 r128_dri.so                                -rw-r--r--   1 root root 2318196 2009-04-18 00:01 r200_dri.so                                       -rw-r--r--   1 root root 2327348 2009-04-18 00:01 r300_dri.so                                      -rw-r--r--   1 root root 2283288 2009-04-18 00:01 radeon_dri.so                        -rw-r--r--   1 root root 2216436 2009-04-18 00:01 s3v_dri.so                            -rw-r--r--   1 root root 2290744 2009-04-18 00:01 savage_dri.so
-rw-r--r--   1 root root 2306740 2009-04-18 00:01 sis_dri.so
-rw-r--r--   1 root root 2076832 2009-04-18 00:01 swrast_dri.so
-rw-r--r--   1 root root 2298420 2009-04-18 00:01 tdfx_dri.so
-rw-r--r--   1 root root 2160888 2009-04-18 00:01 trident_dri.so
-rw-r--r--   1 root root 2237020 2009-04-18 00:01 unichrome_dri.so

---

### Post by Monkey_Tales on 2009-04-28
I have installed the 3D driver with:

[B]sudo apt-get install xorg-driver-fglrx
[/B]
But afther restart the login screen went completely purple with stripes and i could not see the login box. So i had to remove the driver,** sudo apt-get remove xorg-driver-fglrx**, again for normal access to 9.04

Now i can login again, but not with 3D enabled.
Can anyone help me to get 3D support for the intel 945GM running?

---

### Post by zevans on 2009-04-28
The Intel driver is now xserver-xorg-video-intel. Do you have that package installed? If so, can you post your /var/log/Xorg.0.log please?

If not, then, erm, install it. :D

---

### Post by Monkey_Tales on 2009-04-28
> **zevans said:**
> The Intel driver is now xserver-xorg-video-intel. Do you have that package installed? If so, can you post your /var/log/Xorg.0.log please?

If not, then, erm, install it. :D


Here is the /var/log/Xorg.0.log:


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Maverick 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 28 23:21:03 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xeff00000/524288, 0xd0000000/268435456, 0xefec0000/262144, I/O @ 0x0000eff8/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.7.99
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, IGD_GM, IGD_G, 965G, G35,
    965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    Mobile Intel® GM45 Express Chipset,
    Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xEFF00000
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(==) intel(0): Using EXA for acceleration
(II) intel(0): 2 display pipes available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video0
(II) intel(0): Output TV has no monitor section
(II) intel(0): Resizable framebuffer: not available (1 3)
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.4.0
    ABI class: X.Org Video Driver, version 5.0
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x00000242 to 0x80000242
(WW) intel(0): PIPEBSTAT before: status: VSYNC_INT_STATUS LBLC_EVENT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: FIFO_UNDERRUN VSYNC_INT_STATUS LBLC_EVENT_STATUS VBLANK_INT_STATUS
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x10000000 to 0x000c0000
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710087
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x6b405140
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x800010bb
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00028283
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00014141
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 488960 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1955836 kB available
(WW) intel(0): DRI2 requires UXA
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(EE) intel(0): Failed to set tiling on front buffer: rejected by kernel
(EE) intel(0): Failed to set tiling on back buffer: rejected by kernel
(EE) intel(0): Failed to set tiling on depth buffer: rejected by kernel
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0xeff00000
(II) intel(0): [dri] visual configs initialized
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 31457280 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(WW) intel(0): drmDropMaster failed: Unknown error 4294967295
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0dbf4000 (pgoffset 56308)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x005fffff: compressed frame buffer (6144 kB, 0x000000007f800000 physical
)
(II) intel(0): 0x00600000-0x00600fff: compressed ll buffer (4 kB, 0x000000007fe00000 physical
)
(II) intel(0): 0x00601000-0x0060afff: HW cursors (40 kB, 0x000000007fe01000 physical
)
(II) intel(0): 0x0060b000-0x0060bfff: overlay registers (4 kB, 0x000000007fe0b000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x007bf000-0x0dbf3fff: DRI memory manager (217300 kB)
(II) intel(0): 0x0dbf4000-0x0f9f3fff: exa offscreen (30720 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x007bf000:            start of memory manager
(II) intel(0): 0x01000000-0x01ffffff: depth buffer (16384 kB)
(II) intel(0): 0x02000000-0x02ffffff: back buffer (16384 kB)
(II) intel(0): 0x03000000-0x03ffffff: front buffer (16384 kB)
(II) intel(0): 0x0dbf4000:            end of memory manager
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): [drm] mapped front buffer at 0xd3000000, handle = 0xd3000000
(II) intel(0): [drm] mapped back buffer at 0xd2000000, handle = 0xd2000000
(II) intel(0): [drm] mapped depth buffer at 0xd1000000, handle = 0xd1000000
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: XF86DRI Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 331 x 207
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event8"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Dell Premium USB Optical Mouse
(**) Dell Premium USB Optical Mouse: always reports core events
(**) Dell Premium USB Optical Mouse: Device: "/dev/input/event5"
(II) Dell Premium USB Optical Mouse: Found 7 mouse buttons
(II) Dell Premium USB Optical Mouse: Found x and y relative axes
(II) Dell Premium USB Optical Mouse: Configuring as mouse
(**) Dell Premium USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Dell Premium USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell Premium USB Optical Mouse" (type: MOUSE)
(**) Dell Premium USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Dell Premium USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Dell Premium USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Dell Premium USB Optical Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.99.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event9"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): [drm] mapped front buffer at 0xd3000000, handle = 0x2a600000
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (49.4 kHz)
(II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1301 1333 1440  800 804 808 823 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "AUO", prod id 5236
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.

---

