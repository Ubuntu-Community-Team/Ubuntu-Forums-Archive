---
title: "SMPlayer play videos freezing"
date: 2013-03-08
forum: Multimedia Software
---

### Post by ubunet on 2013-03-08
I run Xubuntu 12.10 x32 with all codecs installed (xubuntu-restricted-extras, w32codecs, etc).

---

### Post by xc3RnbFO8P on 2013-03-08
Try to run Smplayer from Terminal:
> smplayer

---

### Post by SeijiSensei on 2013-03-08
Or navigate to Options > View Log > mplayer to see what it has logged.

SMPlayer is just a shell for mplayer.  If you want to examine the issue from the command line run 

```
mplayer /path/to/video/file
```

You can use "mplayer -v" for more details, though you'll probably be overwhelmed.

---

### Post by ubunet on 2013-03-08
> **Ringi said:**
> Try to run Smplayer from Terminal:

```
smplayer J.Edgar.2011.720p.BrRip.x264.YIFY.mp4
SMPlayer v.0.8.0 playing on Linux 
```

> **SeijiSensei said:**
> Or navigate to Options > View Log > mplayer to see what it has logged.

SMPlayer>Options>View Log>Mplayer
```
 /usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 75497507 -monitorpixelaspect 1 -ass -embeddedfonts -ass-line-spacing 0 -ass-font-scale 1 -ass-force-style PlayResX=512,PlayResY=320,Name=Default,Fontname=Liberation Sans,Fontsize=20,PrimaryColour=&H0000ffff,BackColour=&H00000000,OutlineColour=&H00000000,Bold=0,Italic=0,Alignment=2,BorderStyle=1,Outline=1,Shadow=2,MarginL=20,MarginR=20,MarginV=0 -fontconfig -font Liberation Sans -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -nocache -osdlevel 0 -vf-add screenshot -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 100 /home/gustavo/Downloads/Torrents/J Edgar (2011)/J.Edgar.2011.720p.BrRip.x264.YIFY.mp4
 

 MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 

 Playing /home/gustavo/Downloads/Torrents/J Edgar (2011)/J.Edgar.2011.720p.BrRip.x264.YIFY.mp4.
 libavformat version 53.21.1 (external)
 Mismatching header version 53.19.0
 libavformat file format detected.
 ID_VIDEO_ID=0
 [lavf] stream 0: video (h264), -vid 0
 ID_AUDIO_ID=0
 [lavf] stream 1: audio (aac), -aid 0, -alang und
 VIDEO:  [H264]  1280x536  24bpp  23.976 fps  804.7 kbps (98.2 kbyte/s)
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
  creation_time: 2012-02-11 22:24:42
 ID_CLIP_INFO_NAME3=creation_time
 ID_CLIP_INFO_VALUE3=2012-02-11 22:24:42
 ID_CLIP_INFO_N=4
 Load subtitles in /home/gustavo/Downloads/Torrents/J Edgar (2011)/
 ID_FILE_SUB_ID=0
 ID_FILE_SUB_FILENAME=/home/gustavo/Downloads/Torrents/J Edgar (2011)/J.Edgar.2011.720p.BrRip.x264.YIFY.srt
 SUB: Added subtitle file (1): /home/gustavo/Downloads/Torrents/J Edgar (2011)/J.Edgar.2011.720p.BrRip.x264.YIFY.srt
 ID_FILENAME=/home/gustavo/Downloads/Torrents/J Edgar (2011)/J.Edgar.2011.720p.BrRip.x264.YIFY.mp4
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=H264
 ID_VIDEO_BITRATE=804720
 ID_VIDEO_WIDTH=1280
 ID_VIDEO_HEIGHT=536
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=2.3881
 ID_AUDIO_FORMAT=MP4A
 ID_AUDIO_BITRATE=63992
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 ID_START_TIME=0.00
 ID_LENGTH=8214.49
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 Opening video filter: [ass auto=1]
 [ass] auto-open
 Opening video filter: [screenshot]
 ==========================================================================
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 libavcodec version 53.35.0 (external)
 Mismatching header version 53.32.2
 Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
 ==========================================================================
 ID_VIDEO_CODEC=ffh264
 ==========================================================================
 Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
 AUDIO: 48000 Hz, 2 ch, s16le, 64.0 kbit/4.17% (ratio: 7999->192000)
 ID_AUDIO_BITRATE=63992
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
 ==========================================================================
 AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
 ID_AUDIO_CODEC=ffaac
 Starting playback...
 Unsupported PixelFormat 61
 Unsupported PixelFormat 53
 Unsupported PixelFormat 81
 Movie-Aspect is 2.39:1 - prescaling to correct movie aspect.
 ID_VIDEO_ASPECT=2.3881
 [swscaler @ 0xb6c1d320]using unscaled yuv420p -> rgb24 special converter
 VO: [xv] 1280x536 => 1280x536 Planar YV12 
 

 [Mixer] No hardware mixing, inserting volume filter.
 
```


