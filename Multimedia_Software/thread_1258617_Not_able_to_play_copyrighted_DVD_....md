---
title: "Not able to play copyrighted DVD ..."
date: 2009-09-05
forum: Multimedia Software
---

### Post by dagarshali on 2009-09-05
HI,
I am using ubuntu Jaunty and I have followed the guides in documentation and installed the restricted packages. However, when I try to play the DVD using VLC, it just closes and if I try movie player and play, it gives a error saying you may not have the permission to open the file..

I have a lenovo Y450 laptop, with nvidia geforce g 105 graphics card..

thanks,
Vishwa

---

### Post by jerrrys on 2009-09-05
win32 ??

[http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback)

[http://ubuntuforums.org/showthread.php?t=1155698&highlight=vlc](http://ubuntuforums.org/showthread.php?t=1155698&highlight=vlc)

---

### Post by dagarshali on 2009-09-05
hi,
Thanks for the response.. I had installed the libdvdcss already.. I now installed w32codecs and the result is still the same :(

---

### Post by wojox on 2009-09-05
Open Synaptic

Download mplayer and gnome gui for it

also 

libdvdcss2

---

### Post by dagarshali on 2009-09-05
did download mplayer with gnome-gui...but it still doesn't open..:(

Its so frustrating..

---

### Post by wojox on 2009-09-05
Do you Medibuntu:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by dagarshali on 2009-09-05
Yes, I followed the instructions for medibuntu as well :(

---

### Post by andrew.46 on 2009-09-05
Hi Vishwa,

> **dagarshali said:**
> I am using ubuntu Jaunty and I have followed the guides in documentation and installed the restricted packages. However, when I try to play the DVD using VLC, it just closes and if I try movie player and play, it gives a error saying you may not have the permission to open the file..

Do you have a copy of MPlayer on your system? If so try running the following command and then post the terminal output:

```
mplayer -v dvd://
```

Hopefully this will give a few hints as to what is going on...

Andrew

---

### Post by dagarshali on 2009-09-06
Here is the result of mplayer -v dvd://

It opened and started playing though..but the video was very bad and the voice was creaky too..



MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     P7450  @ 2.13GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/dagarshali/.mplayer/codecs.conf'
Reading /home/dagarshali/.mplayer/codecs.conf: Can't open '/home/dagarshali/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-libamr_nb --enable-libamr_wb --enable-faac --enable-gui --enable-mencoder
CommandLine: '-v' 'dvd://'
init_freetype
get_path('font/font.desc') -> '/home/dagarshali/.mplayer/font/font.desc'
font: can't open file: /home/dagarshali/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/dagarshali/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/dagarshali/.mplayer/input.conf'
Can't open input config file /home/dagarshali/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('.conf') -> '/home/dagarshali/.mplayer/.conf'

Playing dvd://.
get_path('sub/') -> '/home/dagarshali/.mplayer/sub/'
URL: dvd://
Reading disc structure, please wait...
There are 26 titles on this DVD.
There are 2 chapters in this DVD title.
There are 1 angles in this DVD title.
*** Zero check failed in ifo_read.c:1361
    for vts_tmapt->zero_1 = 0x970a
*** Zero check failed in ifo_read.c:1535
    for c_adt->zero_1 = 0x44b6
*** Zero check failed in ifo_read.c:1535
    for c_adt->zero_1 = 0x44b6
libdvdread: Invalid title IFO (VTS_01_0.IFO).
DVD successfully opened.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
number of audio channels on disk: 1.
subtitle ( sid ): 0 language: es
subtitle ( sid ): 1 language: pt
subtitle ( sid ): 2 language: zh
subtitle ( sid ): 3 language: ko
subtitle ( sid ): 4 language: th
number of subtitles on disk: 5
DVD start cell: 0  pack: 0x0-0xB92AC  
DVD start=0 end=759163  
STREAM: [null] dvd://
STREAM: Description: DVD stream
STREAM: Author: 
STREAM: Comment: 
DVD Seek! lba=0x0  cell=0  packs: 0x0-0xB92AC  
Angle-seek synced by cell/vob IDN search!  
system stream synced at 0x7680D (485389)!
==> Found video stream: 0
MPEG-PS file format detected.
==> Found audio stream: 128
Searching for sequence header... OK!
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  7500.0 kbps (937.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
get_path('sub/') -> '/home/dagarshali/.mplayer/sub/'
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1366x768 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2046x2046
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
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
Using SSE optimized IMDCT transform
AC3: 2.0 (stereo)  48000 Hz  192.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0x2
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
a52: CRC check failed!  
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO Config (720x480->854x480,flags=0,'MPlayer',0x32315659)
VO: [xv] 720x480 => 854x480 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 280 for hw scaling
[xv] dx: 0 dy: 0 dw: 854 dh: 480
*** [vo] Allocating mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
[xv] dx: 256 dy: 144 dw: 854 dh: 480
a52: CRC check failed!  0.851 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 
a52: error at resampling
==> Found subtitle: 2
==> Found subtitle: 0
==> Found subtitle: 1
*** [vo] Allocating mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
==> Found subtitle: 3:  0.358 ct:  0.003   2/  2 ??% ??% ??,?% 1 0 
==> Found subtitle: 4
get_path('subfont.ttf') -> '/home/dagarshali/.mplayer/subfont.ttf'
Unicode font: 5009 glyphs.
*** [vo] Allocating mp_image_t, 720x480x12bpp YUV planar, 518400 bytes
a52: CRC check failed!  0.575 ct:  0.010   4/  4 ??% ??% ??,?% 3 0 
a52: error at resampling
a52: CRC check failed!  0.054 ct:  0.057  18/ 18 46%  2% 332.2% 10 0 
a52: error at resampling
a52: CRC check failed!  0.092 ct:  0.063  20/ 20 42%  2% 313.4% 10 0 
a52: error at resampling
a52: CRC check failed!  0.266 ct:  0.100  31/ 31 30%  1% 298.2% 14 0 
a52: error at resampling
a52: CRC check failed!  0.286 ct:  0.103  32/ 32 31%  1% 309.5% 15 0 
a52: error at resampling
a52: CRC check failed!  0.263 ct:  0.114  42/ 42 26%  1% 259.3% 18 0 
a52: CRC check failed!  0.331 ct:  0.141  50/ 50 24%  1% 257.5% 22 0 
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  0.325 ct:  0.145  51/ 51 24%  1% 260.4% 23 0 
a52: CRC check failed!  0.114 ct:  0.175  60/ 60 23%  1% 241.2% 26 0 
a52: error at resampling
a52: CRC check failed!  0.079 ct:  0.181  62/ 62 23%  1% 235.3% 26 0 
a52: error at resampling
Invalid NAVI packet! lba=0x5AA  navi=0x5A9  / 65 22%  1% 224.5% 26 0 
Invalid NAVI packet! lba=0x5AB  navi=0x5A9  
a52: CRC check failed!  
a52: CRC check failed!  0.040 ct:  0.222  75/ 75 21%  1% 227.3% 30 0 
a52: error at resampling
a52: CRC check failed!  0.014 ct:  0.224  76/ 76 21%  1% 225.6% 30 0 
a52: error at resampling
a52: CRC check failed!  0.083 ct:  0.208  82/ 82 21%  1% 218.3% 30 0 
a52: error at resampling
Uninit audio filters... 0.384 ct:  0.212  83/ 83 21%  1% 239.6% 31 0 
[libaf] Removing filter dummy 
Uninit audio: liba52
Uninit video: libmpeg2
Successfully enabled DPMS
GNOME screensaver enabled
vo: uninit ...

Exiting... (Quit)

---

### Post by dagarshali on 2009-09-06
result of vlc -v dvd:// is here

VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: Casino Royale (Bonus Disc)
libdvdnav: DVD Serial Number: 36318e72
libdvdnav: DVD Title (Alternative): Casino Royale (Bonus Disc)
libdvdnav: Unable to find map file '/home/dagarshali/.dvdnav/Casino Royale (Bonus Disc).map'
libdvdnav: DVD disk reports itself with Region mask 0x00f20000. Regions: 1 3 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001a8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000225
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0004027e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0004027e)!!
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000f9841
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00132999
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001ce79d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001ce7d6
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x001ce7d6)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00227c88
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x00227c88)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00227cc1
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x00227cc1)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0029e4d6
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x0029e4d6)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0029e50f
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x0029e50f)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003129ac
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_0.VOB (0x003129ac)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003129e5
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x003129e5)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00312d11
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00312d4a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x00312d4a)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0032e2e4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_0.VOB (0x0032e2e4)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0032e31d
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x0032e31d)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0033a739
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0033a772
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x0033a772)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x00346ef9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x00346f32
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_1.VOB (0x00346f32)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00352e32
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_0.VOB (0x00352e32)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x00352e6b
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_1.VOB (0x00352e6b)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x0035eb37
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x0035eb70
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_12_1.VOB (0x0035eb70)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x0036b175
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x0036b1ae
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_13_1.VOB (0x0036b1ae)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x0037491e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_14_0.VOB (0x0037491e)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x00374957
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_14_1.VOB (0x00374957)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x00375cd8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_15_0.VOB (0x00375cd8)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x00375d11
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_15_1.VOB (0x00375d11)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x00378270
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_16_0.VOB (0x00378270)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x003782a9
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_16_1.VOB (0x003782a9)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x00379b6d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x00379ba6
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_17_1.VOB (0x00379ba6)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_0.VOB at 0x0037b355
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x0037b38e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_18_1.VOB (0x0037b38e)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_0.VOB at 0x0037c671
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_1.VOB at 0x0037c6aa
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_19_1.VOB (0x0037c6aa)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_0.VOB at 0x0037d012
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_20_0.VOB (0x0037d012)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_1.VOB at 0x0037d04b
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_20_1.VOB (0x0037d04b)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_0.VOB at 0x0037d6a9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_1.VOB at 0x0037d6e2
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_21_1.VOB (0x0037d6e2)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_0.VOB at 0x0037e171
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_1.VOB at 0x0037e1aa
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_22_1.VOB (0x0037e1aa)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_23_0.VOB at 0x0037e77a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_23_0.VOB (0x0037e77a)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_23_1.VOB at 0x0037e7b3
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_23_1.VOB (0x0037e7b3)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_24_0.VOB at 0x0037f0df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_24_1.VOB at 0x0037f118
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_24_1.VOB (0x0037f118)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_25_0.VOB at 0x0037f79c
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_25_0.VOB (0x0037f79c)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_25_1.VOB at 0x0037f7d5
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_25_1.VOB (0x0037f7d5)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_26_0.VOB at 0x00380754
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_26_0.VOB (0x00380754)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_26_1.VOB at 0x0038078d
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_26_1.VOB (0x0038078d)!!
libdvdread: Elapsed time 0
libdvdread: Found 26 VTS's
libdvdread: Elapsed time 7
libdvdnav: ifoRead_PGCI_UT failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted

