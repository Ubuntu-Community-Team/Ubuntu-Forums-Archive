---
title: "Jaunty mplayers .flv failure"
date: 2009-04-27
forum: Multimedia Software
---

### Post by Matt_Rapp on 2009-04-27
I have been using mplayer to watch .flv videos for quite sometime now. Every once in awhile it would stop playing them and just closes as soon as the program appears, it doesn't start playing the video at all. The same thing happens when I try to play .mp4 files. The bug usually goes away on its own after a few restarts. However, I just updated to Jaunty and now mplayer is closing up again. It has not fixed itself after many restarts as it once did, though mplayer did work for awhile after the update. I have tried reinstalling mplayer and the problem still persists. 

xine is able to still play .flv files but they are cropped funny and i would rather just continue to use mplayer.

Any ideas?



Also anybody know a good gui program to convert .flv and other videos. I know about ffmpeg but I do not want to mess around in the terminal all the time.

---

### Post by andrew.46 on 2009-04-28
Hi Matt_Rapp,

> **Matt_Rapp said:**
> I have been using mplayer to watch .flv videos for quite sometime now. Every once in awhile it would stop playing them and just closes as soon as the program appears, it doesn't start playing the video at all. The same thing happens when I try to play .mp4 files. 

Can you open one of the troublesome files on the commandline as follows:

```
mplayer -v myfile.flv
```

and post the entire terminal output here? This may very well yield some diagnostic information.

All the best,

Andrew

---

### Post by Matt_Rapp on 2009-04-28
Here are the results,

