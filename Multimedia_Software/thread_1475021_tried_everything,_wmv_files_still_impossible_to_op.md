---
title: "tried everything, wmv files still impossible to open"
date: 2010-05-06
forum: Multimedia Software
---

### Post by lenca.flenca on 2010-05-06
Hey!

I have searched all trough the forum and tried several options, but had no success...

When I try to play a wmv file, it simply doesn't work.

In VLC, it comes up with a window that says "VLC cannot read the file."

And Mplayer doesn't even register it. 

I have installed the "extras" and w32codecs, and everything requested in between, with no success...

Any ideas? 

(I am a beginner and all, but till now I could allways fix everything using advice I found here...)

---

### Post by lenca.flenca on 2010-05-06
please, anyone? 

i could at least use some links or something to try, anything i haven't tried yet... any kind of help would be nice....

(i'm beginning to think it's not the problem per se that's bothering me - it could be the fact that i'm not able to fix it.... ;) )

---

### Post by mc4man on 2010-05-06
> And Mplayer doesn't even register it. 

Assuming you mean mplayer, not the 'Movie Player' (totem) then open a terminal and go 
mplayer -v /path/to/[COLOR="Blue"]whatever[/COLOR].wmv

post the results

---

### Post by lenca.flenca on 2010-05-07
Okay, so this is what happened... (sorry for putting it up like this, i don't know how to put it in a separate window to minimize..)

-laptop:~$ mplayer -v /path/to/wolfman.wmv
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 10
CPU: Intel(R) Core(TM)2 Duo CPU     T5870  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
extended cpuid-level: 8
extended cache-info: 134242368
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/encha/.mplayer/codecs.conf'
Reading /home/encha/.mplayer/codecs.conf: Can't open '/home/encha/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --datadir=/usr/share/mplayer --codecsdir=/usr/lib/codecs --enable-xvmc --enable-vdpau --enable-sdl --enable-ossaudio --enable-lirc --enable-freetype --enable-menu --enable-largefiles --extra-cflags=-I/build/buildd/mplayer-1.0~rc3+svn20090426/debian/include --disable-bitmap-font --disable-ggi --language=all --disable-xmms --disable-arts --disable-aa --disable-mad --disable-musepack --disable-libdv --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --enable-mp3lame --enable-faac-lavc --enable-x264-lavc --enable-mp3lame-lavc --enable-libdirac-lavc --enable-libschroedinger-lavc --target=i586-linux --enable-win32dll --enable-real --enable-xanim --enable-runtime-cpudetection --enable-vdpau --disable-libdvdcss-internal --enable-dvdread --enable-debug --enable-tv-v4l2 --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-fbdev --disable-gui
CommandLine: '-v' '/path/to/wolfman.wmv'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/encha/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/encha/.mplayer/input.conf'
Can't open input config file /home/encha/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('wolfman.wmv.conf') -> '/home/encha/.mplayer/wolfman.wmv.conf'

Playing /path/to/wolfman.wmv.
get_path('sub/') -> '/home/encha/.mplayer/sub/'
File not found: '/path/to/wolfman.wmv'
Failed to open /path/to/wolfman.wmv.

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)

I did consider the file being corrupted or something, but this has happened before and only with this type of files. It's strange for me, I never had problems before - I mean, VLC plays everything, right? :)

And tnx for helping...

---

### Post by doixanh on 2010-05-07
lol you need to put the correct path to your wmv file within the command 
```
mplayer -v /path/to/[COLOR=Blue]whatever[/COLOR].wmv
```

things like 
```
mplayer -v /home/name/wolfman.wmv
```

there is also an possibility of broken wmv file.

---

### Post by lenca.flenca on 2010-05-07
LOL, yeah, i was in a hurry, working on it

---

### Post by lenca.flenca on 2010-05-07
okay, so now it opened the file but it's all weird... streched out and stuff, and with really bad audio.

and besides, am i suppose to open .wmv like this from now on?

this is what came up in the terminal:


