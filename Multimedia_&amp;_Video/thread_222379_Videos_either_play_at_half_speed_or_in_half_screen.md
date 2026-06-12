---
title: "Videos either play at half speed or in half screen."
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by Maheriano on 2006-07-24
When I play videos, they play fine except when I maximize them. Depending on the driver I use, it either maximizes the application without maximizing the viewing screen, or it does maximize it and plays really choppy. I wanted to see exactly what it was doing, so I ran it from the command line and got this.

> root@danny:/home/dan/Desktop/Danny/Downloads# gmplayer With*
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron D Prescott; Xeon Nocona (Family: 15, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


vo: couldn't open the X11 display ()!
MPlayer GUI requires X11.
91 audio & 204 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing Without a Paddle - Proper US retail DVD rip [XviD].avi.
AVI file format detected.
VIDEO:  [XVID]  640x272  12bpp  23.976 fps  1048.4 kbps (128.0 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2439/release)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
vo: couldn't open the X11 display ()!
SDL: Using driver: fbcon
vo: couldn't open the X11 display ()!
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 640 x 272 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [sdl] 640x272 => 640x272 Planar YV12
aspect: Warning: no suitable new res found!
alsa-space: xrun of at least 0.355 msecs. resetting stream?,?% 1 0
alsa-uninit: pcm closed-0.005 ct: -0.013 641/641  5% 46%  0.8% 21 0

Exiting... (Quit)


I'm using a Radeon 9250 dual head PCI video card which I know can handle it because I've had it running it a month ago. The only things that have changed on my computer since I had it working is I changed from Gentoo to Ubuntu, and I also changed motheroards. Here is the motherboard I'm running now, it's just a cheapy. [http://www.ncix.com/products/index.php?sku=18887&vpn=P4I65G&manufacture=ASRock](http://www.ncix.com/products/index.php?sku=18887&vpn=P4I65G&manufacture=ASRock)

[IMG]http://img.ncix.com/gif/18887.JPG[/IMG]

I had the exact same problem a year ago and I think I can fix it by changing my USE flags in both my make.conf and my Mplayer to support MMX, SSE and SSE2. However I can't seem to find these files on my computer.

---

### Post by dtfinch on 2006-07-25
You want to be using xv or another accelerated mode for video output. The slowness comes from it having to resize each frame in software, which is awfully slow no matter how fast your system is. Verify which output methods are available by running "mplayer -vo help".

If building mplayer from the source, you'll want to make sure that libxv1 and libxv-dev are installed, and reconfigure. Something else I do is use oss instead of alsa for audio output. I've had performance issues with alsa.

I can only guess why it says "vo: couldn't open the X11 display ()!", unless you ran it outside of x.org.

---

### Post by Maheriano on 2006-07-25
Once I have these, what do I do with them? 

```
dan@danny:~$ mplayer -vo help
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron D Prescott; Xeon Nocona (Family: 15, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Available video output drivers:
        xmga    Matrox G200/G4x0/G550 overlay in X11 window (using /dev/mga_vid)        mga     Matrox G200/G4x0/G550 overlay (/dev/mga_vid)
        tdfxfb  3Dfx Banshee/Voodoo3/Voodoo5
        3dfx    3dfx (/dev/3dfx)
        xvmc    XVideo Motion Compensation
        xv      X11/Xv
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        gl      X11 (OpenGL)
        gl2     X11 (OpenGL) - multiple textures version
        dga     DGA ( Direct Graphic Access V2.0 )
        sdl     SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
        ggi     General Graphics Interface (GGI) output
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        aa      AAlib
        caca    libcaca
        dxr3    DXR3/H+ video out
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        jpeg    JPEG file
        gif89a  animated GIF output
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

91 audio & 204 video codecs
```

And how do I do this?
> you'll want to make sure that libxv1 and libxv-dev are installed, and reconfigure

---

### Post by Maheriano on 2006-07-25
So I figured all that out and got it done, it runs at normal speed and size now. The only problem is it seems to be skipping frames in order to do so. Could this be because of the crappy motherboard? It's the same CPU which was running it fine before, just a different motherboard. Is it possible? Or can someone point me in the direction to check something else?

Here's what I get now.
```
dan@danny:~/Desktop/Danny/Downloads$ gmplayer With*
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron D Prescott; Xeon Nocona (Family: 15, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.



91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/dan/Desktop/Danny/Downloads/Without a Paddle - Proper US retail DVD rip [XviD].avi.
AVI file format detected.
VIDEO:  [XVID]  640x272  12bpp  23.976 fps  1048.4 kbps (128.0 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2439/release)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 640 x 272 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [x11] 640x272 => 640x272 Planar YV12
SwScaler: using unscaled Planar YV12 -> BGRA special converter
A:   7.2 V:   6.7 A-V:  0.450 ct:  0.264 162/162  4% 86%  0.6% 102 0

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

alsa-uninit: pcm closed 1.103 ct:  0.506 220/220  4% 92%  0.7% 158 0

Exiting... (Quit)

```

---

### Post by dtfinch on 2006-07-25
It looks like it ought to just work. I guess choose xv in your gmplayer preferences or add "-vo xv" you your mplayer command line.

You should really try something other than alsa. It's caused skipping problems for me in dapper, mainly when using mplayer and zsnes. So now I use oss for audio output.

---

### Post by Maheriano on 2006-07-25
I tried OSS, it couldn't open the driver. I'll check to see if I even have it installed.

---

### Post by Maheriano on 2006-07-25
OSS is not installed, but when I run the video even without sound using the OSS, it's the same. Here's some more information that might help you help me.

1. In Totem, it runs full screen and looks like it's skipping frames. Not sure if it's using ALSa, OSS, or how to tell. 
2. In Gmplayer, it's running smooth but won't maximize the video screen with the window. It keeps it the same size.
3. I can't run it with -xv vo, it gives an error saying it couldn't open the selected video out device.
4. I can only run it in X11 and see the video with the above mentioned problems.
5. I tried to force it to full screen with -fs but it won't go.

---

### Post by dtfinch on 2006-07-25
What about -vo gl2 ?

---

### Post by Maheriano on 2006-07-25
That plays slow when it's small, and slower when maximized.

---

### Post by cracker on 2006-07-25
Perhaps this is an issue with your video driver?

---

### Post by Maheriano on 2006-07-25
It was the driver installed when I installed Ubuntu. I'm going to pick up a socket 939 Athlon 64 3500+ processor and Asus motherboard today to see if it's any of those giving me trouble. Right now I'm running a socket 478 Celeron D processor and Asrock motherboard.

---

### Post by dtfinch on 2006-07-25
You've probably already checked this, but do see a "direct rendering: Yes" when you run glxinfo?

---

### Post by Maheriano on 2006-07-25
You might have found it. Now what does this mean?

> dan@danny:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: No**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
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
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_NV_blend_square, GL_NV_point_sprite, GL_NV_texgen_reflection,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None


---

### Post by Maheriano on 2006-07-26
It may be because it's using the "vesa" driver in my xorg.conf which I have non idea what that is. It should be using the Radeon driver. I tried to install it from their website and I'm having loads of troubles. I just upgraded from a Celeron D x86 processor to a Athlon 64 3500+ processor, and the driver depends on the architecture. Could that be confusing it? What's the quickest way to get my system to acknowledge the 64 bit processor as 64 bit?

---

### Post by Maheriano on 2006-07-26
I changed the driver in my xorg.conf from "vesa" to "ati" and everything is fixed. Scrolling on the internet is smoother, videos aren't jumpy, applications run faster.

---

