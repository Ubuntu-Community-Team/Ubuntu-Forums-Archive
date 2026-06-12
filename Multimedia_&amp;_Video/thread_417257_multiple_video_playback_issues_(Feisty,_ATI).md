---
title: "multiple video playback issues (Feisty, ATI)"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by leptogenesis on 2007-04-21
Hello,

I recently upgraded to Feisty and installed the newest ATI drivers for my Radeon X1400 card (version 8.36.5).  However, I'm having video playback issues on both totem and mplayer, on all video files I've tried (so far, i've tried mpg, avi, and mp4).  

On mplayer, the video plays several pixels too low (See the attached screenshot) for all videos.  On avi files with MPEG-4 video, I also get a "seek failed!" error, although the video still seems to play (at least, it plays as well as the other files I've tried) (I believe the seek failed error may be unrelated; I've had that problem before, but I can't find the thread with the solution)

Here's mplayer's output when running the video shown in the attachment:

```

leptogenesis@leptogenesis-laptop:/shared/torrents/video$ gmplayer -v mpeg4video.avi
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2500  @ 2.00GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1680x1050 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Adding filename mpeg4video.avi && pathname /shared/torrents/video
get_path('codecs.conf') -> '/home/leptogenesis/.mplayer/codecs.conf'
Reading /home/leptogenesis/.mplayer/codecs.conf: Can't open '/home/leptogenesis/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' 'mpeg4video.avi'
init_freetype
get_path('font/font.desc') -> '/home/leptogenesis/.mplayer/font/font.desc'
font: can't open file: /home/leptogenesis/.mplayer/font/font.desc
Bitmap font /usr/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using nanosleep() timing
get_path('input.conf') -> '/home/leptogenesis/.mplayer/input.conf'
Can't open input config file /home/leptogenesis/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 67 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
vo: X11 truecolor visual 0x23, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x24, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x25, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x26, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x27, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x28, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x29, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2a, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2b, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2c, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2d, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2e, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2f, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x30, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x31, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x32, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x33, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x34, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x35, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x36, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x37, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x38, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x39, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3a, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3b, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3c, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3d, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3e, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3f, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x40, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x41, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x42, depth 24, R:FF0000 G:FF00 B:FF
get_path('skins') -> '/home/leptogenesis/.mplayer/skins'
get_path('Skin') -> '/home/leptogenesis/.mplayer/Skin'
SKIN dir 1: '/home/leptogenesis/.mplayer/skins'
SKIN dir 1 (obsolete): '/home/leptogenesis/.mplayer/Skin'
SKIN dir 2: '/usr/share/mplayer/skins'
SKIN dir 2 (obsolete): '/usr/share/mplayer/Skin'
vo: X11 truecolor visual 0x23, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x24, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x25, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x26, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x27, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x28, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x29, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2a, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2b, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2c, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2d, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2e, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2f, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x30, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x31, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x32, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x33, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x34, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x35, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x36, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x37, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x38, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x39, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3a, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3b, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3c, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3d, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3e, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3f, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x40, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x41, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x42, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x23, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x24, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x25, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x26, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x27, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x28, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x29, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2a, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2b, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2c, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2d, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2e, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2f, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x30, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x31, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x32, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x33, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x34, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x35, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x36, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x37, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x38, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x39, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3a, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3b, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3c, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3d, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3e, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x3f, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x40, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x41, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x42, depth 24, R:FF0000 G:FF00 B:FF
get_path('mpeg4video.avi.conf') -> '/home/leptogenesis/.mplayer/mpeg4video.avi.conf'

Playing /shared/torrents/video/mpeg4video.avi.
get_path('sub/') -> '/home/leptogenesis/.mplayer/sub/'
[file] File size is 244023300 bytes
STREAM: [file] /shared/torrents/video/mpeg4video.avi
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
AVI file format detected.
list_end=0x2292
======= AVI Header =======
us/frame: 41708  (fps=23.976)
max bytes/sec: 0
padding: 0
MainAVIHeader.dwFlags: (272) HAS_INDEX IS_INTERLEAVED
frames  total: 34398   initial: 0
streams: 2
Suggested BufferSize: 0
Size:  640 x 480
==========================
list_end=0x10F4
==> Found video stream: 0
====== STREAM Header =====
Type: vids   FCC: xvid (64697678)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 0
Rate: 2997001/125000 = 23.976
Start: 0   Len: 34398
Suggested BufferSize: 160655
Quality 10000
Sample size: 0
==========================
Found 'bih', 40 bytes of 40
======= VIDEO Format ======
  biSize 40
  biWidth 640
  biHeight 480
  biPlanes 1
  biBitCount 12
  biCompression 1145656920='XVID'
  biSizeImage 1843200
===========================
Regenerating keyframe table for MPEG-4 video.
list_end=0x2186
==> Found audio stream: 1
====== STREAM Header =====
Type: auds   FCC:  (0)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 1
Rate: 20000/1 = 20000.000
Start: 0   Len: 28693084
Suggested BufferSize: 10000
Quality -1
Sample size: 1
==========================
Found 'wf', 30 bytes of 18
======= WAVE Format =======
Format Tag: 85 (0x55)
Channels: 2
Samplerate: 48000
avg byte/sec: 20000
Block align: 1
bits/sample: 0
cbSize: 12
mp3.wID=1
mp3.fdwFlags=0x2
mp3.nBlockSize=480
mp3.nFramesPerBlock=1
mp3.nCodecDelay=0
==========================================================================
list_end=0x2292
AVI: dmlh found (size=248) (total_frames=34398)
list_end=0x22D2
hdr=Software  size=44
Software  : VirtualDubMod 1.5.10.1 (build 2366/release)
list_end=0xE7AACF4
Found movie at 0x280C - 0xE7AACF4
Reading INDEX block, 68785 chunks for 34398 frames (fpos=242920700).
[x11] NET style stay on top (layer 0). Using state _NET_WM_STATE_ABOVE.
Seek failed
AVI index offset: 0x2808 (movi=0x280C idx0=0x4 idx1=0x271C)
Auto-selected AVI audio ID = 1
Auto-selected AVI video ID = 0
AVI: Searching for audio stream (id:1)
AVI video size=213638206 (34398) audio size=28693084 (28693084)
VIDEO:  [XVID]  640x480  12bpp  23.976 fps  1191.3 kbps (145.4 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:640x480  fps:23.98  ftime:=0.0417
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2366/release)
get_path('sub/') -> '/home/leptogenesis/.mplayer/sub/'
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 4096x4096
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
dec_audio: Allocating 4096 bytes for input buffer.
dec_audio: Allocating 9216 + 65536 = 74752 bytes for output buffer.
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
alsa-init: requested format: 48000 Hz, 2 channels, 9
alsa-init: using ALSA 1.0.13
alsa-init: setup for 1/2 channel(s)
alsa-init: using device default
alsa-init: pcm opend in blocking mode
alsa-init: chunksize set to 1024
alsa-init: fragcount=16
alsa-init: got buffersize=65536
alsa-init: got period size 1024
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio output
AO: Author: Alex Beregszaszi, Zsolt Barat <joy@streamminister.de>
AO: Comment: under developement
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
XXX initial  v_pts=0.000  a_pos=10000 (0.500) 
[ffmpeg] aspect_ratio: 1.333333
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (640x480->640x480,flags=0,'MPlayer',0x32315659)
VO: [xv] 640x480 => 640x480 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 115 for hw scaling
[xv] dx: 0 dy: 0 dw: 640 dh: 480
*** [vo] Allocating (slices) mp_image_t, 640x480x12bpp YUV planar, 460800 bytes
[xv] dx: 0 dy: 0 dw: 640 dh: 480
*** [vo] Allocating (slices) mp_image_t, 640x480x12bpp YUV planar, 460800 bytes 
*** [vo] Allocating (slices) mp_image_t, 640x480x12bpp YUV planar, 460800 bytes 
Uninit audio filters... 0.001 ct:  0.004  78/ 78  7%  9%  2.4% 0 0              
[libaf] Removing filter dummy 
Uninit audio: libmad
Uninit video: ffmpeg
alsa-uninit: pcm closed
[GUI] done.
get_path('gui.conf') -> '/home/leptogenesis/.mplayer/gui.conf'
get_path('gui.pl') -> '/home/leptogenesis/.mplayer/gui.pl'
get_path('gui.url') -> '/home/leptogenesis/.mplayer/gui.url'
get_path('gui.history') -> '/home/leptogenesis/.mplayer/gui.history'

Exiting... (Quit)

```

Playing the same video on totem yields the following output:

```

leptogenesis@leptogenesis-laptop:/shared/torrents/video$ totem mpeg4video.avi 
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 42 error_code 8 request_code 141 minor_code 14)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

The output is similar for all files, not just avi's with mpeg4.

I have no idea whether the two problems are related.  Any ideas?

---

### Post by sgardne on 2007-04-26
Hello, I have the exact same video card and am also using Feisty, but a slightly different problem. Whenever playing any .mp4 video, I can hear the audio, but cannot see the video. Different players do different things, but they all do one of two things: 1) Most commonly I get just a red and yellow noise field. 2) Occasionally, I get a still screen of the previous successfully played video. I've tried gxine, vlc, mplayer, totem. They all do one of those two things. Mplayer will actually do either/or depending on which video driver is used. I assume this means I'm missing some codec, but I have no idea which one. I've installed all the gstreamer plugins as well as the Ubuntu restricted extras.

---

