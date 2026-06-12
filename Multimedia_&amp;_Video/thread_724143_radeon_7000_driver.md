---
title: "radeon 7000 driver"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by koenjacobs on 2008-03-14
Hi everybody,
This is my problem: when I opened for the first time Call of Duty in Wine I got to following error:

*You should install the latest drivers for your video card, being sure to uninstall the old drivers first. If you already have the latest drivers, you should completely uninstall the drivers and then reinstall them. This fixes most problems. If the game still doesn't work, it may be that your video card does not have the minimum features required. Please check the readme for more information, including a list of supported video cards.*

This is a message I get in a console:

[I]COD 1.0 build win-x86 Oct  5 2003
----- FS_Startup -----
Current language: english
Current search path:
C:\Program Files\Call of Duty\main\pak6.pk3 (3 files)
C:\Program Files\Call of Duty\main\pak5.pk3 (4858 files)
C:\Program Files\Call of Duty\main\pak4.pk3 (1668 files)
C:\Program Files\Call of Duty\main\pak2.pk3 (694 files)
C:\Program Files\Call of Duty\main\pak1.pk3 (2642 files)
C:\Program Files\Call of Duty\main\pak0.pk3 (12828 files)
C:\Program Files\Call of Duty/main
C:\Program Files\Call of Duty\main\localized_english_pak1.pk3 (3736 files)
    localized assets pak file for english
C:\Program Files\Call of Duty\main\localized_english_pak0.pk3 (1204 files)
    localized assets pak file for english

File Handles:
----------------------
27633 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec config.cfg
couldn't exec autoexec.cfg
========= autoconfigure
configure.csv: using configuration 1200 cpu MHz 512 sys MB 64 vid MB
execing configure.cfg
fs_basepath is write protected.
fs_homepath is write protected.
Hunk_Clear: reset the hunk ok
...detecting CPU, found AMD w/ 3DNow!
Measured CPU speed is 1.36 GHz
System memory is 1012 MB (capped at 1 GB)
Video card memory is 64 MB
Streaming SIMD Extensions (SSE) supported

----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
Initializing OpenGL subsystem
...initializing QGL
...calling LoadLibrary( 'c:\windows\system32\opengl32.dll' ): succeeded
...setting mode 4: 800 600 FS
...using colorbits of 32
...calling CDS: ok
...registered window class
...created window@0,0 (800x600)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 32, 24, 8 )
...15 PFDs found
...hardware acceleration found
...PIXELFORMAT 1 selected
...creating GL context: succeeded
...making context current: succeeded
Initializing OpenGL extensions

GL_VENDOR: Tungsten Graphics, Inc.
GL_RENDERER: Mesa DRI Radeon 20061018 AGP 4x x86/MMX+/3DNow!+/SSE NO-TCL
GL_VERSION: 1.3 Mesa 7.0.1
GL_EXTENSIONS:  GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
----- CL_Shutdown -----
RE_Shutdown( 1 )
Shutting down OpenGL subsystem
...wglMakeCurrent( NULL, NULL ): success
...deleting GL context: success
...releasing DC: success
...destroying window
...resetting display
...shutting down QGL
...unloading OpenGL DLL
-----------------------
Hunk_Clear: reset the hunk ok
Your video card appears to be missing one or more features required to run Call of Duty.

You should install the latest drivers for your video card, being sure to uninstall the old drivers first.  If you already have the latest drivers, you should completely uninstall the drivers and then reinstall them.  This fixes most problems.  If the game still doesn't work, it may be that your video card does not have the minimum features required.  Please check the readme for more information, including a list of supported video cards.[/I]


Is it possible that there isn't a driver installed for my graphical card. It would really make sense to me because with windows I thought my desktop was more fluent (sorry). I also looked at the ati site, and there are drivers for linux but not for the Radeon RV100 QY [Radeon 7000/VE]
Already thanks
Koen p.s. Sorry for my bad English.

---