```
pwd

/media/Data/Movies

matt@Matt-Ubuntu:/media/Data/Movies$ mplayer -v "Fanfare For The Common Man.flv"MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team

CPU: AMD Sempron(tm) Processor 3000+ (Family: 15, Model: 44, Stepping: 2)

CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1

Compiled with runtime CPU detection.

get_path('codecs.conf') -> '/home/matt/.mplayer/codecs.conf'

Reading /home/matt/.mplayer/codecs.conf: Can't open '/home/matt/.mplayer/codecs.conf': No such file or directory

Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory

Using built-in default codecs.conf.

Configuration: --enable-runtime-cpudetection --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-gui --enable-mencoder

CommandLine: '-v' 'Fanfare For The Common Man.flv'

init_freetype

get_path('font/font.desc') -> '/home/matt/.mplayer/font/font.desc'

font: can't open file: /home/matt/.mplayer/font/font.desc

font: can't open file: /usr/share/mplayer/font/font.desc

Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay

get_path('fonts') -> '/home/matt/.mplayer/fonts'

Using nanosleep() timing

get_path('input.conf') -> '/home/matt/.mplayer/input.conf'

Can't open input config file /home/matt/.mplayer/input.conf: No such file or directory

Parsing input config file /etc/mplayer/input.conf

Input config file /etc/mplayer/input.conf parsed: 81 binds

Setting up LIRC support...

mplayer: could not connect to socket

mplayer: No such file or directory

Failed to open LIRC support. You will not be able to use your remote control.

get_path('Fanfare For The Common Man.flv.conf') -> '/home/matt/.mplayer/Fanfare For The Common Man.flv.conf'



Playing Fanfare For The Common Man.flv.

get_path('sub/') -> '/home/matt/.mplayer/sub/'

[file] File size is 2796846 bytes

STREAM: [file] Fanfare For The Common Man.flv

STREAM: Description: File

STREAM: Author: Albeu

STREAM: Comment: based on the code from ??? (probably Arpi)

LAVF_check: flv format

libavformat file format detected.

==> Found video stream: 0

[lavf] Video stream found, -vid 0

======= VIDEO Format ======

  biSize 40

  biWidth 320

  biHeight 240

  biPlanes 0

  biBitCount 0

  biCompression 827739206='FLV1'

  biSizeImage 0

===========================

==> Found audio stream: 1

[lavf] Audio stream found, -aid 1

======= WAVE Format =======

Format Tag: 85 (0x55)

Channels: 1

Samplerate: 22050

avg byte/sec: 8000

Block align: 1

bits/sample: 16

cbSize: 0

==========================================================================

LAVF: 1 audio and 1 video streams found

LAVF: build 3345920

VIDEO:  [FLV1]  320x240  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)

[V] filefmt:44  fourcc:0x31564C46  size:320x240  fps:29.97  ftime:=0.0334

get_path('sub/') -> '/home/matt/.mplayer/sub/'

X11 opening display: :0.0

vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)

vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)

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

Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family

INFO: libavcodec init OK!

Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)

==========================================================================

==========================================================================

Forced audio codec: mad

Opening audio decoder: [libmad] libmad mpeg audio decoder

dec_audio: Allocating 4096 bytes for input buffer.

dec_audio: Allocating 9216 + 65536 = 74752 bytes for output buffer.

AUDIO: 22050 Hz, 1 ch, s16le, 64.0 kbit/18.14% (ratio: 8000->44100)

Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)

==========================================================================

Building audio filter chain for 22050Hz/1ch/s16le -> 0Hz/0ch/??...

[libaf] Adding filter dummy 

[dummy] Was reinitialized: 22050Hz/1ch/s16le

[dummy] Was reinitialized: 22050Hz/1ch/s16le

AO: [pulse] 22050Hz 1ch s16le (2 bytes per sample)

AO: Description: PulseAudio audio output

AO: Author: Lennart Poettering

Building audio filter chain for 22050Hz/1ch/s16le -> 22050Hz/1ch/s16le...

[dummy] Was reinitialized: 22050Hz/1ch/s16le

[dummy] Was reinitialized: 22050Hz/1ch/s16le

Starting playback...

[ffmpeg] aspect_ratio: 0.000000

VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)

Trying filter chain: vo

VDec: using Planar YV12 as output csp (no 0)

Movie-Aspect is undefined - no prescaling applied.

VO Config (320x240->320x240,flags=0,'MPlayer',0x32315659)

VO: [xv] 320x240 => 320x240 Planar YV12 

VO: Description: X11/Xv

VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others

Xvideo image format: 0x32595559 (YUY2) packed

Xvideo image format: 0x32315659 (YV12) planar

Xvideo image format: 0x59565955 (UYVY) packed

Xvideo image format: 0x30323449 (I420) planar

using Xvideo port 355 for hw scaling

[xv] dx: 0 dy: 0 dw: 320 dh: 240

*** [vo] Allocating (slices) mp_image_t, 320x240x12bpp YUV planar, 115200 bytes

get_path('subfont.ttf') -> '/home/matt/.mplayer/subfont.ttf'

Unicode font: 5009 glyphs.

[xv] dx: 480 dy: 392 dw: 320 dh: 240

*** [vo] Allocating (slices) mp_image_t, 320x240x12bpp YUV planar, 115200 bytes

[xv] dx: 823 dy: 334 dw: 320 dh: 240.007 182/182  5%  0%  0.4% 3 0 

Uninit audio filters...-0.001 ct:  0.021 670/670  1%  0%  0.4% 3 0 

[libaf] Removing filter dummy 

Uninit audio: libmad

Uninit video: ffmpeg

Successfully enabled DPMS

GNOME screensaver enabled

vo: uninit ...



Exiting... (Quit)

matt@Matt-Ubuntu:/media/Data/Movies$ 
```

The video opened in a small player window with no toolbar or play/pause buttons. When I tried it the first few times from the terminal I would get the same type of window, but sound and a black screen with jagged colors only. When I try and double click a .flv or .mp4 file from nautilus the player still opens quickly then closes as before.

---

### Post by andrew.46 on 2009-04-29
Hi,