-laptop:~$ mplayer -v /home/encha/qBT_dir/the_wolfman.wmv
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 10
CPU: Intel(R) Core(TM)2 Duo CPU     T5870  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
extended cpuid-level: 8
extended cache-info: 134242368
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/encha/.mplayer/codecs.conf'
Reading /home/encha/.mplayer/codecs.conf: Can't open '/home/encha/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --datadir=/usr/share/mplayer --codecsdir=/usr/lib/codecs --enable-xvmc --enable-vdpau --enable-sdl --enable-ossaudio --enable-lirc --enable-freetype --enable-menu --enable-largefiles --extra-cflags=-I/build/buildd/mplayer-1.0~rc3+svn20090426/debian/include --disable-bitmap-font --disable-ggi --language=all --disable-xmms --disable-arts --disable-aa --disable-mad --disable-musepack --disable-libdv --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --enable-mp3lame --enable-faac-lavc --enable-x264-lavc --enable-mp3lame-lavc --enable-libdirac-lavc --enable-libschroedinger-lavc --target=i586-linux --enable-win32dll --enable-real --enable-xanim --enable-runtime-cpudetection --enable-vdpau --disable-libdvdcss-internal --enable-dvdread --enable-debug --enable-tv-v4l2 --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-fbdev --disable-gui
CommandLine: '-v' '/home/encha/qBT_dir/the_wolfman.wmv'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/encha/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/encha/.mplayer/input.conf'
Can't open input config file /home/encha/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('the_wolfman.wmv.conf') -> '/home/encha/.mplayer/the_wolfman.wmv.conf'

Playing /home/encha/qBT_dir/the_wolfman.wmv.
get_path('sub/') -> '/home/encha/.mplayer/sub/'
[file] File size is 708333431 bytes
STREAM: [file] /home/encha/qBT_dir/the_wolfman.wmv
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: ASF format
Checking for YUV4MPEG2
ASF file format detected.
stream type: guid_audio_stream
stream concealment: guid_audio_conceal_interleave
type: 28 bytes,  stream: 8 bytes  ID: 1
unk1: 0  unk2: 248FC64
FILEPOS=0x1348
==> Found audio stream: 1
[asfheader] Audio stream found, -aid 1
======= WAVE Format =======
Format Tag: 353 (0x161)
Channels: 2
Samplerate: 44100
avg byte/sec: 40004
Block align: 7431
bits/sample: 16
cbSize: 10
Unknown extra header dump: [0] [88] [0] [0] [f] [0] [0] [0] [0] [0] 
==========================================================================
ASF: audio scrambling: 1 x 1 x 7431
stream type: guid_video_stream
stream concealment: unknown guid 0057fb20-555b-cf11-a8fd00805f5c442b
type: 73 bytes,  stream: 0 bytes  ID: 2
unk1: 0  unk2: 0
FILEPOS=0x13BA
==> Found video stream: 2
[asfheader] Video stream found, -vid 2
======= VIDEO Format ======
  biSize 62
  biWidth 1280
  biHeight 1024
  biPlanes 1
  biBitCount 24
  biCompression 826496599='WVC1'
  biSizeImage 0
Unknown extra header dump: [27] [0] [0] [1] [f] [db] [fe] [27] [f1] [ff] [88] [80] [0] [0] [1] [e] [10] [44] [9f] [c7] [fc] [80] 
===========================
ASF: packets: 342  flags: 2  max_packet_size: 8000  min_packet_size: 8000  max_bitrate: 3348812  preroll: 5000
============ ASF Stream group == START ===
 stream count=[0x2][2]
   stream id=[0x1][1]
   max bitrate=[0x4f877][325751]
   stream id=[0x2][2]
   max bitrate=[0x2e20d5][3023061]
