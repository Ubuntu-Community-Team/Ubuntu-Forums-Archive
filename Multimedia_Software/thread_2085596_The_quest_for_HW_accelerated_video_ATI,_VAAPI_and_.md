---
title: "The quest for HW accelerated video: ATI, VAAPI and Mplayer"
date: 2012-11-18
forum: Multimedia Software
---

### Post by intheflesh on 2012-11-18
I finally learned how to properly manage switching back and forth between priprietary and open-source drivers for my ATI Radeon HD 5750 (somehow, sometimes NVidia graphic drivers get installed and then the system can't load GLX modules), so I embarked on  a quest to get hardware accelerated video playback on my machine since I decided to keep fglrx.  Since I mostly use UMplayer for video playback, I found out I had to compile vaapi-enabled branch of it (from [http://gitorious.org/vaapi/mplayer](http://gitorious.org/vaapi/mplayer)). Now, I did that and hardware accelerated playback seems to work. 

CPU usage drops from about 50% to a mere 10% when I add -vo vaapi to the mplayer command to play a 720p video, but no matter what I do I can't get it to work in UMplayer nor SMplayer. I tried setting vaapi for Video output driver and adding -vo vaapi to the "Options for MPlayer", but all I get is a UMplayer logo instead of the movie being played.

How do I make videos play inside U/SMplayer?

UPDATE: Starting video with $ mplayer file.mp4-vo vaapi:gl -va vaapi seems to pause it at first frame. Maybe that's the problem?

Also, this is the output:
```

MPlayer SVN-r35107-4.6 (C) 2000-2012 MPlayer Team

Playing file.mp4.
libavformat version 54.25.104 (internal)
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (ac3), -aid 0, -alang und
[lavf] stream 2: audio (aac), -aid 1, -alang und
VIDEO:  [H264]  1280x544  24bpp  23.976 fps  2619.1 kbps (319.7 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 1
 compatible_brands: isomavc1
 creation_time: 1940-08-15 17:43:07
Load subtitles in ./
[vo_vaapi] Using OpenGL rendering
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/i386-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 54.53.100 (internal)
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
[VD_FFMPEG] Trying pixfmt=1.
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [vaapi] 1280x544 => 1280x544 H.264 VA-API Acceleration 
[VD_FFMPEG] XVMC-accelerated MPEG-2.
A:   0.5 V:   0.5 A-V: -0.080 ct: -0.029   0/  0 140% 16%  0.8% 8 0 

```

**UPDATE2: **Okay, so I messed up compiling, two different versions were at /usr/bin and /usr/local/bin; players picked the latter while bash would choose the former. That is fixed now and I can play video in SMplayer (not in UMplayer - X11 Error (BadMatch) occurs whether I select vaapi or any other output driver). So i played the same movie in SMplayer and through command line. They use the same -vo settings. The SMplayer is still using 50% CPU while the command line one uses 9. This sucks.

---

### Post by BicyclerBoy on 2012-11-18
I would have thought bash would have picked the latter..

Install/run
vainfo

Did you install the vaapi driver for AMD video BS decoder:
xvba-va-driver

---

### Post by intheflesh on 2012-11-18
Yes, all that is installed (it was rather painless, but I of course had to purge everything before installing fglrx, fglrx-amdcccle, xvba-va-driver libva-glx1 libva-egl1 and vainfo packages). I seem to have found where the problem lies.

> 
  [B]     [SIZE=2]2011-03-26, Saturday :: MPlayer is now Multi Threaded     
posted by Compn[/SIZE] [/B]

   Thanks to FFmpeg and its project in the Google Summer of Code program, we now have multi threaded support for playing back H.264 and other codecs. 
To enable threading run *mplayer -lavdopts threads=***N** file.mkv where N is the number of threads you want to use. 

   You will need to have the latest SVN MPlayer for this. Please report any bugs you find to our Bugzilla. 
  
   
(from [http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html))

When I run **$ mplayer -lavdopts threads=4 -vo vaapi -va vaapi file.mp4**, I get the same high CPU usage. Omitting -**lavdopts** switch puts it down at 8-9%.

```

 /usr/bin/mplayer -noquiet -nofs -nomouseinput -lavdopts threads=4 -sub-fuzziness 1 -identify -slave -vo vaapi:gl -ao pulse -nokeepaspect -dr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 50331707 -monitorpixelaspect 1 -*** -msglevel ***=6 -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-force-style PlayResX=512,PlayResY=320,Name=Default,Fontname=Arial,Fontsize=24,PrimaryColour=&H00ffffff,BackColour=&H00000000,OutlineColour=&H00000000,Bold=0,Italic=0,Alignment=2,BorderStyle=1,Outline=1,Shadow=2,MarginL=20,MarginR=20,MarginV=8 -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 24 -subfont-text-scale 24 -subcp CP1250 -aid 0 -subpos 100 -volume 100 -cache 65536 -osdlevel 0 -vf-add pp -autoq 3 -vf-add eq2,hue -vf-add spp -noslices -channels 2 -af scaletempo -softvol -softvol-max 110 -vo vaapi -va vaapi "/data/Downloads/Totally not an illegally downloaded file.mp4" 
 

 MPlayer SVN-r35107-4.6 (C) 2000-2012 MPlayer Team
 Terminal type `unknown' is not defined.
 Playing /data/Downloads/Totally not an illegally downloaded file.mp4.
 Cache fill:  0.00% (0 bytes)   
 libavformat version 54.25.104 (internal)
 libavformat file format detected.
 Cache not responding! [performance issue]
 ID_VIDEO_ID=0
 [lavf] stream 0: video (h264), -vid 0
 ID_AUDIO_ID=0
 [lavf] stream 1: audio (ac3), -aid 0, -alang und
 ID_AUDIO_ID=1
 [lavf] stream 2: audio (aac), -aid 1, -alang und
 VIDEO:  [H264]  1280x544  24bpp  23.976 fps  2619.1 kbps (319.7 kbyte/s)
 Clip info:
  major_brand: isom
 ID_CLIP_INFO_NAME0=major_brand
 ID_CLIP_INFO_VALUE0=isom
  minor_version: 1
 ID_CLIP_INFO_NAME1=minor_version
 ID_CLIP_INFO_VALUE1=1
  compatible_brands: isomavc1
 ID_CLIP_INFO_NAME2=compatible_brands
 ID_CLIP_INFO_VALUE2=isomavc1
  creation_time: 1940-08-15 17:43:07
 ID_CLIP_INFO_NAME3=creation_time
 ID_CLIP_INFO_VALUE3=1940-08-15 17:43:07
 ID_CLIP_INFO_N=4
 Load subtitles in /data/Downloads/
 ID_FILENAME=/data/Downloads/Totally not an illegally downloaded file.mp4
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=H264
 ID_VIDEO_BITRATE=2619056
 ID_VIDEO_WIDTH=1280
 ID_VIDEO_HEIGHT=544
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=2.3529
 ID_AUDIO_FORMAT=8192
 ID_AUDIO_BITRATE=384000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=6
 ID_START_TIME=0.00
 ID_LENGTH=5706.69
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 libva: VA-API version 0.32.0
 libva: va_getDriverName() returns 0
 libva: Trying to open /usr/lib/i386-linux-gnu/dri/fglrx_drv_video.so
 libva: va_openDriver() returns 0
 Opening video filter: [*** auto=1]
 Couldn't open video filter '***'.
 ***: cannot add video filter
 Opening video filter: [spp]
 libavcodec version 54.53.100 (internal)
 Opening video filter: [hue]
 Opening video filter: [eq2]
 Opening video filter: [pp]
 [***] Raster: FreeType 2.4.8
 [***] Shaper:
 [***] Initialized
 [***] Updating font cache
 ==========================================================================
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
 ==========================================================================
 ID_VIDEO_CODEC=ffh264
 [PP] Using external postprocessing filter, max q = 6.
 ==========================================================================
 Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
 AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
 ID_AUDIO_BITRATE=384000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
 ==========================================================================
 AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
 ID_AUDIO_CODEC=ffac3
 [Mixer] No hardware mixing, inserting volume filter.
 Starting playback...
 Unsupported PixelFormat 61
 [VD_FFMPEG] Trying pixfmt=1.
 [PP] Using external postprocessing filter, max q = 6.
 Could not find matching colorspace - retrying with -vf scale...
 Opening video filter: [scale]
 The selected video_out device is incompatible with this codec.
 Try appending the scale filter to your filter list,
 e.g. -vf spp,scale instead of -vf spp.
 Unsupported PixelFormat 81
 Unsupported PixelFormat 61
 [VD_FFMPEG] Trying pixfmt=0.
 Unsupported PixelFormat 61
 [PP] Using external postprocessing filter, max q = 6.
 Could not find matching colorspace - retrying with -vf scale...
 Opening video filter: [scale]
 The selected video_out device is incompatible with this codec.
 Try appending the scale filter to your filter list,
 e.g. -vf spp,scale instead of -vf spp.
 Unsupported PixelFormat 81
 [VD_FFMPEG] Trying pixfmt=2.
 Unsupported PixelFormat 81
 [PP] Using external postprocessing filter, max q = 6.
 Could not find matching colorspace - retrying with -vf scale...
 Opening video filter: [scale]
 The selected video_out device is incompatible with this codec.
 Try appending the scale filter to your filter list,
 e.g. -vf spp,scale instead of -vf spp.
 [VD_FFMPEG] Trying pixfmt=3.
 [PP] Using external postprocessing filter, max q = 6.
 Movie-Aspect is undefined - no prescaling applied.
 **VO: [vaapi]** 1280x544 => 1280x544 Planar YV12 
 [PP] Using external postprocessing filter, max q = 6.
 Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
 ID_VIDEO_ASPECT=2.3529
 **VO: [vaapi] **1280x544 => 1280x544 Planar YV12 
 
```So, now only to find out how to disable threading.

---

### Post by BicyclerBoy on 2012-11-19
You should take care around mixing package managed shared libraries & your personal external packages..

The big problems occur around shared dynamic libraries.
All std *buntu package managed programs are built on the system shared libraries..they are a distro..

The easiest way to avoid problems is:
- not install the std *buntu applications that you build from source.
- build all programs full static & build no shared libraries.
- can use a private name for the executable.

This has the downside of large applications but insures you know exactly what is linked to what..

Maybe I read this thread wrong...
I'm not at all surprised that the std distro SMplayer does not work right with your mplayer built from source..
You should build SMplayer from source.

---

### Post by tux-gamer on 2013-03-06
sory if i bump old thread, i need help from intheflesh

i have try to compile mplayer vaapi from git://gitorious.org/vaapi/mplayer.git in Ubuntu 12.10
but i have no luck withthis error:
```

ffmpeg/libavcodec/libavcodec.a(mpeg12enc.o): In function `ff_mpeg1_encode_picture_header':
mpeg12enc.c:(.text+0x163f): undefined reference to `ff_write_quant_matrix'
mpeg12enc.c:(.text+0x1654): undefined reference to `ff_write_quant_matrix'
ffmpeg/libavcodec/libavcodec.a(mpeg12enc.o):(.data+0x54): undefined reference to `ff_MPV_encode_picture'
ffmpeg/libavcodec/libavcodec.a(mpeg12enc.o):(.data+0x5c): undefined reference to `ff_MPV_encode_end'
ffmpeg/libavcodec/libavcodec.a(mpeg12enc.o):(.data+0xd4): undefined reference to `ff_MPV_encode_picture'
ffmpeg/libavcodec/libavcodec.a(mpeg12enc.o):(.data+0xdc): undefined reference to `ff_MPV_encode_end'
ffmpeg/libavcodec/libavcodec.a(mpeg12enc.o): In function `encode_init':
mpeg12enc.c:(.text.unlikely+0x1a): undefined reference to `ff_MPV_encode_init'
ffmpeg/libavcodec/libavcodec.a(snowenc.o): In function `encode_q_branch':
snowenc.c:(.text+0x3dca): undefined reference to `ff_epzs_motion_search'
snowenc.c:(.text+0x3e99): undefined reference to `ff_get_mb_score'
ffmpeg/libavcodec/libavcodec.a(snowenc.o): In function `encode_q_branch.constprop.16':
snowenc.c:(.text+0x5b12): undefined reference to `ff_epzs_motion_search'
snowenc.c:(.text+0x5be1): undefined reference to `ff_get_mb_score'
ffmpeg/libavcodec/libavcodec.a(snowenc.o): In function `encode_frame':
snowenc.c:(.text+0xdf0f): undefined reference to `ff_write_pass1_stats'
snowenc.c:(.text+0xe619): undefined reference to `ff_init_me'
snowenc.c:(.text+0xfc1d): undefined reference to `ff_rate_estimate_qscale'
snowenc.c:(.text+0x11261): undefined reference to `ff_rate_estimate_qscale'
snowenc.c:(.text+0x119c9): undefined reference to `ff_rate_estimate_qscale'
ffmpeg/libavcodec/libavcodec.a(snowenc.o): In function `encode_init':
snowenc.c:(.text.unlikely+0x264): undefined reference to `ff_rate_control_init'
ffmpeg/libavcodec/libavcodec.a(ituh263enc.o): In function `ff_clean_h263_qscales':
ituh263enc.c:(.text+0x9c5): undefined reference to `ff_init_qscale_tab'
collect2: error: ld returned 1 exit status
make: *** [mplayer] Error 1

```

please help, i need to compile my self to optimize with my cpu celeron 847

thanks :)



Edit:
I managed to compile it, found good howto in here [http://forums.debian.net/viewtopic.php?f=6&t=84825](http://forums.debian.net/viewtopic.php?f=6&t=84825)
lookslike because i disable alot of thing  :
```

./configure --enable-vaapi --disable-mencoder --disable-v4l2 --disable-matrixview --disable-gif --disable-pnm --disable-jpeg --disable-dvb --disable-fbdev --disable-caca --disable-vidix --disable-dga2 --disable-dga1 --disable-directfb --disable-mga --disable-yuv4mpeg --disable-md5sum --disable-tga

```

then i do "make clean" and use only:
```

./configure --enable-vaapi --enable-x11

```

then it compiled successfully.

ps: sory for my bad english.

---