Can I ask where you picked up this copy of MPlayer? If you are having a primary video display problem a troubleshooting option is to test different 'video out' settings. Settings available to you can be seen by running:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vo help[/COLOR]**
MPlayer SVN-r29237-4.2.4 (C) 2000-2009 MPlayer Team
Available video output drivers:
	xv	X11/Xv
	x11	X11 ( XImage/Shm )
	xover	General X11 driver for overlay capable video output drivers
	gl	X11 (OpenGL)
	gl2	X11 (OpenGL) - multiple textures version
	dga	DGA ( Direct Graphic Access V2.0 )
	sdl	SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
	fbdev	Framebuffer Device
	fbdev2	Framebuffer Device
	svga	SVGAlib
	aa	AAlib
	caca	libcaca
	v4l2	V4L2 MPEG Video Decoder Output
	xvidix	X11 (VIDIX)
	cvidix	console VIDIX
	null	Null video output
	mpegpes	MPEG-PES to DVB card
	yuv4mpeg	yuv4mpeg output for mjpegtools
	png	PNG file
	jpeg	JPEG file
	gif89a	animated GIF output
	tga	Targa output
	pnm	PPM/PGM/PGMYUV file
	md5sum	md5sum of each frame

```

And then testing as follows:

```

mplayer -vo xv 'Fanfare For The Common Man.flv'
mplayer -vo gl 'Fanfare For The Common Man.flv'

```

and so on...

Andrew

---

### Post by Matt_Rapp on 2009-04-29
I never downloaded mplayer separately from just installing the distro, other than when I reinstalled the packages through synaptic.

I have tried all the extensions up to caca so far, only one failed entirely, most just play audio some with a black screened player window others with no widow at all. The extensions that work so far are as follows: gl works for .flv and .mp4 , gl2 and sdl work for .flv, i haven't tried either of them with .mp4's yet,

---

### Post by andrew.46 on 2009-04-29
Hi Matt_Rapp,

> **Matt_Rapp said:**
> I never downloaded mplayer separately from just installing the distro, other than when I reinstalled the packages through synaptic.

I have tried all the extensions up to caca so far, only one failed entirely, most just play audio some with a black screened player window others with no widow at all. The extensions that work so far are as follows: gl works for .flv and .mp4 , gl2 and sdl work for .flv, i haven't tried either of them with .mp4's yet,

Well, some of those 'video out's are a little crazy (caca and aa) and some are of little practical use :-). But at least it demonstrates that the files are not broken and that MPlayer can be coaxed in to working. You could try a few things, in descending order:

[LIST=1]
[*]Install the meta package *ubuntu-restricted-extras*. This big package might fix a possibly global problem wih your system.
[*]Install the Medibuntu MPlayer and the extra codec pack. This will always be a more able version of MPlayer than the standard repository version.
[*]Try vlc. The Jaunty has a nice version in place and this might be worth a try. I have a version of vlc on my own system for backup and comparison at least.
[*]Replace the repository MPlayer and compile MPlayer from source. I read your note about the commandline and perhaps you might not be keen on this. But it is how I run my own copy and I have written a guide [here]("http://ubuntuforums.org/showthread.php?t=1081070").
[/LIST]

I have a little suspicion that you might have more of a *system* problem than a *media* problem but perhaps one of the above might at least get some reliable media playback going.

Andrew

---

### Post by Matt_Rapp on 2009-04-29
I already had the restricted extras package installed,
I tried the Medibuntu thing, add it and did an update, installed all the packages that came up, now I have GNOME Mplayer which does audio only, black screen, but no random colors! 
I tried to install vlc from the terminal, apt-get install... I tried playing some videos from terminal with it but it says VLC -(caca) and has a really blurry picture with random text running over it, sounds fine though. How should I go about getting rid of caca which must have been set somehow when I was working with mplayer in terminal earlier?

---

### Post by andrew.46 on 2009-04-29
Hi Matt_Rapp,

> **Matt_Rapp said:**
> I tried to install vlc from the terminal, apt-get install... I tried playing some videos from terminal with it but it says VLC -(caca) and has a really blurry picture with random text running over it, sounds fine though. How should I go about getting rid of caca which must have been set somehow when I was working with mplayer in terminal earlier?

vlc options are set from: Tools --> Preferences --> Video --> Output. There is a dropdown box there for these settings and usually 'Default' does the job but perhaps not in your case.

I will confess that I am more than a little puzzled why the Medibuntu MPlayer cannot play something as simple as an flv file, and in fact I have little more to offer as a solution. However in the unlikely case that you have a big batch of broken flv files I have uploaded a short sample to my own website for your to test. It is a standard low quality sample:

```

