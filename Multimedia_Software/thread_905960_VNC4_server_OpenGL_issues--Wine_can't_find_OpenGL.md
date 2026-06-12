---
title: "VNC4 server OpenGL issues--Wine can't find OpenGL"
date: 2008-08-30
forum: Multimedia Software
---

### Post by DOS4dinner on 2008-08-30
PC: ATI Radeon 9800 and Ubuntu 8.04.

Normally, I appear to be able to use my graphics card just fine.
glxgears gives me 5258 FPS miniscreen, and I get 350-450 FPS in fullscreen. I can run those 3D Tron lightcycle games perfectly, along with Defcon and other 3D games in Wine great.

However, when I try to run Wine through VNC4 server (I need to because the game I want to run--Sonic CD--ONLY runs in 256 colors), it says it cannot set up OpenGL. The tutorial I used is [here]("http://wiki.winehq.org/256ColorsWorkarounds"). I used the VNC part, as the Xnest did not want to work for some reason. (It crashes with some error--I could post what happens there if you think it would help)

This is what happens when I try to run Sonic CD:

```
name@name-desktop:~/.wine/drive_c/SEGA/SONICCD$ wine SONICCD.EXE
Xlib:  extension "GLX" missing on display ":2.0".
**err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems**
wine: Unhandled page fault on read access to 0x00000000 at address 0x7e1f090a (thread 0026), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e1f090a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e1f090a ESP:0032f268 EBP:0032f290 EFLAGS:00010202(   - 00      - -RI1)
 EAX:7c032ea0 EBX:7c032ea0 ECX:7c079f88 EDX:00000000
 ESI:7c07a770 EDI:00000034
Stack dump:
0x0032f268:  7c032ea0 7c032ea0 00000036 0032f2d0
0x0032f278:  7c07a968 7c07a1f8 b7d5625b 7e23b73c
0x0032f288:  7e23b73c 7c079f88 0032f2a0 7e1e9ba4
0x0032f298:  7e23b760 7e23b73c 0032f2b0 7e22c9bc
0x0032f2a8:  b7f3cff4 b7f3cff4 0032f500 b7f3432e
0x0032f2b8:  7c01cf10 00000000 00000036 7e7bc84c
Backtrace:
=>1 0x7e1f090a in libgl.so.1 (+0x2990a) (0x0032f290)
 2 0x7e1e9ba4 in libgl.so.1 (+0x22ba4) (0x0032f2a0)
  3 0x7e22c9bc glIsRenderbufferEXT+0x16c() in libgl.so.1 (0x0032f2b0)
  4 0xb7f3432e in ld-linux.so.2 (+0x1232e) (0x0032f500)
  5 0xb7f34bd7 in ld-linux.so.2 (+0x12bd7) (0x0032f530)
  6 0xb7c6ecb4 GLIBC_2+0xcb4() in libdl.so.2 (0x0032f540)
  7 0xb7f2f5d6 in ld-linux.so.2 (+0xd5d6) (0x0032f620)
  8 0xb7c6f2bc in libdl.so.2 (+0x12bc) (0x0032f640)
  9 0xb7c6ecea GLIBC_2+0xcea() in libdl.so.2 (0x0032f650)
  10 0xb7defd5f wine_get_es+0xa37() in libwine.so.1 (0x0032f680)
  11 0x7e853f65 in winex11 (+0x43f65) (0x0032f700)
  12 0x7e856027 X11DRV_wglGetProcAddress+0x27() in winex11 (0x0032f740)
  13 0x7ed0a48d wglGetProcAddress+0x6d() in gdi32 (0x0032f770)
  14 0x7e2a0bb5 InitAdapters+0x155() in wined3d (0x0032fc00)
  15 0x7e312f52 WineDirect3DCreate+0x22() in wined3d (0x0032fc30)
  16 0x7e4b91b5 in ddraw (+0x291b5) (0x0032fcb0)
  17 0x7e4b9d63 DirectDrawCreate+0xb3() in ddraw (0x0032fd00)
fixme:dbghelp_msc:pe_load_debug_directory This guy has FPO information
  18 0x00338151 in dmix (+0x8151) (0x0032fda4)
  19 0x0040a837 in soniccd (+0xa837) (0x0032fe44)
  20 0x0040821f in soniccd (+0x821f) (0x0032fe74)
  21 0x00411a9b in soniccd (+0x11a9b) (0x0032ff08)
22 0x7b8773a7 in kernel32 (+0x573a7) (0x0032ffe8)
0x7e1f090a: movl        0x0(%edx),%edx
Modules:
Module  Address                 Debug info      Name (77 modules)
PE        330000-  34d000       Export          dmix
PE        350000-  36b000       Deferred        lzxx
PE        400000-  43e000       Export          soniccd
PE      10000000-10020000       Deferred        dino2d
ELF     7b800000-7b92d000       Export          kernel32<elf>
  \-PE  7b820000-7b92d000       \               kernel32
ELF     7bc00000-7bca4000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca4000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e1c7000-7e241000       Export          libgl.so.1
ELF     7e241000-7e344000       Export          wined3d<elf>
  \-PE  7e250000-7e344000       \               wined3d
ELF     7e46c000-7e477000       Deferred        libgcc_s.so.1
ELF     7e487000-7e4de000       Export          ddraw<elf>
  \-PE  7e490000-7e4de000       \               ddraw
ELF     7e4de000-7e4f5000       Deferred        mcicda<elf>
  \-PE  7e4e0000-7e4f5000       \               mcicda
ELF     7e51d000-7e531000       Deferred        midimap<elf>
  \-PE  7e520000-7e531000       \               midimap
ELF     7e531000-7e557000       Deferred        msacm32<elf>
  \-PE  7e540000-7e557000       \               msacm32
ELF     7e557000-7e56e000       Deferred        msacm32<elf>
  \-PE  7e560000-7e56e000       \               msacm32
ELF     7e56e000-7e631000       Deferred        libasound.so.2
ELF     7e641000-7e677000       Deferred        winealsa<elf>
  \-PE  7e650000-7e677000       \               winealsa
ELF     7e677000-7e67c000       Deferred        libxfixes.so.3
ELF     7e67c000-7e685000       Deferred        libxcursor.so.1
ELF     7e685000-7e68b000       Deferred        libxrandr.so.2
ELF     7e68b000-7e693000       Deferred        libxrender.so.1
ELF     7e693000-7e696000       Deferred        libxinerama.so.1
ELF     7e696000-7e6b6000       Deferred        imm32<elf>
  \-PE  7e6a0000-7e6b6000       \               imm32
ELF     7e6b6000-7e6bb000       Deferred        libxdmcp.so.6
ELF     7e6bb000-7e6d3000       Deferred        libxcb.so.1
ELF     7e6d3000-7e6d5000       Deferred        libxcb-xlib.so.0
ELF     7e6d5000-7e6d8000       Deferred        libxau.so.6
ELF     7e6d8000-7e7bf000       Deferred        libx11.so.6
ELF     7e7bf000-7e7cd000       Deferred        libxext.so.6
ELF     7e7cd000-7e7d2000       Deferred        libxxf86vm.so.1
ELF     7e7d2000-7e7ea000       Deferred        libice.so.6
ELF     7e7ea000-7e7f2000       Deferred        libsm.so.6
ELF     7e802000-7e899000       Export          winex11<elf>
  \-PE  7e810000-7e899000       \               winex11
ELF     7e8b0000-7e8d1000       Deferred        libexpat.so.1
ELF     7e8d1000-7e8fb000       Deferred        libfontconfig.so.1
ELF     7e90b000-7e920000       Deferred        libz.so.1
ELF     7e920000-7e990000       Deferred        libfreetype.so.6
ELF     7e990000-7e9da000       Deferred        dsound<elf>
  \-PE  7e9a0000-7e9da000       \               dsound
ELF     7e9da000-7e9ed000       Deferred        libresolv.so.2
ELF     7e9fd000-7ea1b000       Deferred        iphlpapi<elf>
  \-PE  7ea00000-7ea1b000       \               iphlpapi
ELF     7ea1b000-7ea7c000       Deferred        rpcrt4<elf>
  \-PE  7ea30000-7ea7c000       \               rpcrt4
ELF     7ea7c000-7eb20000       Deferred        ole32<elf>
  \-PE  7ea90000-7eb20000       \               ole32
ELF     7eb20000-7ebc2000       Deferred        oleaut32<elf>
  \-PE  7eb30000-7ebc2000       \               oleaut32
ELF     7ebc2000-7ec54000       Deferred        winmm<elf>
  \-PE  7ebd0000-7ec54000       \               winmm
ELF     7ec54000-7eca6000       Deferred        advapi32<elf>
  \-PE  7ec60000-7eca6000       \               advapi32
ELF     7eca6000-7ed41000       Export          gdi32<elf>
  \-PE  7ecc0000-7ed41000       \               gdi32
ELF     7ed41000-7ee88000       Deferred        user32<elf>
  \-PE  7ed60000-7ee88000       \               user32
ELF     7efa8000-7efb3000       Deferred        libnss_files.so.2
ELF     7efb3000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff0000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c64000-b7c6d000       Deferred        libnss_compat.so.2
ELF     b7c6e000-b7c72000       Export          libdl.so.2
ELF     b7c72000-b7dc1000       Deferred        libc.so.6
ELF     b7dc2000-b7dda000       Deferred        libpthread.so.0
ELF     b7dea000-b7f20000       Export          libwine.so.1
ELF     b7f22000-b7f3e000       Export          ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        00000012    0
        0000000e    0
        0000000d    0
0000000f 
        00000015    0
        00000014    0
        00000011    0
        00000010    0
00000016 
        0000001a    0
        00000017    0
00000018 
        00000019    0
00000037 
        00000039    0
        00000038    0
0000001f (D) C:\SEGA\SONICCD\SONICCD.EXE
        00000024   15
        00000026    0 <==
Backtrace:
=>1 0x7e1f090a in libgl.so.1 (+0x2990a) (0x0032f290)
  2 0x7e1e9ba4 in libgl.so.1 (+0x22ba4) (0x0032f2a0)
  3 0x7e22c9bc glIsRenderbufferEXT+0x16c() in libgl.so.1 (0x0032f2b0)
  4 0xb7f3432e in ld-linux.so.2 (+0x1232e) (0x0032f500)
  5 0xb7f34bd7 in ld-linux.so.2 (+0x12bd7) (0x0032f530)
  6 0xb7c6ecb4 GLIBC_2+0xcb4() in libdl.so.2 (0x0032f540)
  7 0xb7f2f5d6 in ld-linux.so.2 (+0xd5d6) (0x0032f620)
  8 0xb7c6f2bc in libdl.so.2 (+0x12bc) (0x0032f640)
  9 0xb7c6ecea GLIBC_2+0xcea() in libdl.so.2 (0x0032f650)
  10 0xb7defd5f wine_get_es+0xa37() in libwine.so.1 (0x0032f680)
  11 0x7e853f65 in winex11 (+0x43f65) (0x0032f700)
  12 0x7e856027 X11DRV_wglGetProcAddress+0x27() in winex11 (0x0032f740)
  13 0x7ed0a48d wglGetProcAddress+0x6d() in gdi32 (0x0032f770)
  14 0x7e2a0bb5 InitAdapters+0x155() in wined3d (0x0032fc00)
  15 0x7e312f52 WineDirect3DCreate+0x22() in wined3d (0x0032fc30)
  16 0x7e4b91b5 in ddraw (+0x291b5) (0x0032fcb0)
  17 0x7e4b9d63 DirectDrawCreate+0xb3() in ddraw (0x0032fd00)
  18 0x00338151 in dmix (+0x8151) (0x0032fda4)
  19 0x0040a837 in soniccd (+0xa837) (0x0032fe44)
  20 0x0040821f in soniccd (+0x821f) (0x0032fe74)
  21 0x00411a9b in soniccd (+0x11a9b) (0x0032ff08)
22 0x7b8773a7 in kernel32 (+0x573a7) (0x0032ffe8)
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```

The bolded line tells me that it is probably not a problem with Wine, but something with my OpenGL set up.(This was said in a Wine forum too).

Output of glxinfo, if useful:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.1.7412 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

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
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
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
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x85 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  8 1 Ncon
```

Any ideas on what's wrong? I am a bit of a Linux/wine/openGL/VNC n00b. If there is something I am supposed to do other than what is in the tutorial, I probably did not do it.
Thanks in advance!

---

### Post by DOS4dinner on 2008-08-31
BUMPED! In the naaaammmeeee of love...before you break my CPU....

(Bumping is not illegal here, right? It's been 14 hours or so...)

---

### Post by DOS4dinner on 2008-09-02
BUMP! HAMMERTIME!
Final bump...I'll let it die after this.

---