---

### Post by andrew.46 on 2009-09-06
Hi dagarshali,

Your vlc results seem to indicated that the copy protection on the DVD renders it unplayable on your system. Not sure if there is a way around this. Oddly enough MPlayer seems to have moved past the protection but I note the error message where libdvdread/libdvdcss *should* be running:

```
libdvdread: Invalid title IFO (VTS_01_0.IFO)
```

and subsequently libdvdcss is not used at all. A *correct* read of a DVD is more like:

```

andrew@skamandros~$ mplayer dvd:// -demuxer lavf
MPlayer SVN-r29652-4.3.3 (C) 2000-2009 MPlayer Team

Playing dvd://.
**[COLOR="Red"]libdvdread: Using libdvdcss version 1.2.10 for DVD access[/COLOR]**
There are 3 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000137
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001a4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000aae2
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000d42f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000d486
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00391d46
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00391d9d
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 1
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
number of audio channels on disk: 1.
number of subtitles on disk: 0
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [MPG2]  720x576  0bpp  25.000 fps  8549.2 kbps (1043.6 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
A:  15.3 V:  23.4 A-V: -8.120 ct: -0.784   0/  0 12%  0% 12.8% 2 0 
Exiting... (Quit)
andrew@skamandros~$ 

```

Could be a bad backup copy of a dvd perhaps?

