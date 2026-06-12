---
title: "A bit of configuration help needed.."
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by IoCaster on 2006-08-27
Hardware list:

MSI K8N Neo4 Platinum
AMD64 X2 4400+
2GB DDR400
Nvidia 7950GX2
Dell 2405FPW
Dual Boot Ubuntu Dapper/WinXP Pro

Yesterday I installed an nvidia 7950gx2 card in my pc. I was running the 2.6.15-26-k7 w/smp kernel and nvidia-glx 8762 drivers. After a bunch of crashes and troubleshooting I got a clean boot, but no SLI. I then installed the 8774 drivers directly from nvidia. Did some wrangling and got a clean boot, but now compiz was broken. And I couldn't get SLI to work on the k7 kernel so I switched to 386. Reinstalled 8774 drivers, configured xorg.conf **again** and got a clean  boot with SLI enabled. Spent a bunch of time trying to get compiz to work on that configuration, but no joy.](*,) 

So all in all, a bunch of back and forth, with partial success, but no combination of kernels, drivers and configurations could get me all the features of my hardware enabled simultaneously.:-({|= 

Right now I'm back to k7-smp, 8774 drivers, no SLI and for some reason I haven't been able to get compiz to work again. As long as I'm going to sacrifice the SLI, I'd really like to get compiz back working. I'll try reverting back to the 8762's and see if that gets compiz working again.

Having said all that, I've got a weird situation here that I don't understand. Check out this glxinfo output and the subsequent glxgears result.


```
:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: No**  <------ ouch!
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
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
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7950 GX2/PCI/SSE2/3DNOW!/forceSW
OpenGL version string: 1.4 (2.0.2 NVIDIA 87.74)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_HP_occlusion_test, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fog_distance, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_texgen_reflection, GL_NV_texture_compression_vtc, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_multi_draw_arrays, GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
-----------------------------------------------------------------

:~$ glxgears
[B]71521 frames in 5.0 seconds = 14285.043 FPS
76100 frames in 5.0 seconds = 15219.997 FPS
69769 frames in 5.0 seconds = 13942.739 FPS
68937 frames in 5.0 seconds = 13770.233 FPS
71431 frames in 5.0 seconds = 14286.187 FPS[/B]<------ Huh!! 


```

It looks kind of strange to me, but then again I'm a bit of a linux n00b. If anyone can help me sort out my compiz or no k7-smp SLI problem I'd appreciate any suggestions.

---

### Post by IoCaster on 2006-08-27
After a bit of screwing about with drivers, kernels and such, I've settled on the k7 kernel. I'd rather have my dual cores working than have one of them sitting around with it's virtual thumb 'up it's butt'. At some point I'll make the transition to i686 and take full advantage of the hardware capabilities of this box. I'm still feeling my way around linux and have much more to learn yet.

I've also reverted back to the 'nvidia-glx' 8762 drivers. They seemingly don't have support for SLI on this kernel regardless of the efforts I've put forth to date, but I can live with that. I can always boot into windows for SLI gaming. It's really that simple, I'm not a fanatic about linux yet.  :)  

I've also gotten compiz working again with this configuration. Don't ask me how, I'm a total n00b!  :shock: 

I have to admit that the pace of change with that whole cgwd and compiz crowd is breathtaking in it's reckless disregard for stability. Daily updates/upgrades are a rollercoaster ride even for those who are inclined to live on the bleeding edge, but I digress.  :p  

Bottom line summation is that there's a problem with k7 and 9750GX2 support, at least for SLI anyway. The 8762 drivers will work, even though they don't recognize the card. Just have to do a bit of xorg config voodoo. The i386 will work fine with the 8774 drivers and SLI, but absolutely seem to hate compiz. At least, on my system they do. I'm fortunate in that I have the luxury of being able to just boot into windows for full support of my hardware, but I'm truly addicted to the Ubuntu experience now. It's so much more friendly for surfing the web, avoiding malware, desktop navigation and just endless tinkering than anything coming out of MS these days.  8)

Well, see ya folks later. I'm pretty sure that if I keep trying I can nuke this Ubuntu install until it glows in the dark. 

Wish me luck.  :twisted:

---

