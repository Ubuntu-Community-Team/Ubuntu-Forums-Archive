---
title: "reinstalling ati driver without x?"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by Catalyst2Death on 2007-12-28
Ok, so I just reinstalled gutsy and got moved in.  I was trying to install Valve's orange box using wine, and one of the requirements was ATI's proprietary driver.  I tried the one from the ubuntu repositories, but it didn't allow any of the games to run.  I then proceeded to install the driver from Envy.  This worked well, however I began to notice problems, mainly x would crash whenever I tried to run gl apps (glxgears in particular)  so, I decided to remove the driver included with Envy, and use the driver included in the ubuntu repositories.

The long and short of it is, I hosed the uninstallation.  After envy removed the driver, I decided to restart x, and when x failed to load, I rebooted the entire machine.  Now I'm only left with the command line login (no x, essentially the recovery mode)  so, how can I reinstall the ati driver and get x back?  can I just modify xorg.conf?!  I'm going to bed now, but I'll piddle around with it in the morning a little more... I'm afraid envy removed some of the more essential files.  Any help would be greatly appreciated

---

### Post by sloggerkhan on 2007-12-28
sudo dpkg-reconfigure xserver-xorg 

is your friend. (it reconfigures your xserver.)

you can do most stuff by using the console VT and using nano + the startx command if you need to manually tweak the xorg.conf file in /etc/X11/xorg.conf

There are a lot of guides about ati cards because the fglrx driver == trouble.

Still, if you have more detailed questions, please post.

---

### Post by Catalyst2Death on 2007-12-28
Thanks for the help!  I'm back into X, which is good, this is what I've done to get it to work:

(Keep in mind that I don't have X running so I'm inputing all of my commands from a bash prompt)

Start by logging into your default user

After the NO WARRANTY warning, you're essentially in a terminal.

now type:
"sudo nano /etc/X11/xorg.conf"

now, use the arrows to move the cursor to the section for your video card which has your device's driver, mine was ahead of the section for the monitor.

then find the line "driver             'fglrx'"
and change it to "driver             'radeon'"

save changes by hitting ctrl+x and pressing y when prompted. 

This changes the driver from the proprietary fglrx to the opensource radeon driver.  Restarting the computer should allow X to load... (It did in my case!)

This now allows you to continue to screw around with installing the ati drivers as per tutorials and guides!

---

### Post by sloggerkhan on 2007-12-28
yep. Most of us ATI owners learn to become experts at first doing this to get the fglrx driver installed and running, and then to fix things when it gets hosed when we try to tweak it.

---

### Post by Catalyst2Death on 2007-12-29
so, unfortunately I got so frustrated with messing with this that I just reinstalled gutsy and went back to using the supported ati driver... there's no reason for me to try to continue to get the latest ati driver working right?  I was trying to run Portal, but I just give up... for now.  Anyway, ATI support sucks, and as much as I like ATI, I may switch to Nvidia if I continue my affair with linux.

for the record I could not get direct rendering to remain enabled... I would get the latest driver installed... I would check direct rendering, it would say enabled, and act nice... I would re-enable compiz to get all of the pretty window effects, restart X, and then check direct rendering again and it would be disabled.  I could not get any consistency with having it enabled or disabled... so finally I had a fit and did a throwback to the microsoft days when you fix a problem with a bulldozer when all you need is a scissors...

---

### Post by sloggerkhan on 2007-12-29
There are a couple of problems you might have. There are some settings that need to be enabled in the xorg.conf file, and by default, your graphics card is probably blacklisted in compiz.

Also, switching between the ati and the fglrx drivers will sometimes require a reboot, before which some things me not behave accurately.

Lastly, don't know what card you have, but that can make a major difference also.

I've got compiz-fusion working okay on a single screen using second to latest driver w/ my x700 mobility. Has weird quirks, like video only showing up in full screen mode.

This, and the fact that my card can't seem to drive compiz on 2 monitors mean I don't usually use it.

---

### Post by acoustibop on 2007-12-29
Catalyst2Death, I'd really recommend the current [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page") method: it seems much more reliable than applications like Envy which, although easy to run, often don't seem to get it right.

And it's not that difficult: it just involves copy + pasting lines into your terminal and making a few simple decisions.  But the bottom line is, it's always got the fglrx driver installed and running satisfactorily for me.

---

### Post by Catalyst2Death on 2007-12-31
I know what you mean,  anyway, after a short hiatus, and a decision to play some linux games, I have revisited my attempt to get the latest driver working.  I now fully understand the install process and can easily switch between the drivers.  I see a considerable performance increase switching between drivers (glxgears reports ~1000 fps on the default ubuntu one, and ~1600 fps on the latest ATI driver)

