---
title: "Mplayer won't play DVD's"
date: 2010-11-16
forum: Multimedia Software
---

### Post by chris1379 on 2010-11-16
Running Lucid Lynx. VLC works fine but Xvmc output uses less CPU on my PIII 750 laptop and isn't supported by VLC.  I installed Mplayer but I can't play anything from the Mplayer GUI. I get the message "FATAL: Could not initialize video filters (-vf) or video output (-vo)". The interface is all black so I can't see the controls.

I installed Gnome Mplayer GUI and now I have different problems. Playing video files, including VOB files from a DVD works fine. Trying to play a DVD with or without menues does not. I followed the instructions at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) .  What could be wrong?

Chris

---

### Post by andrew.46 on 2010-11-17
Hi Chris,

Could you try playing a dvd from the commandline as follows:

```
mplayer -v dvd://1
```

and post the command and full terminal output here?

Andrew

---

### Post by chris1379 on 2010-11-18
I have since tried a few other DVD's and they play from the command line or Gnome Mplayer but the menus don't work and nothing works from MPlayer GUI.
Here it is.

chris@chris-fx150:~$ mplayer -v dvd://1
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 2
CPU:  (Family: 6, Model: 8, Stepping: 10)
Detected cache-line size is 32 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 0 SSSE3: 0
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/chris/.mplayer/codecs.conf'
Reading /home/chris/.mplayer/codecs.conf: Can't open '/home/chris/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' 'dvd://1'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/chris/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/chris/.mplayer/input.conf'
Can't open input config file /home/chris/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('1.conf') -> '/home/chris/.mplayer/1.conf'

Playing dvd://1.
get_path('sub/') -> '/home/chris/.mplayer/sub/'
URL: dvd://1
libdvdread: Using libdvdcss version 1.2.10 for DVD access
Reading disc structure, please wait...
There are 99 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001e2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000242
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000002a4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000002c2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000002e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x000002ff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0000031d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0000033a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00000377
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x001dc64e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x001dc66b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x001dc688
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x001dc6a6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x001dc6c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x001dc704
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x001dd6f5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x001dd70d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x001dd722
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x001dd741
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x001e6906
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_0.VOB at 0x001e692d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x001ef84f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_0.VOB at 0x001ef874
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_1.VOB at 0x001f876c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_1.VOB at 0x001f8789
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_1.VOB at 0x001fc5b7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_1.VOB at 0x001ffbcf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_23_1.VOB at 0x00200220
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_24_1.VOB at 0x0020708a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_25_1.VOB at 0x002076ef
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_26_1.VOB at 0x0020d146
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_27_1.VOB at 0x0020d70d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_28_1.VOB at 0x0020e870
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_29_1.VOB at 0x0020f740
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_30_1.VOB at 0x002112d5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_31_1.VOB at 0x00215141
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_32_1.VOB at 0x00219413
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_33_1.VOB at 0x0021d797
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_34_1.VOB at 0x00224476
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_35_1.VOB at 0x0022b282
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_36_0.VOB at 0x0022c1be
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_36_1.VOB at 0x0022d735
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_37_1.VOB at 0x0022d74e
libdvdread: Elapsed time 0
libdvdread: Found 37 VTS's
libdvdread: Elapsed time 0
DVD successfully opened.
number of audio channels on disk: 0.
subtitle ( sid ): 0 language: unknown
number of subtitles on disk: 1
DVD start cell: 0  pack: 0x0-0x4F  
DVD start=0 end=79  
STREAM: [null] dvd://1
STREAM: Description: DVD stream
STREAM: Author: 
STREAM: Comment: 
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x4F  
Angle-seek synced by cell/vob IDN search!  
system stream synced at 0xD (13)!
==> Found video stream: 0
MPEG-PS file format detected.
==> Found subtitle: 0
--- END OF CELL !!! ---
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
MPEG: No audio stream found -> no sound.
Searching for sequence header... OK!
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.970  ftime:=0.0334
get_path('sub/') -> '/home/chris/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFF  (R:F800 G:7E0 B:1F)
vo: X11 running at 1024x768 with depth 16 and 16 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
[VO_XV] Using Xv Adapter #0 (I810 Video Overlay)
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x00083e).
[xv common] Maximum source image dimensions: 1440x1080
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
INFO: libavcodec init OK!
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
Audio: no sound
Freeing 0 unused audio chunks.
Starting playback...
[ffmpeg] aspect_ratio: 1.333333
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (720x480->720x540,flags=0,'MPlayer',0x32315659)
VO: [xv] 720x480 => 720x540 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x35315652 (RV15) packed
Xvideo image format: 0x36315652 (RV16) packed
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
using Xvideo port 63 for hw scaling
*** [vo] Allocating (slices) mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
[mpeg2video @ 0x1d18c00]ac-tex damaged at 37 7
[mpeg2video @ 0x1d18c00]Warning MVs not available
[mpeg2video @ 0x1d18c00]concealing 1035 DC, 1035 AC, 1035 MV errors
*** [vo] Allocating (slices) mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
Unicode font: 5025 glyphs.
Unicode font: 5025 glyphs.
MPEG Stream reached EOF%  0.0% 0 0 
ds_fill_buffer: EOF reached (stream: video)  
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
EOF code: 1   61 49% 16%  0.0% 0 0 

Uninit video: ffmpeg
Successfully enabled DPMS
vo: uninit ...

Exiting... (End of file)

---

### Post by chris1379 on 2010-11-20
OK, I solved my problems and can now play DVD's. I downgraded VLC to the version in the Ubuntu repositories, installed the newest Smplayer and Mplayer, and reinstalled libdvdread4 and libdvdnav4. Now I can use the command line, Smplayer, Mplayer gui, and Gnome Mplayer. Too bad Xvmc output doesn't work. I'll open this in a new topic.

---

