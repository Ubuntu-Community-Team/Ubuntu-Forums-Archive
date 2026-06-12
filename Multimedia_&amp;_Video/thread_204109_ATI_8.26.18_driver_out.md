---
title: "ATI 8.26.18 driver out"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by abstractgray on 2006-06-26
Not linked yet from the driver website, but it's on the driver notification RSS feed.

Release notes: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.26.18.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.26.18.html)

The driver itself (32-bit): [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run)

Trying it now...

---

### Post by abstractgray on 2006-06-26
*sigh* Still broken on my X1600. Time to put the 9600 back in and the X1600 back in a crate to gather dust, or else sell it to someone who can actually use it.

Unfortunately, there is (to my knowledge) no NVIDIA AGP card with a dual-link DVI port, or I wouldn't put up with this nonsense. Nor is there an easy way to get a PCI Express slot without buying a new CPU (the current one is an Athlon XP 2.16 GHz so there will be practically no speed benefit seen). This is ridiculous; the computer is only two years old.

---

### Post by Perfex on 2006-06-26
Well I will give it a try on my 9700 pro

---

### Post by Ranime on 2006-06-26
I've installed them with my X800VE...

this is what i get...
```
ranime@ishtar:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

ranime@ishtar:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None


```

damn... not too prommissing... ](*,)

---

### Post by evil_elman on 2006-06-26
Just two questions:

How long does it usually take for it to be available in the repositories?

Will the system give me a notification or do I have to update the driver manually?

---

### Post by whatever on 2006-06-26
[QUOTE=evil_elman]How long does it usually take for it to be available in the repositories?[/QUOTE]
as long as the new version does not fix some critical bug it will probably never reach the dapper repositories.

manual install: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually)

---

### Post by ltmon on 2006-06-26
Phoronix has it's usual excellent wrap up of all the changes in the new ati drivers here: [http://www.phoronix.com/scan.php?page=article&item=501&num=1](http://www.phoronix.com/scan.php?page=article&item=501&num=1)

---

### Post by rekahsoft on 2006-06-26
cool...it says it supports it...i will give it a try and report back :)

---

### Post by Ranime on 2006-06-27
YES!! I've got it up and running :D

Let's see how well it will do...

