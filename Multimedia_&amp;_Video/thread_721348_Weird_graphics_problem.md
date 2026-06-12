---
title: "Weird graphics problem?"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by Metar on 2008-03-11
Having just returned to Linux last week after a two-year break, I found the installation of Ubuntu so much easier and more enjoyable (Sudoku is a great way to pass the time while installing :p) compared to the Debian I ran last time - and unlike my previous runs, everything worked perfectly this time. Internet, sound, they all worked flawlessly - apart from the graphics. After installing the VIA UniChrome Pro drivers for an Integrated GPU from VIA's website, games like Planet Penguin (TuxRacer?) started running at usual speeds again - but some issues remained. Being helpless as I am, I tried getting screenshots to show the problems. First of all, the text:

[http://img82.imageshack.us/img82/6910/screenshotplanetpenguinpr5.png](http://img82.imageshack.us/img82/6910/screenshotplanetpenguinpr5.png)

And then I encountered some freak rendering-issues in the game itself - notice how the fish and flags are rendered as weird flat things, except when very close while "driving" *very* slowly:

Far:
[http://img151.imageshack.us/img151/5527/screenshotplanetpenguinwf7.png](http://img151.imageshack.us/img151/5527/screenshotplanetpenguinwf7.png)
Near:
[http://img355.imageshack.us/img355/5045/screenshotplanetpenguinmr5.png](http://img355.imageshack.us/img355/5045/screenshotplanetpenguinmr5.png)
[SIZE="1"](Note: That black thing was the screenshot-tool)[/SIZE]

Also, the screensavers haven't gotten away unscathed, with the "Mirror Blob" getting the same rendering-issues:

[http://img353.imageshack.us/img353/4606/screenshotscreensaverprhg4.png](http://img353.imageshack.us/img353/4606/screenshotscreensaverprhg4.png)

As did a few others:

[http://img96.imageshack.us/img96/624/screenshotscreensaverpraw4.png](http://img96.imageshack.us/img96/624/screenshotscreensaverpraw4.png)
[http://img355.imageshack.us/img355/8901/screenshotscreensaverprgs4.png](http://img355.imageshack.us/img355/8901/screenshotscreensaverprgs4.png)

And Matrix didn't get away from the weird text either:

[http://img355.imageshack.us/img355/3902/screenshotscreensaverprug3.png](http://img355.imageshack.us/img355/3902/screenshotscreensaverprug3.png)


Now, I searched and googled for help: a thread here suggested running compiz, but that one required xgl, or forcing compiz to run without xgl. While it ran without xgl, the rendering-problem was solved (though the text remained squares), but the upper bar (orange thingy) disappeared. So, I tried to install xgl, hoping that would cure the problem - but instead, I messed up the X completely, left with the console alone. After a long uninstallation-process, I finally got X running again, without xgl - but I'm back to square one, with the rendering-issues and text-problem remaining.

Any suggestions?

---

### Post by kdarkentity on 2008-03-11
> **Metar said:**
> Having just returned to Linux last week after a two-year break, I found the installation of Ubuntu so much easier and more enjoyable (Sudoku is a great way to pass the time while installing :p) compared to the Debian I ran last time - and unlike my previous runs, everything worked perfectly this time. Internet, sound, they all worked flawlessly - apart from the graphics. After installing the VIA UniChrome Pro drivers for an Integrated GPU from VIA's website, games like Planet Penguin (TuxRacer?) started running at usual speeds again - but some issues remained. Being helpless as I am, I tried getting screenshots to show the problems. First of all, the text:

[http://img82.imageshack.us/img82/6910/screenshotplanetpenguinpr5.png](http://img82.imageshack.us/img82/6910/screenshotplanetpenguinpr5.png)

And then I encountered some freak rendering-issues in the game itself - notice how the fish and flags are rendered as weird flat things, except when very close while "driving" *very* slowly:

Far:
[http://img151.imageshack.us/img151/5527/screenshotplanetpenguinwf7.png](http://img151.imageshack.us/img151/5527/screenshotplanetpenguinwf7.png)
Near:
[http://img355.imageshack.us/img355/5045/screenshotplanetpenguinmr5.png](http://img355.imageshack.us/img355/5045/screenshotplanetpenguinmr5.png)
[SIZE="1"](Note: That black thing was the screenshot-tool)[/SIZE]

Also, the screensavers haven't gotten away unscathed, with the "Mirror Blob" getting the same rendering-issues:

[http://img353.imageshack.us/img353/4606/screenshotscreensaverprhg4.png](http://img353.imageshack.us/img353/4606/screenshotscreensaverprhg4.png)

As did a few others:

[http://img96.imageshack.us/img96/624/screenshotscreensaverpraw4.png](http://img96.imageshack.us/img96/624/screenshotscreensaverpraw4.png)
[http://img355.imageshack.us/img355/8901/screenshotscreensaverprgs4.png](http://img355.imageshack.us/img355/8901/screenshotscreensaverprgs4.png)

And Matrix didn't get away from the weird text either:

[http://img355.imageshack.us/img355/3902/screenshotscreensaverprug3.png](http://img355.imageshack.us/img355/3902/screenshotscreensaverprug3.png)


Now, I searched and googled for help: a thread here suggested running compiz, but that one required xgl, or forcing compiz to run without xgl. While it ran without xgl, the rendering-problem was solved (though the text remained squares), but the upper bar (orange thingy) disappeared. So, I tried to install xgl, hoping that would cure the problem - but instead, I messed up the X completely, left with the console alone. After a long uninstallation-process, I finally got X running again, without xgl - but I'm back to square one, with the rendering-issues and text-problem remaining.

Any suggestions?

Maybe you have the wrong graphics driver installed? What Graphics card do you have?

---

### Post by kdarkentity on 2008-03-11
Sorry i didn't mean to quote your original question...

---

### Post by Metar on 2008-03-11
> **kdarkentity said:**
> Maybe you have the wrong graphics driver installed? What Graphics card do you have?

I honestly have no idea - it's a built-in thingy, and both on Windows and Linux it fits one bundle of cards - [**[COLOR="Blue"]these[/COLOR]**]("http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=183") for Linux - and none of VIA's own identifying-tools can identify the specific one.

However, glxinfo raised this:

```
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x22
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  1 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x23 24 tc  1 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  1 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  1 24  0 r  y  .  8  8  8  0  0 32  0  0  0  0  0  0 0 None
0x27 24 tc  1 24  0 r  .  .  8  8  8  0  0 32  0  0  0  0  0  0 0 None
0x28 24 tc  1 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  1 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  1 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16 16  0 0 None
0x2b 24 tc  1 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16 16  0 0 None
0x2c 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16 16  0 0 None
0x2d 24 tc  1 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16 16  0 0 None
0x2e 24 tc  1 24  0 r  y  .  8  8  8  0  0 32  0 16 16 16 16  0 0 None
0x2f 24 tc  1 24  0 r  .  .  8  8  8  0  0 32  0 16 16 16 16  0 0 None
0x30 24 tc  1 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  0 0 None
0x31 24 tc  1 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  0 0 None
0x53 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

The first part looks suspicious...

---

### Post by PmDematagoda on 2008-03-11
The pictures have been removed as such large pictures are not allowed. The links have been left intact.

---

### Post by Metar on 2008-03-11
Sorry, I wasn't aware of the size limit.


As to the drivers, I have verified that they are correct - opening up the case revealed that I'm dealing with a P4M800Pro, which is one of those using the driver-package I linked to before.


Weird thing is, compiz *did* solve the rendering-issue, at a price though - and obviously didn't fix the text. :-k

---

### Post by Metar on 2008-03-16
With the lack of replies here, I have attempted to solve it on my own. Apparently, so I've found out, OpenChrome is a potential alternative... But it didn't turn out to work that well.

Actually, the 2D part works fantastic now - the text-glitches are gone. On the other hand, 3D became very, very slow - it's crawling at 1FPS, at best, on most of the 3D things, such as the basic 3D screensavers (ATunnel, Lavalamp, etc).


Any idea? Advice? (Hopefully one that doesn't include scrapping the card)

---

