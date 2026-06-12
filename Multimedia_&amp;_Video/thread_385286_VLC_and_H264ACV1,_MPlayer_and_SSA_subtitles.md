---
title: "VLC and H264/ACV1, MPlayer and SSA subtitles"
date: 2007-03-15
forum: Multimedia &amp; Video
---

### Post by rayofash on 2007-03-15
I have an MKV video that uses an avc1 video codec. When I load it in VLC, it's all blurry. Switching the video output to X11 or OpenGL helps the blurriness, but the video is slow and skips, and then crashes. Other MKV files work fine. The video works fine in MPlayer, but MPlayer can't read the the subtitle file embedded in the video.

I have another video file, an AVI, that uses H264. It has the same problem in VLC, but works fine in MPlayer.

How can I get VLC to work? I don't like MPlayer's quirkiness (unpausing if you click anything, go-to tracking instead of scroll tracking, controling the whole systems volume) .

Here's what it looks like:

[IMG]http://img.photobucket.com/albums/v317/RayOfAsh/img000004.png[/IMG]

---

### Post by panch0 on 2007-03-15
In general MPlayer should work as good or better than vlc, so let's try to fix it. Run

mplayer -v file.mkv

from the command line and post the output you get.

---

### Post by rayofash on 2007-03-15
But I want VLC to work :( .

rayofash@SHODAN:~$ cd Desktop
rayofash@SHODAN:~/Desktop$ mplayer -v '[Anime-RG] Venus Versus Virus - 01 [WS][4AC4E600].mkv'
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP Thoroughbred; Duron Applebred (Family: 6, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


get_path('codecs.conf') -> '/home/rayofash/.mplayer/codecs.conf'
Reading /home/rayofash/.mplayer/codecs.conf: Can't open '/home/rayofash/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: 91 audio & 204 video codecs
CommandLine: '-v' '[Anime-RG] Venus Versus Virus - 01 [WS][4AC4E600].mkv'
init_freetype
get_path('font/font.desc') -> '/home/rayofash/.mplayer/font/font.desc'
font: can't open file: /home/rayofash/.mplayer/font/font.desc
Font /usr/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/rayofash/.mplayer/input.conf'
Can't open input config file /home/rayofash/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 59 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
get_path('[Anime-RG] Venus Versus Virus - 01 [WS][4AC4E600].mkv.conf') -> '/home/rayofash/.mplayer/[Anime-RG] Venus Versus Virus - 01 [WS][4AC4E600].mkv.conf'
Playing [Anime-RG] Venus Versus Virus - 01 [WS][4AC4E600].mkv.
get_path('sub/') -> '/home/rayofash/.mplayer/sub/'
[file] File size is 179401034 bytes
STREAM: [file] [Anime-RG] Venus Versus Virus - 01 [WS][4AC4E600].mkv
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
[mkv] Found the head...
[mkv] + a segment...
[mkv] /---- [ parsing seek head ] ---------
[mkv] /---- [ parsing seek head ] ---------
[mkv] \---- [ parsing seek head ] ---------
[mkv] /---- [ parsing cues ] -----------
[mkv] \---- [ parsing cues ] -----------
[mkv] /---- [ parsing chapters ] ---------
[mkv] Chapter 1 from 00:00:00.000 to 00:00:00.000
[mkv] Chapter 2 from 00:01:23.300 to 00:00:00.000
[mkv] Chapter 3 from 00:02:53.000 to 00:00:00.000
[mkv] Chapter 4 from 00:12:12.000 to 00:00:00.000
[mkv] Chapter 5 from 00:12:20.000 to 00:00:00.000
[mkv] Chapter 6 from 00:22:10.000 to 00:00:00.000
[mkv] Chapter 7 from 00:23:40.000 to 00:00:00.000
[mkv] \---- [ parsing chapters ] ---------
[mkv] \---- [ parsing seek head ] ---------
[mkv] |+ segment information...
[mkv] | + timecode scale: 1000000
[mkv] | + duration: 1459.680s
[mkv] |+ segment tracks...
[mkv] | + a track...
[mkv] |  + Track number: 1
[mkv] |  + Track type: Video
[mkv] |  + Default flag: 1
[mkv] |  + Codec ID: V_MPEG4/ISO/AVC
[mkv] |  + CodecPrivate, length 39
[mkv] |  + Default duration: 33.367ms ( = 29.970 fps)
[mkv] |  + Language: jpn
[mkv] |  + Video track
[mkv] |   + Pixel width: 704
[mkv] |   + Pixel height: 400
[mkv] |   + Display width: 704
[mkv] |   + Display height: 400
[mkv] | + a track...
[mkv] |  + Track number: 2
[mkv] |  + Track type: Audio
[mkv] |  + Default flag: 1
[mkv] |  + Codec ID: A_MPEG/L3
[mkv] |  + Default duration: 24.000ms ( = 41.667 fps)
[mkv] |  + Language: jpn
[mkv] |  + Audio track
[mkv] |   + Sampling frequency: 48000.000000
[mkv] |   + Channels: 2
[mkv] | + a track...
[mkv] |  + Track number: 3
[mkv] |  + Track type: Subtitle
[mkv] |  + Default flag: 1
[mkv] |  + Codec ID: S_TEXT/***
[mkv] |  + CodecPrivate, length 724
[mkv] |  + Language: eng
[mkv] |+ found cluster, headers are parsed completely :)
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_MPEG/L3), -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang eng
==> Found video stream: 1
[mkv] Aspect: 1.760000
[mkv] Will play video track 1
==> Found audio stream: 2
[mkv] Will play audio track 2
Matroska file format detected.
VIDEO:  [avc1]  704x400  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:31  fourcc:0x31637661  size:704x400  fps:29.97  ftime:=0.0334
get_path('sub/') -> '/home/rayofash/.mplayer/sub/'
get_path('default.sub') -> '/home/rayofash/.mplayer/default.sub'
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
dec_audio: Allocating 4608 + 65536 = 70144 bytes for output buffer.
mp3lib: made decode tables with MMX optimization
mp3lib: using 3DNow!Ex optimized decore!
MP3lib: init layer2&3 finished, tables done
MPEG 1.0, Layer III, 48000 Hz 192 kbit Stereo, BPF: 576
Channels: 2, copyright: No, original: Yes, CRC: No, emphasis: 0
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports layers.
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Current fstype setting honours LAYER FULLSCREEN X atoms
Disabling DPMS
DPMSDisable stat: 1
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x0101fe).
[xv common] Maximum source image dimensions: 2046x2046
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
alsa-init: requested format: 48000 Hz, 2 channels, 9
alsa-init: compiled for ALSA-1.0.10
alsa-init: setup for 1/2 channel(s)
alsa-init: 1 soundcard found, using: default
alsa-init: pcm opend in block-mode
alsa-init: chunksize set to 1024
alsa-init: fragcount=16
alsa-init: got buffersize=65536
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio output
AO: Author: Alex Beregszaszi, Zsolt Barat <joy@streamminister.de>
AO: Comment: under developement
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
alsa-space: free space = 65536, prepared --
[ffmpeg] aspect_ratio: 0.000000
VDec: vo config request - 704 x 400 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.76:1 - prescaling to correct movie aspect.
VO Config (704x400->704x400,flags=0,'MPlayer',0x32315659)
VO: [xv] 704x400 => 704x400 Planar YV12
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 244 for hw scaling
[xv] dx: 0 dy: 0 dw: 704 dh: 400
*** [vo] Exporting mp_image_t, 704x400x12bpp YUV planar, 422400 bytes
[xv] dx: 0 dy: 0 dw: 704 dh: 400
Uninit audio filters... 0.001 ct:  0.030 286/286 55% 10%  1.3% 0 0
[libaf] Removing filter dummy
uninit audio: mp3lib
uninit video: ffmpeg
Successfully enabled DPMS
alsa-uninit: pcm closed
vo: uninit ...

Exiting... (Quit)
rayofash@SHODAN:~/Desktop$

---

### Post by shirilover on 2007-03-15
VLC does not support stylized subtitles like SSA.
Any recent version of MPlayer; i.e. 1.0rc1, should display the subtitles without any problem.
Be aware that MPlayer does not display the subtitle stream by default, you will need to select it or use the j key to cycle through the available subtitles.

---

### Post by rayofash on 2007-03-15
> **shirilover said:**
> VLC does not support stylized subtitles like SSA.
Any recent version of MPlayer; i.e. 1.0rc1, should display the subtitles without any problem.
Be aware that MPlayer does not display the subtitle stream by default, you will need to select it or use the j key to cycle through the available subtitles.

The subtitles work fine in VLC, I can't select them in MPlayer (using the j key like you said worked though). This is what i've been saying.

I want to get the *video* to work in *VLC*. I don't care about MPlayer. I *hate* MPlayer.

---

### Post by panch0 on 2007-03-16
Do you hate MPlayer or its GUI? There are other GUIs for it. KPlayer is the one I always recommend, especially if you are on KDE.

KPlayer lists subtitles on a submenu where you can select the ones you want to display.

By the way, your MPlayer is rather old, you should get 1.0rc1.

---

### Post by rayofash on 2007-03-16
I tried KPlayer, it didn't work. And what I hate about MPlayer is that it unpauses if you click anything, and you can't grab the bar and find places in your video.

---

### Post by amgeex on 2007-07-22
Try SMPlayer, its the next best thing since VLC. The inteface is ugly, but at least it displays subtitles ok, and you can move around in your video by dragging the progress bar. :D

Get it at getdeb.net

---

