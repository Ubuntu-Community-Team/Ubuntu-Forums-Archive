---
title: "How to install sound drivers in Ubuntu for Asus M2N-MX motherboard"
date: 2013-02-19
forum: Multimedia Software
---

### Post by tlotr on 2013-02-19
Hi All,

Need some help in installing the sound drivers in Ubuntu 12.10. I have downloaded the drivers from Asus website which contains these below 5 files: 

I have no idea what to do with these files. Please help me in installing the drivers.

1. alsa-driver-1.0.11.tar.bz2
2. alsa-lib-1.0.11.tar.bz2
3. alsa-tools-1.0.11.tar.bz2
4. alsa-utils-1.0.11.tar.bz2
5. Readme.txt

---

### Post by Yellow Pasque on 2013-02-19
> I have no idea what to do with these files.
Delete them because they're ancient.

The best way to update your driver is to: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

Here's the .deb you (not other people reading this) want:
[https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+files/alsa-hda-dkms_0.201302182033%7Equantal1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+files/alsa-hda-dkms_0.201302182033%7Equantal1_all.deb)

---

### Post by Yellow Pasque on 2013-02-19
If it still doesn't work after that, file a bug, which will automatically gather your ALSA info.
```
ubuntu-bug alsa-base
```

Try to remember to post the bug link in this thread.

---

### Post by tlotr on 2013-02-19
Hi Temujin,

Thanks for the reply. I have installed the deb files.

Actually the reason I wanted to install the motherboard sound drivers is because I have installed these three games Assault Cube, Quake III Arena & Enemy Territory.

I am unable to get sound in Quake III Arena and Enemy Territory game the sound works fine in Assault Cube. I don't know why the sound is not working on these two games. The only difference between these two games and Assault Cube is that I installed Assault Cube from Ubuntu software centre and the other two were downloaded from an ftp site and has a .run extension whereas Assault cube had a .deb extension.

Would you be able to help me in enabling the sound for these games or if you can provide any links where I can get the answers or there is any video tutorial for this. 