Right now I have the ubuntu proprietary driver running... direct rendering is off, however opengl games run fine, they just look odd... I've attached a picture of nexuiz to demonstrate what I mean.  Here is the output of the console as nexuiz launches:

```
 ./nexuiz-linux-686-glx 
Console initialized.
Nexuiz Linux 16:37:51 May 30 2007
Trying to load library... "libz.so.1" - loaded.
Compressed files support enabled
Added packfile data/common-spog.pk3 (26 files)
Added packfile data/data20070531.pk3 (3675 files)
Trying to load library... "libcurl.so.4" "libcurl.so.3" "libcurl.so" "./libcurl.so.4" "./libcurl.so.3" "./libcurl.so" - failed.
cURL support disabled
Initializing client
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Ogg Vorbis support enabled
couldn't exec config.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Starting video system
Video: fullscreen 800x600x32x60hz
Loading OpenGL driver libGL.so.1
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
checking for GLX_ARB_get_proc_address...  not detected
checking for GLX_SGI_swap_control...  not detected
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Xlib:  extension "XFree86-DGA" missing on display ":1.0".
Failed to detect XF86DGA Mouse extension
checking for OpenGL 1.1.0...  enabled
GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon Xpress Series
GL_VERSION: 1.2 (2.0.6473 (8.37.6))
GL_EXTENSIONS: GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias 
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_ARB_multisample 
Checking OpenGL extensions...
checking for glDrawRangeElements...  enabled
checking for GL_ARB_multitexture...  enabled
checking for GL_ARB_texture_env_combine...  enabled
checking for GL_ARB_texture_env_dot3...  enabled
checking for GL_EXT_texture3D...  not detected
checking for GL_ARB_texture_cube_map...  enabled
checking for GL_ARB_texture_non_power_of_two...  not detected
checking for GL_EXT_compiled_vertex_array...  not detected
checking for GL_EXT_texture_edge_clamp...  not detected
checking for GL_SGIS_texture_edge_clamp...  not detected
checking for GL_EXT_texture_filter_anisotropic...  not detected
checking for GL_EXT_blend_minmax...  enabled
checking for GL_EXT_blend_subtract...  enabled
checking for glStencilOpSeparate...  OpenGL extension "glStencilOpSeparate" is missing function "glStencilOpSeparate" - broken driver!
checking for GL_ATI_separate_stencil...  not detected
checking for GL_EXT_stencil_two_side...  not detected
checking for GL_ARB_vertex_buffer_object...  not detected
checking for GL_ARB_shader_objects...  not detected
OpenGL Backend starting...
glDrawRangeElements detected (max vertices 2147483647, max indices 2147483647)
multitexture detected: texture units = 8
OpenGL backend started.
Trying to load library... "libjpeg.so.62" - loaded.
JPEG support enabled
Trying to load library... "libpng12.so.0" - loaded.
PNG support enabled
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
SndSys_Init: using the ALSA module
Sound format: 48000Hz, 2 channels, 16 bits per sample
ioctl CDROMREADTOCHDR failed
CDAudio_Init: No CD in player.
Initial CD volume: 1
CD Audio Initialized
Draw_CachePic: failed to load gfx/m_white
Fake CD track 1 playing...
Client using port 0
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:32826
Server using port 26000
Server listening on address local:1
Server listening on address 0.0.0.0:26000
Loaded maps/aggressor.ent

```

I will write as my odyssey continues.

---

### Post by Catalyst2Death on 2007-12-31
I have a bit of a problem... I uninstalled compiz to install the ati driver and now when I start it doesn't load metacity on startup... so how do I enable it?!

---

### Post by Catalyst2Death on 2008-01-01
So  I fixed the metacity problem and cleaned everything out.  I followed the unofficial ati driver install guide exactly.  This is the result of my glxinfo:

```
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
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
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.4 (2.1.7170 Release)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x71 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x72 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x85 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

before it would report the mesa driver here, I seem to have remedied this problem.

the question now is how do I enable direct rendering?!

---

### Post by sloggerkhan on 2008-01-01
Is it enabled in your xorg.conf?

```

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "GLcore"
EndSection

```

and 

```

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

see:
[http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)

---

### Post by Catalyst2Death on 2008-01-01
That did the trick!  I didn't even have a section for modules in my xorg.conf!  This coupled with disabling compiz worked wonderfully (I am aware that there is a bug with compiz which disallows direct rendering...)  I have it all working as well as I need it, I can disable it whenever I need direct rendering. Thank you so much for all of your help!  I wish there was an Ahah! moment, but there really wasn't, I just had to follow all of the guides and not use automated scripts.

---