```
ranime@ishtar:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 VE Generic
OpenGL version string: 2.0.5879 (8.26.18)

ranime@ishtar:~$ glxinfo
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
OpenGL renderer string: RADEON X800 VE Generic
OpenGL version string: 2.0.5879 (8.26.18)
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
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3,
    GL_ATI_texture_float, GL_ATI_texture_mirror_once,
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object,
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3,
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
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

---

### Post by ltmon on 2006-06-27
[QUOTE=Ranime]YES!! I've got it up and running :D[/QUOTE]

For posterity what was it you did to fix it since your last post?

Cheers,

L.

---

### Post by MikeMLP on 2006-06-27
Complete newb here, trying to get the latest driver.

I noticed that there is an option to build a driver for Ubuntu 6.06, and that is the option I would like to take, but I keep getting an error when using the following command (everything looks right to me)

Command:.# sudo sh ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/6.06

Error:

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.26.18..................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/dapper
./packages/Ubuntu/ati-packager.sh: line 55: dpkg-architecture: command not found
Error: unsupported architecture:
Removing temporary directory: fglrx-install

and for the future, how do you enter code in the forum, so I don't end up filling up the page?

Thanks a lot, folks!

---

### Post by francescob on 2006-06-27
does anybody knows if this driver solve the issues with the radeon xpress 200m chip?
thank you
francesco

---

### Post by jhr79 on 2006-06-27
[QUOTE=francescob]does anybody knows if this driver solve the issues with the radeon xpress 200m chip?
thank you
francesco[/QUOTE]

Look for the web page mentioned in the post #7. It says:

> One of the very heated issues that was introduced into the fglrx 8.25.18 display drivers was the broken support for the Radeon R200 family. Though a workaround is available, many in the community have been frustrated by this problem. Well, the R200 OpenGL API entry-point issue still has not been resolved in the 8.26.18 release. ATI Technologies is continuing to investigate the issue; however, there is no word yet when they anticipate a fix. ATI will address the issue with a knowledge base article.

So it seems that they have not resolved issues regarding xpress 200M chipsets.

---

### Post by Ranime on 2006-06-27
Well... same problem as with the 8.25.x drivers... <10 mins of gameplay and it crashes or I'm thrown back in to gdm...

Time for a nVidia card I guess...

---

### Post by debernardis on 2006-06-27
I have 8.26.18 up and running after automatic installation (I was unable to make them work after generating deb packages :(  ). BTW on 2.6.17 kernel.
I hoped that suspend-to-ram was enabled in these new drivers, but on my laptop they crash just like 8.25.18 ](*,)  (unless there's something wrong on my side).

---

### Post by domino on 2006-06-27
It works for those with the 9800 Pro with the latest kernel and xgl/compiz. I have not noticed any noticeable enhancements and I can not comment on game play.

---

### Post by Ranime on 2006-06-28
[QUOTE=ltmon]For posterity what was it you did to fix it since your last post?

Cheers,

L.[/QUOTE]
I went to recovery mode (single user mode, terminal, sudo init 1) and removed all fglrx pakages:
```
root@ishtar:~#apt-get remove xorg-driver-fglrx fglrx-kernel-source fglrx-control
```

When you do this it is possible you get an error message telling you */usr/lib/fglrx/libGL.so.1.2.xlibmesa* cannot be removed or overwritten or something... do the following in that case, and only in that case:
```
root@ishtar:~#rm /usr/lib/fglrx/libGL.so.1.2.xlibmesa
root@ishtar:~#apt-get remove xorg-driver-fglrx fglrx-kernel-source fglrx-control
```

reboot in to recovery mode (single user mode) and follow this howto:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

Use method 2, use *8.26.18* where it says *8.25.18*!

before rebooting I also did the instructions from this thread [http://www.ubuntuforums.org/showthread.php?t=197471]("http://www.ubuntuforums.org/showthread.php?t=197471") except the things I already did in the first howto mentioned earlier.

Dont forget to change your */etc/X11/xorg.conf*, check mine below to see how.
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

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
	Load    "GLcore"
	Load	"glx"
	Load	"dri"
	# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
  	SubSection "extmod"
    	    Option "omit xfree86-dga"
  	EndSubSection
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. [COLOR="Red"]RADEON X800 VE (R420 4A54)[/COLOR]"
	Driver		"fglrx"
  	Option 		"NoDDC"
  	Option 		"VideoOverlay" 		"on"
  	Option 		"OpenGLOverlay" 	"off"
  	Option 		"UseInternalAGPGART" 	"no"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	60-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. [COLOR="Red"]RADEON X800 VE (R420 4A54)[/COLOR]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1152x864"
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

Do a reboot (init 6), when you first get an X crash, check your /var/log/xorg.log file for the chipsets supported by the 8.26.18. See if your chipset is there and change that in  your xorg.conf with nano or vi. see the red parts in my xorg.conf, what I've changed.

Reboot and it worked for me :)

---

### Post by flapane on 2006-06-28
I get [http://pastebin.ca/73772](http://pastebin.ca/73772) damn

---

### Post by Arathorn on 2006-06-28
[QUOTE=whatever]as long as the new version does not fix some critical bug it will probably never reach the dapper repositories.

manual install: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually)[/QUOTE]
Doesn't it get added to the backports repository either?

---

### Post by Tourmaline on 2006-06-28
Tested 8.26.18 on Radeon Mobility 9000 and still no direct rendering. Shame to ATI !

Here is an excellent thread to install/generate package with the last known driver version ( 8.24.8 ) enabling direct rendering :

[http://ubuntuforums.org/showthread.php?t=189000&page=3&highlight=Trouble+Installing+ATI+Drivers](http://ubuntuforums.org/showthread.php?t=189000&page=3&highlight=Trouble+Installing+ATI+Drivers)

go on : Generating/Installing Ubuntu packages for the 8.25.18 drivers in Ubuntu Dapper Manually from Ivhassel. 8.25.18 actually don't enable direct rendering but the link to get the drivers point to 8.24.8 version.

---

### Post by domino on 2006-06-28
domino@dapper:~$ glxinfo |grep rendering
direct rendering: Yes

I got that after adding **Option   "XaaNoOffscreenPixmaps"** to xorg.conf. If not added, dr is disabled.

I'm on the 9800 Pro, dist updated, XGL. BTW, what does direct rendering do? I mean with dri off, I don't have any problems with movies, xgl/compiz or any other graphics related issues. Is dr mainly for gaming?

edit: uhh forget that last question... It helps to google sometimes :). Anyway, with DRI enabled, glgears is only half of with DRI disabled. Is that nnormal?

DRI: 24110 frames in 5.0 seconds = 4821.900 FPS
NO DRI: 45527 frames in 5.0 seconds = 9093.019 FPS

Is this right?

---

### Post by domino on 2006-06-28
Hi, sorry to double post but I think this is important and related to my last post. I do have direct rendering support BUT only under normal Gnome. If I log into XGL, direct rendering is disabled.

So, as far as my **Option "XaaNoOffscreenPixmaps** comment, I don't think that's relevant.

---

### Post by debernardis on 2006-07-01
[QUOTE=debernardis]I have 8.26.18 up and running  [...] I hoped that suspend-to-ram was enabled in these new drivers, but on my laptop they crash just like 8.25.18 ](*,)  (unless there's something wrong on my side).[/QUOTE]

There was something wrong on my side, indeed :p 

So, if your 8.26.18 do not come back to business with a resume after suspend-to-ram, just edit /etc/default/acpi-support adn uncomment the line ```
DOUBLE_CONSOLE_SWITCH=true
```

This was needed on my hp zv6278ea pavilion with ati radeon 9200, 2.6.17 kernel, kubuntu dapper with kde 3.2.3. Now suspend-to-ram does not hang the video driver after resume.

---

