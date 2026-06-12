---
title: "x264 + pipe + mplayer = bad combination?"
date: 2011-01-28
forum: Multimedia Software
---

### Post by glh5 on 2011-01-28
I sometimes stream files from a fileserver with the following command:

```
ssh arjen@server.ip.address cat ~/path/to/mkv_file.mkv | mplayer -cache 32768 -
```

This works fine with allmost all files, but I recently had problems with playing .mkv files with the x264 video encoder. 

I just get this output then:

```
arjen@arjen-laptop:~$ ssh server cat ~/torrents/completed/timpe-thetown.mkv | mplayer -v -cache 32768 -
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 10
CPU: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
extended cpuid-level: 8
extended cache-info: 67125312
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/arjen/.mplayer/codecs.conf'
Reading /home/arjen/.mplayer/codecs.conf: Can't open '/home/arjen/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --disable-arts --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' '-cache' '32768' '-'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/arjen/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/arjen/.mplayer/input.conf'
Can't open input config file /home/arjen/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 91 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('-.conf') -> '/home/arjen/.mplayer/-.conf'

Playing -.
get_path('sub/') -> '/home/arjen/.mplayer/sub/'
Reading from stdin...
[file] File size is -1 bytes
STREAM: [file] -
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
CACHE_PRE_INIT: 0 [0] 0  pre:6710886  eof:0  
Cache fill: 19.97% (6701056 bytes)   
LAVF_check: Matroska file format
libavformat file format detected.
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
Cache not filling!
^C

MPlayer interrupted by signal 2 in module: enable_cache


MPlayer interrupted by signal 2 in module: demux_open
[matroska @ 0x951a060]Estimating duration from bitrate, this may be inaccurate
==> Found video stream: 0
======= VIDEO Format ======
  biSize 82
  biWidth 720
  biHeight 304
  biPlanes 0
  biBitCount 0
  biCompression 875967048='H264'
  biSizeImage 0
Unknown extra header dump: [1] [64] [0] [1f] [ff] [e1] [0] [18] [67] [64] [0] [1f] [ac] [56] [24] [b] [42] [7b] [1] [10] [0] [0] [3e] [90] [0] [b] [b8] [8] [f1] [83] [18] [98] [1] [0] [7] [68] [e8] [8e] [cb] [30] [2] [c0] 
===========================
[lavf] stream 0: video (h264), -vid 0
==> Found audio stream: 1
======= WAVE Format =======
Format Tag: 8192 (0x2000)
Channels: 6
Samplerate: 48000
avg byte/sec: 48000
Block align: 1
bits/sample: 0
cbSize: 0
==========================================================================
[lavf] stream 1: audio (ac3), -aid 0, -alang eng
LAVF: 1 audio and 1 video streams found
LAVF: build 3424258
VIDEO:  [H264]  720x304  0bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x34363248  size:720x304  fps:24.000  ftime:=0.0417
Clip info:
 doctype: matroska
get_path('sub/') -> '/home/arjen/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1680x945 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Could not grab port 77.
[VO_XV] Using Xv Adapter #0 (Intel(R) Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2048x2048
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
dec_audio: Allocating 192000 + 65536 = 257536 bytes for output buffer.
FFmpeg's libavcodec audio codec
INFO: libavcodec "ac3" init OK!
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
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
[h264 @ 0x14c1760]no picture
[h264 @ 0x14c1760]no picture
[ffmpeg] aspect_ratio: 2.368421
VDec: vo config request - 720 x 304 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.37:1 - prescaling to correct movie aspect.
VO Config (720x304->720x304,flags=0,'MPlayer',0x32315659)
VO: [xv] 720x304 => 720x304 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x434d5658 (XVMC) planar
using Xvideo port 78 for hw scaling
*** [vo] Exporting mp_image_t, 720x304x12bpp YUV planar, 328320 bytes
Unicode font: 5103 glyphs.
Unicode font: 5103 glyphs.
Uninit audio filters... 0.191 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 19% 
[libaf] Removing filter dummy 
Uninit audio: ffmpeg
Uninit video: ffmpeg
Successfully enabled DPMS
vo: uninit ...

Exiting... (Quit)
```

As far as I know I have all codec files installed. Am I missing something? How to solve this problem?

---

### Post by glh5 on 2011-01-29
bump

---

