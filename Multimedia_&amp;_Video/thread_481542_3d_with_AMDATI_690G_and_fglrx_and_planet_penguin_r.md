---
title: "3d with AMD/ATI 690G and fglrx and planet penguin racer"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by mike_sierra on 2007-06-22
Hello together,

i have just installed ubuntu feisty on my new pc which has an  ASUS M2A-VM
motherboard with an integrated graphic chip 690G from AMD/ATI.

In general everything works fine. 

Using the  System–>Administration–>Restricted Drivers Manager.

it was very easy to install the ATI fglrx  driver  and after restart of the xserver
the desktop  is still ok.

the command  fglrxinfo gives me:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress 1200 Series
OpenGL version string: 2.0.6334 (8.34.8)

glxgears  is ok and glxinfo gives me:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

.....

A further test with the game chromium was  ok too, BUT:

When i start PLANET PENGUIN RACER i get a BLACK SCREEN and can only hear the intro music.

There is no way to go out than to restart the x server.

I had the same situation   some time ago with an old NVIDIA card and investigating the forum  and google i am not the only one who has this problem  .

Is there any one  who can give me a hint?


 
for the experts i give the whole glxinfo  

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
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress 1200 Series
OpenGL version string: 2.0.6334 (8.34.8)
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
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend,
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_separate_stencil,
    GL_ATI_shader_texture_lod, GL_ATI_texture_env_combine3,
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_ATI_vertex_streams,
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

By the way, hardware accelerated video using XV is not possible with e 690G chip

xvinfo gives me
X-Video Extension version 2.2
screen #0
 no adaptors present
monika@monika-desktop:~$
monika@monika-desktop:~$       

Best regards and hope to hear from you experts: Mike

---

### Post by mike_sierra on 2007-06-24
Hello together,

i did some further investigations concening planet penguin racer and the black screen.
First there seems to be no known bug and in any way no solution. Some people tell that they could get this game back running by installing an older version or just a version from debian instead of ubuntu. Is there anyone using an AMD690G where planet penguin is running fine?

I want to get shure , if this is a problem of  the amd chip or not.

Another question: running glxgears with default window size in forgruond i get only 120 FPS, although glxinfo is telling me that 3d is working . I cannot believe, that the amd chip realls is so slow compaired to several  1000 FPS i could read about.
Is there anyone using this amd chip to check if he /she  gets a similar benchmark value?

Last not least: 
in my original post i write, that xv is not working because
xvinfo gives me
 X-Video Extension version 2.2
 screen #0
 no adaptors present

After reading some posts towards XV, i am no longer shure,  if this means, that the chip hardware does not support xv at all, or if this means, that the driver currently does not support Xv (and hopefully does it in future)

Is there anybody who can tell me what is right?

I appriciate any comment: 

best regards: Mike

---

### Post by Ziox on 2007-06-24
you are not running desktop effects/compiz/beryl are you?

---

### Post by mike_sierra on 2007-06-24
Hello Ziox,

no i am not running desktop effects.


I did the default installation of ubuntu first. This  gave me a low resolution desktop using the standard vga driver, because ubuntu is not able to detect my card. Afterwards i used the administration of restricted devices and with one click activated the already installed fglrx.

Thats all what i had to do and it works fine beside the facts mentioned in my post.

best regards: Mike

---

### Post by mike_sierra on 2007-06-25
Hello together,

i could get  planet Penguin racer  run again and its running fine and fast enough. 

Therefore i had to do a complete reinstall   of my ubuntu. This time i used the original ubuntu desktop live cd which i downloaded before.  The first time i had installed from a live DVDwhich was part of a german linux magzine containing and installing not only ubuntu but also kubuntu and xubuntu. Indeed original packages but may be some of the additinal packages had an impact on Planet Penguin racer.

Well, I am very shure i never get the reason but well it works and i am glad that the problem was not a matter of the AMD 690G chip which works fine. I see this thread as closed  and will open another one concerning my XVideo matter and the slow 3d performance benchmark from  glxgears. 

Best regards: Mike

---

### Post by crumja on 2007-12-28
It's a well known problem that the 690G series aka X1200 do *NOT* support Xv as an output module. This is apparent when one types xvinfo and finds no adaptors present. This issue has been in existence for several release cycles and does not seem like it's going to be resolved. I have been in contact with AMD support on this matter and they responded with their typical "We do not support Linux." I have heard people having success with mplayer and sdl output on fglrx though.

I am using radeonhd right now and it works without any problems. 2d updates and refreshes seem way faster than fglrx. But both 2D and 3D are not hardware accelerated, so games, compiz, Xv won't work. That doesn't mean that full screen video doesn't play, because they're still blocky like fglrx, but not nearly as bad and actually very tolerable considering it's done on cpu.

In the coming months, all of those features missing in radeonhd will be added as more documentation drop and devs spend more time playing with DRM and the hardware. Support radeonhd!

---

### Post by Yellow Pasque on 2007-12-28
Yeah, I have an X1250 and made the jump to radeonhd. Any day now, AMD is set to release the RS690 specs and we should see some real improvement.

---