Thanks in advance.
[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=327594")

---

### Post by Yellow Pasque on 2013-02-19
Enemy Territory uses OSS for sound, which is not supported in Ubuntu. Try emulating using padsp, where <command> = whatever command starts ET:
```
padsp <command>
```

---

### Post by tlotr on 2013-02-19
Hi Temujin,

Thanks for the reply. I have tried it but still there is no sound in Enemy Territory.

---

### Post by tlotr on 2013-02-19
Hi Temujin,

The issue is resolved. I am able to get the sound now in ET and Quake 3 both.

---

### Post by Yellow Pasque on 2013-02-19
And how did you do that (for my benefit as well as anyone else encountering this thread)?

After explanation, please mark thread solved.

---

### Post by tlotr on 2013-02-19
Hi Temujin,

Below is the solution. Also please let me know how to make this thread to show as solved.

I have downloaded this file from the below mentioned website
[http://ubuntu.kiev.ua/files/et-sdl-sound.gz](http://ubuntu.kiev.ua/files/et-sdl-sound.gz)

Then we need to edit the file with gedit or any text editor which you are using.

FIRST:

# You can set this in GAME_PATH environment variable
# GAME_PATH=""

remove the # sign from GAME_PATH and enter the path of the game.
For me the path is /usr/local/games/quake3 for quake 3 and /usr/local/games/enemy-territory for Enemy Territory

SECOND:

GAME_BIN='et.x86'
et.x86 can be used for enemy territory

GAME_BIN='quake3.x86'
quake3.x86 can be used for quake 3

THIRD:

GAME_DIR='enemy-territory'
GAME_DIR='quake3'
this can be used for enemy territory or the folder name in which you have the game for me the name of the directory is "enemy-territory"

Then save the file. 

You can copy the file to the game directory

Please note that only add one game name in the file either enemy-territory or quake3 do not add both the names in the same file. I am not sure what will happen but I guess it won't work.

I haven't tried re-naming the file "et-sdl-sound" and checking not sure if that works or not.

What I have done is I have copied the file et-sdl-sound in both the game directories and then edited accordingly as per the above mentioned steps.

Lastly open the terminal go to the folder in which you are having the file "et-sdl-sound"

$ sudo chmod a+x et-sdl-sound

and then from the terminal run ./et-sdl-sound

The game will start with the sound for me at least it works fine.

---

### Post by rawcoder on 2013-08-01
Not working for me with Ubuntu 13.04!!

When I run et-sdl-sound from terminal it gives this output :

```

[et-sdl-sound] info   : quake3.x86 is installed to /usr/share/games/quake3
[et-sdl-sound] info   : 32-bit libSDL.so is installed to /home/rawcoder/.local/share/Steam/ubuntu12_32/libSDL2-2.0.so.0
[et-sdl-sound] info   : library is written to /tmp/et-sdl-sound.so
[et-sdl-sound] info   : launching the game...
Read /usr/share/games/quake3/quake3.x86 (1284028 bytes)
0x80bd99c: e9 5f 5b 66 ef 
0x80bdfe8: e9 53 55 66 ef 
0x80aafa4: e8 d7 85 67 ef 
0x80a9568: e8 53 a0 67 ef 
0x80aa7d6: e8 e5 8d 67 ef 
0x80a959e: e8 5d a0 67 ef 
0x80aa7e4: e8 17 8e 67 ef 
Found Q3 1.32b (CRC32 = 0xe5782e44)
Using SDL backend.
et-sdl-sound-r29 (Apr 13 2008 13:59:02, 3.4.6 (Gentoo 3.4.6-r2 p1.5, ssp-3.4.6-1.0, pie-8.7.10)) loaded.
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/rawcoder/.q3a/baseq3
/usr/share/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/share/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/share/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/share/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/share/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/share/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/share/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/share/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/share/games/quake3/baseq3/pak0.pk3 (3540 files)
/usr/share/games/quake3/baseq3
./quake3.x86/baseq3


----------------------
4074 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok


------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Intel(R) Haswell Desktop x86/MMX/SSE2
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
XF86 Gamma extension initialized


GL_VENDOR: Intel Open Source Technology Center
GL_RENDERER: Mesa DRI Intel(R) Haswell Desktop x86/MMX/SSE2
GL_VERSION: 3.0 Mesa 9.1.3
GL_EXTENSIONS: GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_framebuffer_sRGB GL_ARB_multitexture GL_EXT_framebuffer_sRGB GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_compression_s3tc GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_envmap_bumpmap GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_depth_clamp GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_primitive_restart GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_color_buffer_float GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_texture_array GL_EXT_texture_integer GL_EXT_texture_sRGB_decode GL_EXT_timer_query GL_OES_EGL_image GL_MESA_texture_array GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_AMD_draw_buffers_blend GL_ARB_ES2_compatibility GL_ARB_blend_func_extended GL_ARB_debug_output GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_texture_lod GL_ARB_texture_cube_map_array GL_ARB_texture_rgb10_a2ui GL_ARB_uniform_buffer_object GL_ARB_vertex_type_2_10_10_10_rev GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_ARB_get_program_binary GL_ARB_robustness GL_ARB_shader_bit_encoding GL_ARB_timer_query GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_internalformat_query GL_ARB_shading_language_packing GL_ARB_texture_storage GL_EXT_transformGL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 8


PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/lightningnew.shader'
...loading 'scripts/explode1.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/tim.shader'
...loading 'scripts/base.shader'
...loading 'scripts/base_button.shader'
...loading 'scripts/base_floor.shader'
...loading 'scripts/base_light.shader'
...loading 'scripts/base_object.shader'
...loading 'scripts/base_support.shader'
...loading 'scripts/base_trim.shader'
...loading 'scripts/base_wall.shader'
...loading 'scripts/common.shader'
...loading 'scripts/ctf.shader'
...loading 'scripts/eerie.shader'
...loading 'scripts/gothic_block.shader'
...loading 'scripts/gothic_floor.shader'
...loading 'scripts/gothic_light.shader'
...loading 'scripts/gothic_trim.shader'
...loading 'scripts/gothic_wall.shader'
...loading 'scripts/hell.shader'
...loading 'scripts/liquid.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/models.shader'
...loading 'scripts/organics.shader'
...loading 'scripts/sfx.shader'
...loading 'scripts/shrine.shader'
...loading 'scripts/skin.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/test.shader'
----- finished R_Init -----


------- sound initialization -------
Could not load SDL_AudioDriverName: /home/rawcoder/.local/share/Steam/ubuntu12_32/libSDL2-2.0.so.0: undefined symbol: SDL_AudioDriverName
------------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm.
VM file ui compiled to 594408 bytes of code
ui loaded in 1963008 bytes on the hunk
35 arenas parsed
32 bots parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: rawcoder.ubuntu
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
[et-sdl-sound] info   : done

```

Do I need to install alsa drivers??
Please help!! I really want to play this game!!

---

### Post by Yellow Pasque on 2013-08-01
If you start it like this, does it help?
```
SDL_AUDIODRIVER=alsa et-sdl-sound
```

(If that helps, you can put the 'SDL_AUDIODRIVER=alsa' at the end of ~/.bashrc)

[http://nullkey.kapsi.fi/et-sdl-sound/](http://nullkey.kapsi.fi/et-sdl-sound/)

---

### Post by rawcoder on 2013-08-03
Solved!!
No need to do all this et-sdl-sound stuff. Just add 'padsp' before 'quake3' in terminal :

**[SIZE=2]$ padsp quake3[/SIZE]**

However, it is not working for smp version.
Anyway, still getting 90fps!!

Thanks for quick reply!!

---