> **SeijiSensei said:**
> SMPlayer is just a shell for mplayer.  If you want to examine the issue from the command line run 

```
mplayer /path/to/video/file
```

You can use "mplayer -v" for more details, though you'll probably be overwhelmed.

```
mplayer -v J.Edgar.2011.720p.BrRip.x264.YIFY.mp4
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 6
CPU: AMD C-60 APU with Radeon(tm) HD Graphics (Family: 20, Model: 2, Stepping: 0)
extended cpuid-level: 27
extended cache-info: 33587520
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/gustavo/.mplayer/codecs.conf'
Reading optional codecs config file /home/gustavo/.mplayer/codecs.conf: No such file or directory
Reading optional codecs config file /etc/mplayer/codecs.conf: No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/gustavo/.mplayer/fonts'
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-radio --enable-radio-capture --disable-arts --language=all --disable-dvdread-internal --disable-libdvdcss-internal --disable-libmpeg2-internal --disable-ffmpeg_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-joystick --disable-gui
CommandLine: '-v' 'J.Edgar.2011.720p.BrRip.x264.YIFY.mp4'
Using nanosleep() timing
get_path('input.conf') -> '/home/gustavo/.mplayer/input.conf'
Reading optional input config file /home/gustavo/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 92 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('J.Edgar.2011.720p.BrRip.x264.YIFY.mp4.conf') -> '/home/gustavo/.mplayer/J.Edgar.2011.720p.BrRip.x264.YIFY.mp4.conf'

Playing J.Edgar.2011.720p.BrRip.x264.YIFY.mp4.
get_path('sub/') -> '/home/gustavo/.mplayer/sub/'
[file] File size is 895253093 bytes
STREAM: [file] J.Edgar.2011.720p.BrRip.x264.YIFY.mp4
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
Configuration: --arch=i386 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.8.5-0ubuntu0.12.10.1' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-gnutls --enable-libgsm --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-swscale --enable-libcdio --enable-x11grab --shlibdir=/usr/lib/i386-linux-gnu/i686/cmov --cpu=i686 --enable-shared --disable-static
LAVF_check: QuickTime/MPEG-4/Motion JPEG 2000 format
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0xb6c235e0]ISO: File Type Major Brand: isom
[h264 @ 0xb64ccd20]err{or,}_recognition separate: 1; 1
[h264 @ 0xb64ccd20]err{or,}_recognition combined: 1; 1
[h264 @ 0xb64ccd20]Unsupported bit depth: 0
[aac @ 0xb64ccd20]err{or,}_recognition separate: 1; 1
[aac @ 0xb64ccd20]err{or,}_recognition combined: 1; 1
[aac @ 0xb64ccd20]Unsupported bit depth: 0
[h264 @ 0xb64ccd20]no picture
[h264 @ 0xb64ccd20]no picture
[mov,mp4,m4a,3gp,3g2,mj2 @ 0xb6c235e0]All info found
==> Found video stream: 0
======= VIDEO Format ======
  biSize 81
  biWidth 1280
  biHeight 536
  biPlanes 0
  biBitCount 24
  biCompression 875967048='H264'
  biSizeImage 2058240
Unknown extra header dump: [1] [64] [0] [1f] [ff] [e1] [0] [19] [67] [64] [0] [1f] [ac] [d9] [80] [50] [4] [5f] [97] [1] [10] [0] [0] [3e] [90] [0] [b] [b8] [8] [f1] [83] [19] [a0] [1] [0] [5] [68] [e9] [7b] [2c] [8b] 
===========================
[lavf] stream 0: video (h264), -vid 0
==> Found audio stream: 1
======= WAVE Format =======
Format Tag: 20557 (0x504D)
Channels: 2
Samplerate: 48000
avg byte/sec: 7999
Block align: 1
bits/sample: 16
cbSize: 7
Unknown extra header dump: [13] [10] [56] [e5] [9d] [48] [0] 
==========================================================================
[lavf] stream 1: audio (aac), -aid 0, -alang und
LAVF: 1 audio and 1 video streams found
LAVF: build 3478272
VIDEO:  [H264]  1280x536  24bpp  23.976 fps  804.7 kbps (98.2 kbyte/s)
[V] filefmt:44  fourcc:0x34363248  size:1280x536  fps:23.976  ftime:=0.0417
Clip info:
 major_brand: isom
 minor_version: 1
 compatible_brands: isomavc1
 creation_time: 2012-02-11 22:24:42
Load subtitles in ./
get_path('sub/') -> '/home/gustavo/.mplayer/sub/'
[file] File size is 152404 bytes
STREAM: [file] ./J.Edgar.2011.720p.BrRip.x264.YIFY.srt
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
SUB: Detected subtitle file format: subviewer
SUB: Read 2002 subtitles, 0 bad line(s).
SUB: Adjusted 1142 subtitle(s).
SUB: Added subtitle file (1): ./J.Edgar.2011.720p.BrRip.x264.YIFY.srt
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1360x768 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Detected wm supports FULLSCREEN state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Using Xv Adapter #0 (AMD Radeon AVIVO Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 4096x4096
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Configuration: --arch=i386 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.8.5ubuntu0.12.10.1+medibuntu1' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libdirac --enable-libfreetype --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-swscale --enable-libcdio --enable-x11grab --enable-libx264 --enable-libxvid --enable-libfaac --enable-nonfree --shlibdir=/usr/lib/i386-linux-gnu/i686/cmov --cpu=i686 --enable-shared --disable-static --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3
[h264 @ 0xb64ccd20]err{or,}_recognition separate: 2; 1
[h264 @ 0xb64ccd20]err{or,}_recognition combined: 2; 3
[h264 @ 0xb64ccd20]Unsupported bit depth: 0
INFO: libavcodec init OK!
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
dec_audio: Allocating 192000 + 131072 = 323072 bytes for output buffer.
FFmpeg's libavcodec audio codec
[aac @ 0xb64ccd20]err{or,}_recognition separate: 1; 1
[aac @ 0xb64ccd20]err{or,}_recognition combined: 1; 1
[aac @ 0xb64ccd20]Unsupported bit depth: 0
INFO: libavcodec "aac" init OK!
AUDIO: 48000 Hz, 2 ch, s16le, 64.0 kbit/4.17% (ratio: 7999->192000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Trying preferred audio driver 'pulse', options '[none]'
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
Increasing filtered audio buffer size from 0 to 50048
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
[h264 @ 0xb64ccd20]no picture
[h264 @ 0xb64ccd20]no picture
[ffmpeg] aspect_ratio: 2.388060
VDec: vo config request - 1280 x 536 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.39:1 - prescaling to correct movie aspect.
VO Config (1280x536->1280x536,flags=0,'MPlayer',0x32315659)
VO: [xv] 1280x536 => 1280x536 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x59565955 (UYVY) packed
using Xvideo port 143 for hw scaling
*** [vo] Exporting mp_image_t, 1280x536x12bpp YUV planar, 1029120 bytes
Unicode font: 5193 glyphs.
Unicode font: 5193 glyphs.
A:  28.4 V:  28.4 A-V:  0.000 ct: -0.042   0/  0 33%  3%  3.1% 1 0 
Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: ffmpeg
Uninit video: ffmpeg
Successfully enabled DPMS
vo: uninit ...

Exiting... (Quit)

```

---

### Post by SeijiSensei on 2013-03-08
In Options > Preferences > Video try using the "gl fast" driver for ATI in the drop-down box.  It may give you better performance than the default xv driver.

---

### Post by tintin13 on 2013-05-18
Had exactly the same problem in any distro is use smplayer.  Solved it by disabling the audio equalizer in options/prefernces/audio. Hope it helps.

---