============ ASF Stream group == END ===
Found movie at 0x1505 - 0x29D485
ASF: 1 audio and 1 video streams found
Auto-selected ASF video ID = 2
Auto-selected ASF audio ID = 1
ASF: Searching for audio stream (id:1).
VIDEO:  [WVC1]  1280x1024  24bpp  1000.000 fps  3000.0 kbps (366.2 kbyte/s)
[V] filefmt:6  fourcc:0x31435657  size:1280x1024  fps:1000.000  ftime:=0.0010
get_path('sub/') -> '/home/encha/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1366x768 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[VO_XV] Using Xv Adapter #0 (Intel(R) Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2048x2048
==========================================================================
Opening video decoder: [dmo] DMO video codecs
get_path('registry') -> '/home/encha/.mplayer/registry'
Creating new registry
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 1280 x 1024 (preferred colorspace: Packed YUY2)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO Config (1280x1024->1280x1024,flags=0,'MPlayer',0x32315659)
VO: [xv] 1280x1024 => 1280x1024 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x434d5658 (XVMC) planar
using Xvideo port 65 for hw scaling
INFO: Win32/DMO video codec init OK.
Selected video codec: [wmvvc1dmo] vfm: dmo (Windows Media Video (VC-1) Advanced Profile)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
dec_audio: Allocating 192000 + 65536 = 257536 bytes for output buffer.
FFmpeg's libavcodec audio codec
INFO: libavcodec init OK!
AUDIO: 44100 Hz, 2 ch, s16le, 320.0 kbit/22.68% (ratio: 40004->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Trying preferred audio driver 'pulse', options '[none]'
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Starting playback...
Increasing filtered audio buffer size from 0 to 46144

avg. framerate: 24 fps             
*** [vo] Allocating mp_image_t, 1280x1024x12bpp YUV planar, 1966080 bytes
Unicode font: 5025 glyphs.
Unicode font: 5025 glyphs.
ds_fill_buffer: EOF reached (stream: audio)  308 36%  5%  0.7% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  309 36%  5%  0.7% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  310 36%  5%  0.7% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  311 36%  5%  0.7% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  312 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  313 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  314 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  315 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  316 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  317 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  318 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  319 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  320 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  321 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  322 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  323 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: audio)  324 36%  5%  0.6% 0 0 
ds_fill_buffer: EOF reached (stream: video)  
EOF code: 1  17.9 A-V: -0.483 ct: -0.089 324/324 36%  5%  0.6% 0 0 

Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: ffmpeg
Uninit video: dmo
vo: uninit ...

Exiting... (End of file)





i desperatly need something to eat (just came from work) so i'll let you read it while i cook. ;)

---

### Post by flyingmonkey35 on 2010-05-07
Ok,

First off  dose the .wmv in question work!

have you tested it on a different computer? 

Are you able to play other .wmv files?

---

### Post by lenca.flenca on 2010-05-07
okay, so, it's like this.

since i don't have a tv, i download loads of stuff, series, movies, etc. on a daily basis. Everything that's bad quality or doesn't work, i delete, to keep my comp. clean. so, right now, i don't have any other wmv files to try - i deleted them all since they didn't work. 

but it didn't take me long to realise that ONLY wmv files don't work, so i did a little research and found out i'm not the only one with the problem.

after entering the command earlier, it opened, just to play for 18 seconds, saying i need to install some player to watch the movie. i've seen this before and i usually delete it and find a different copy. but the thing that bothers me is that even with this kind of tricks, players i have installed usually open the message (about downloading a different player) si the wmv file IS the problem.

i have NEVER been able to play wmv since i have ubuntu.

---

### Post by lenca.flenca on 2010-05-07
downloading a valid wmv movie, just to prove my point ;)

in the meantime, if you have any suggestions...

---

### Post by lenca.flenca on 2010-05-07
got my computer-expert-friend (that got me on ubunto in the firstplace) on the phone, we'll try to fix it tonight. it's a good thing i have a laptop! :)

if we figure anything out, i'll post the solution.

and still, if you have any suggestions, please...

tnx for now!

---

### Post by andrew.46 on 2010-05-07
Hi lenca,

Does the sound improve by avoiding pulse:

```
mplayer -ao alsa /home/encha/qBT_dir/the_wolfman.wmv
```

Andrew

---

### Post by lenca.flenca on 2010-05-10
It works, it works! :)

My "expert friend" said it would be too much trouble to explain the whole process, so I'll keep it simple - I think you'll get the picture.

He said, everything would be fine if I were the one to build up the system from the begining, but I didn't, because I was to terrified of the computers at the time, so he did it for me.

So I didn't know some things I should have known. Now I know them. :)

So he basically just cleaned up everything I've done about this issue, instaled the extras and win32, and some library(?) files, again and everything works just fine, at least with the files we've tried.

Sorry for wasting your time... But still, thanks to all of you who tried to help. I really appreciate it.

I'm doing my best, so thanks again. Have fun!

---

