---
title: "Is OpenGL 2.0 supported under ubuntu?"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by roger99 on 2006-12-10
I've just noticed after looking at glxinfo that my system is running opengl version 1.3, yet i was under the impression that 2.0 was the standard.  Is 1.3 the highest version available for linux or is there some way that I can install 2.0?

Just curious :D

---

### Post by fannus on 2006-12-10
Let me explain a few things that might help you out.

GLX is the operating system binding between Linux and OpenGL, OpenGL doesn't handle any OS specific stuff, like window management (and even important graphicsy stuff like framebuffers, which makes programming crossplatform a pain..).  Its counterpart in windows is called 'WGL', its version is completely independent from OpenGL.

OpenGL is just a specification, it will depend on the driver whether it implements any given version of the spec.  Some cards simply can't implement 2.0 because they don't have the features, like programmable shaders.  The only way you could be running below 2.0 is that
1.) your hardware can't support the 2.0 spec.
2.) your driver is old, and doesn't implement the 2.0 spec

When I run glxinfo, I get something like this, let me annotate it a bit with some C++ style comments

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes  //this means that we have 3d acceleration
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4  //GLX version, the implementation of this is also provided by nVidia
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float //see, framebuffer stuff!
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4 //opengl is a client-server model, so there are client and server versions..
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3 //info about extensions for an *older* GLX version
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation  //now we're at the meat of the nvidia driver
OpenGL renderer string: GeForce 7900 GS/PCI/SSE2
OpenGL version string: 2.0.2 NVIDIA 87.76 //w00t, version 2.0!
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 

.....

    (a bunch of extensions will follow)


I've noticed another common cause of confusion is what the hell Mesa GL is.  Mesa is a fully software driver implementation of OpenGL, not connected to hardware in any way.  This gives them the advantage of being able to implement the newest feature set on any system that has a CPU, but it will do everything on the CPU and be painfully slow.  So maybe if you need to test 2.0 features and don't care about real world performance, this could work for you.

The above glxinfo I posted was from my system running the 'nvidia' driver, not the 'nv' driver, I'm not sure if the 'nv' driver supports 2.0 or not.  So OpenGL 2.0 is not something that is supported or unsupported on ubuntu, it depends on your hardware and what driver you have to interface to that hardware.

If you want info on how to install the 'nvidia' driver, check out:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by roger99 on 2006-12-10
fair enough, glx version is 1.3.  Your explanation clears things up.  I was just wondering as my desktop with a nvidia 7800 gs and the latest nvidia beta drivers, and my laptop with intel integrated graphics were both running 1.3. But on closer inspection of the bits you highlighted I can see the desktop is using 2.0 and the laptop is still using 1.3.  Guess I'm gonna have to wait for better drivers for the laptop.

This is all because I have installed the irrlicht engine on the laptop and only get framerates of about 3fps with my code.  Guess i'll have to do all my opengl games coding on the desktop.

Thank you very much for the comprehensive answer

---

### Post by yasha on 2006-12-10
If that's the case, is there something wrong with my install? I noticed that direct rendering is not enabled, I did the compiz xorg mod for some of the extra eye-candy but I can't seem to get my compilation of gmplayer to work right with the normal gl, gl2, and xv drivers. The non-gui version "mplayer" works fine, and if I get the pre-compilied package gmplayer will also work fine, just doesn't have all the codecs and such that I want, so...

> 
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_SGIX_fbconfig, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 7900 GS/PCI/SSE2
OpenGL version string: 1.2 (2.0.2 NVIDIA 87.76)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_program, 
    GL_ARB_fragment_program, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_ATI_texture_mirror_once, GL_HP_occlusion_test, 
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_NV_texture_env_combine4, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


---