Andrew

---

### Post by mc4man on 2009-09-06
That title and 2 others (Stranger than Fiction, I forget the other) have a rather strong structure protection that caused sony some embarrassment.

It shouldn't prevent playback though and I don't know if it was even used on the 'bonus'disc.

So one question would be -** can you play the main disk?**

You could try to develop some dvdccs debugging and or use a different decryption method.

Because it's already failing with the default method I'd do both at once.

Note that if a key cache exists the dvdcss debug is worthless, the cache is used by default.
So you must first find the .dvdcss folder in home dir. and delete it (,dvdcss is a hidden folder in your home folder, I could give you a rm command but don't like posting rm's

Put the dvd in the drive and close out any player if they open
**Then** delete the .dvdcss folder

In a terminal
```
export DVDCSS_VERBOSE=2
```

Then this command will change the key method ( from disk to title and produce output, after vlc opens just close it and look in home folder for the vlc_output file. You only care about what's under this line
"libdvdread: Using libdvdcss version 1.2.10 for DVD access"

```
export DVDCSS_METHOD=title && vlc dvd:// > vlc_output 2>&1


```


edit : as an ex. showing diif. methods, same disc

default disc (player) key - after deleting .dvdcss
> libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00018535
libdvdcss debug: getting title key at block 99637 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: initial disc key 11:a6:e2:e0:d2
libdvdcss debug: decrypted title key ec:08:23:b5:83
libdvdcss debug: title key is ec:08:23:b5:83
libdvdread: Elapsed time 0


Then using 'title' method on same disc 

> libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00018535
libdvdcss debug: cracking title key at block 99637
libdvdcss debug: successful attempts 1/1, scrambled blocks 1/2
libdvdcss debug: vts key initialized
libdvdcss debug: title key is ec:08:23:b5:83
libdvdread: Elapsed time 0


Note that the exports should be run from the same terminal

---

### Post by me13221 on 2010-03-01
> **andrew.46 said:**
> Hi dagarshali,

Your vlc results seem to indicated that the copy protection on the DVD renders it unplayable on your system. Not sure if there is a way around this. Oddly enough MPlayer seems to have moved past the protection but I note the error message where libdvdread/libdvdcss *should* be running:
...


Could be a bad backup copy of a dvd perhaps?

Andrew

I'm having the same problem on a Karmic system on a known-good DVD.  Not being able to play DVDs?  I feel like I'm back in 2003.  this blows.

The relevant error is:

```

libdvdread: Invalid title IFO (VTS_01_0.IFO).
Cannot open the IFO file for DVD title 1.

```

---

### Post by me13221 on 2010-03-01
Fixed now.  I had to:

```

sudo apt-get install ubuntu-restricted-extras libdvdcss2 libdvdnav2
sudo /usr/share/doc/libdvdread4/install-css.sh

```

I believe that was what did the trick.

---

