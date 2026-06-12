---
title: "Trouble getting GLX to use hardware on other end of SSH/X11 connection."
date: 2009-12-01
forum: Multimedia Software
---

### Post by Defrector on 2009-12-01
I am having difficulty getting GLX-using programs to use hardware over SSH/X11. 

The situation is:
a headless server (with a rudimentary video card in case of an emergency)
a laptop with an ATI graphics accelerator.
These are connecting on a low-latency (0.2-0.4ms) 100mbps LAN with -C and -X flags on over HPN-SSH ([http://www.psc.edu/networking/projects/hpn-ssh/]("http://www.psc.edu/networking/projects/hpn-ssh/")) 

glxgears works, rss-glx works- it all "works" however it appears that all GLX programs on the headless side are rendering to the Mesa *software* rasterizer on the headless end then brute-force sending the whole frame over the network while GLX programs running locally on the laptop access the hardware directly. In situations where fullscreen or large rendering windows are involved this becomes very impractical. 3-4fps.

Is there a way to get the headless machine to use the laptop's hardware over GLX/SSH?

Here is glxinfo and the ssh login sequence from the laptop:
```
 
user@laptop:~$ ssh headless -XY -C -p 6699
Last login: Wed Nov 25 19:15:27 2009 from laptop
Linux headless 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/                               
user@headless:~$ glxinfo -display $DISPLAY        
name of display: headless:11.0                       
display: headless:11  screen: 0                      
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,          
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group     
OpenGL vendor string: Mesa Project                                            
OpenGL renderer string: Software Rasterizer                                   
OpenGL version string: 2.1 Mesa 7.6                                           
OpenGL shading language version string: 1.20                                  
OpenGL extensions:                                                            
    GL_ARB_copy_buffer, GL_ARB_depth_texture, GL_ARB_draw_buffers,            
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow,                  
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object,                        
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_map_buffer_range,         
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,          
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100,                       
    GL_ARB_shading_language_120, GL_ARB_shadow, GL_ARB_shadow_ambient,        
    GL_ARB_sync, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,     
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,                          
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,                  
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,                  
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle,                
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra,                        
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object,                  
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,           
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,                             
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,               
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,        
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,    
    GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements,                     
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord,     
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,                         
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,                       
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex,   
    GL_EXT_rescale_normal, GL_EXT_secondary_color,                             
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,                       
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side,                    
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,  
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,                         
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,                       
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,                      
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB,      
    GL_EXT_texture_swizzle, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra,     
    GL_3DFX_texture_compression_FXT1, GL_APPLE_packed_pixels,                  
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate,              
    GL_ATI_envmap_bumpmap, GL_ATI_texture_env_combine3,                        
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader,                        
    GL_ATI_separate_stencil, GL_IBM_multimode_draw_arrays,                     
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,                     
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_resize_buffers,  
    GL_MESA_texture_array, GL_MESA_ycbcr_texture, GL_MESA_window_pos,          
    GL_NV_blend_square, GL_NV_fragment_program, GL_NV_light_max_exponent,      
    GL_NV_point_sprite, GL_NV_texture_env_combine4, GL_NV_texture_rectangle,   
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1,    
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

8 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x66 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x67 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6a 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5d 32 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

8 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x5e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5f  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x60  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x62  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x63  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x64  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x65  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
```

Note how it mentions "Yes" for direct rendering, yet uses software rasterization. *scratches head*

...however when we look at the laptop's glxinfo locally we get a different story:
```
user@laptop:~$ glxinfo -display $DISPLAY
name of display: :0.0                              
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
OpenGL vendor string: DRI R300 Project                                        
OpenGL renderer string: Mesa DRI R300 (RS690 791F) 20090101  NO-TCL           
OpenGL version string: 1.5 Mesa 7.6                                           
OpenGL extensions:                                                            
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program,       
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,                  
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_shadow,           
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,                       
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,                      
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,                       
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,                     
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat,                   
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,                        
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_buffer_object,                    
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,       
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,                       
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax,   
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_convolution,  
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,        
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,                         
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,     
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,                    
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,         
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,                       
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,                         
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,                       
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,                
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,                        
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array,        
    GL_EXT_vertex_array_bgra, GL_APPLE_packed_pixels,                          
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3,               
    GL_ATI_texture_mirror_once, GL_ATI_separate_stencil,                       
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip,                       
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,               
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,            
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,     
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
0x66 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x67 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6a 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5d 32 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon

8 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x5e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5f  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x60  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x62  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x63  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x64  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x65  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
```

Info on the laptop's video hardware:
```
lspci | grep "ATI"
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
```

Both sides are up-to-date and use ubuntu 9.10.

...Ideally I'd like the headless GLX applications to transparently call the laptop's hardware rendering system instead of how it apparently is currently working: software-rendering and pouring entire frames through the network.

Any ideas/info/advice appreciated.

---

### Post by monraaf on 2009-12-01
Try this:

```

LIBGL_ALWAYS_INDIRECT=1 glxgears

```

---

### Post by Defrector on 2009-12-02
That did the trick, thanks much!:KS

---