Duration: 00:00:15.51, start: 0.000000, bitrate: 64 kb/s
Stream #0.0: Video: flv, yuv420p, 320x240, 15 tbr, 1k tbn, 1k tbc
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s

```

and can be downloaded as follows:

```
wget http://www.andrews-corner.org/samples/linux.flv
```

and I attach a screenshot of MPlayer successfully playing this small flv. With any luck your system will play this file as well :-).

Andrew

---

### Post by Matt_Rapp on 2009-04-29
here is what I got, I attached a screenshot as well.

```
matt@Matt-Ubuntu:~$ mplayer linux.flv
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor 3000+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing linux.flv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x240  0bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 22050 Hz, 1 ch, s16le, 64.0 kbit/18.14% (ratio: 8000->44100)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 22050Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x240 => 320x240 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.7% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.6% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.5% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)0.4% 0 0 
Cannot sync MAD frame: -0.009 ct: -0.063 219/219  1%  0%  0.4% 0 0 
Cannot sync MAD frame
Cannot sync MAD frame
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame: -0.015 ct: -0.064 220/220  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame: -0.022 ct: -0.066 221/221  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame: -0.027 ct: -0.070 222/222  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame: -0.043 ct: -0.074 223/223  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame:  0.140 ct: -0.067 224/224  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame:  0.073 ct: -0.061 225/225  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame:  0.006 ct: -0.060 226/226  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame: -0.060 ct: -0.066 227/227  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame: -0.127 ct: -0.073 228/228  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame: -0.194 ct: -0.079 229/229  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame: -0.260 ct: -0.086 230/230  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame: -0.327 ct: -0.093 231/231  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
Cannot sync MAD frame: -0.394 ct: -0.099 232/232  1%  0%  0.4% 0 0 
A:  15.1 V:  15.5 A-V: -0.394 ct: -0.106 232/232  1%  0%  0.4% 0 0 
X11 error: BadAlloc (insufficient resources for operation)
GNOME screensaver enabled

Exiting... (End of file)
matt@Matt-Ubuntu:~$ 
```

The audio still came through.

---

### Post by andrew.46 on 2009-04-30
Hi Matt_Rapp,

I have a deep suspicion that this is a video display problem related to your system and not an MPlayer problem. You could try as a final thing:

```
mplayer -vo x11 linux.flv
```

but I suspect you will need to look at your video display / driver and somebody cleverer than me to find a solution.

Apologies,

Andrew

---

### Post by Matt_Rapp on 2009-04-30
Okay that worked. Is there a way to integrate this command, mplayer -vo x11, into the way Nautilus is programed to open .flv and .mp4 files? I know you can do "open with > open with other application > Use a custom command", but it doesn't seem to have a way to make that custom command permanent. It does work though.

---

### Post by Matt_Rapp on 2009-04-30
Never mind I figured it out, thanks a ton for all your help!!!! 

Even though there still no tool-bar the keyboard short cuts will work just fine.

---

### Post by andrew.46 on 2009-04-30
Hi Matt_Rapp,

> **Matt_Rapp said:**
> Never mind I figured it out, thanks a ton for all your help!!!! 

Well I am glad that it has all worked out although I think we were both groping around in the dark more than a little :-).

All the best,

Andrew

---

