---
title: "nvidia refresh very low"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by espikenl on 2007-07-07
Seems like this is a known issue, which will be fixed in ubuntu G, however, what i don't understand, is why my manual fixes down't work.
The situation is this: i have a nv7900 gs, running Ubuntu F (7.04) on a iiyama hm903dt a 19" monitor, and enabled the desktop effects.
It works, 3d accel works, everything is just..  peachy, and very wobbly.
Except for 1 little thing:  I'm getting a major headache, and epileptic tendencies from the max 68hz refresh rates.
What i've done so far, is check for my horizontal, and vertical refreeshrates, throw them in to an online modeline tool, and just copy pasted stuff in to the xorg.conf, which still let me start up the x server.
(current relevant xorg.conf) 
```
Section "Monitor"
	Identifier	"HM903DT"
	HorizSync	30-130
	VertRefresh	50-200
	Option		"DPMS"
        Modeline "1280x960_85.00"  149.43  1280 1376 1512 1744  960 961 964 1008  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7900 GS]"
	Monitor		"HM903DT"
	Defaultdepth	24
	SubSection "Display"
```

Now i might misplaced the modeline thing, never used that before, but verified from iiyama specs the horizontal, and vertical refresh should be ok i think
Next i added some options referred to in several topics, on the device part:
```
Section "Device"
	Identifier	"nVidia Corporation G71 [GeForce 7900 GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
        Option          "UseEdidFreqs" "False"
        Option          "UseEDID"      "False"
EndSection

```
i know, turning useEDID off, makes the above line not necessary, but shouldn't hurt it either

However, it's still stuck at 68hz, and i'm running a bit low on options 
if anyone could give me a hint where to look next, it would be really appreciated. 

added info:
```
lspci -n | grep 0300
01:00.0 0300: 10de:0292 (rev a1)
```

glxinfo:
```
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7900 GS/PCI/SSE2
OpenGL version string: 2.1.0 NVIDIA 96.31
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_HP_occlusion_test, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

```
I would understand if i were using some ubscure hardware with some specific settings, but this isn't the case here.
Maybe it is practical to add here, that the nvidia card, is a dual screen, although i currently only use one, and it has 2 dvi connectors on which i stuck a converter back to rgb

---

### Post by Mystique on 2007-07-07
hi,
got the same problem here

$ xrandr

gives me always the wrong refreshrates

i put in the xorg.conf under device section
    Option         "DynamicTwinView" "False" 

now i dont have twinview, but the right refresh rates


i dont know if this is a bug in xorg or in nvidia

give it a try
use xrandr bevor and after the change, and see if results fit your needs


mel

---

### Post by espikenl on 2007-07-07
Solved the issue right away.
Don't think i would've ever thought of turning that off, so tnx a lot.
Now i can get back to making stuff work

---

### Post by dakira on 2007-07-13
You won't believe how much I thank you for this. I had the same problem after upgrading from NVidia beta drivers to the current release. Your fix helped!

---

### Post by xer0kill on 2007-07-15
Thanks Mystique! I just installed a GeForce 7600GT and was having the same issue. I've been messing with this thing for hours and your post finally fixed it for me. No more seizures! :guitar:

---

