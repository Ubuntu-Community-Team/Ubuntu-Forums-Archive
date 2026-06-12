---
title: "ogv and mp4 video playback looks scrambled"
date: 2011-04-08
forum: Multimedia Software
---

### Post by Redsandro on 2011-04-08
Both **MP4** and **OGV** playback completely weird on my Ubuntu 10.04.2 laptop:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=188448&stc=1&d=1302250724[/IMG]

The resolution/length/etc is correct, but the picture is all weird. **Webm** doesn't work at all.

I tried mplayer, kmplayer, smplayer, gxine, totem and kplayer. All the same.

However, the exact same video's play back normally in HTML5 pages with a bunch of browsers on the same machine. They also play back normally on a Windows machine. There is no DRM involved.

Aren't these gstreamer en mplayer based players supposed to handle this correctly?

This is an Intel Core i3 machine with Intel HD graphics.

---

### Post by SeijiSensei on 2011-04-08
In smplayer, what video driver are you using?  If you're not using xv, try that.  Another place to look is in the mplayer logs (Settings > Logs).  You can also watch what happens by running mplayer from the command prompt like this: "mplayer /path/to/the/file.mp4".  You can get more details by adding -v to the options ("mplayer -v /path/to/the/file.mp4") though the amount of detail it produces in verbose mode in pretty overwhelming.  More "v's" will give you more detail.

At the command prompt type "mplayer -vo help" to see what video drivers are supported; "mplayer -vc help" will list the available video codecs. I'm guessing you have the codecs but the wrong output driver.

---

### Post by Redsandro on 2011-04-08
Thanks for the quick reply.

Not sure where you find that driver, but in SMPlayer, I changed
*Settings > Configure > General Options > Output > Auto*
to
*Settings > Configure > General Options > Output > XVideo*
and I got the same result.

Here's the output from mplayer -v, it's a lot so I only did an ogg theora test. mp4 is probably sort of similar.

```
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 11
CPU: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz (Family: 6, Model: 37, Stepping: 5)
extended cpuid-level: 8
extended cache-info: 16801856
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/redsandro/.mplayer/codecs.conf'
Reading /home/redsandro/.mplayer/codecs.conf: Can't open '/home/redsandro/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' 'htest.ogv'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/redsandro/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/redsandro/.mplayer/input.conf'
Can't open input config file /home/redsandro/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('htest.ogv.conf') -> '/home/redsandro/.mplayer/htest.ogv.conf'

Playing htest.ogv.
get_path('sub/') -> '/home/redsandro/.mplayer/sub/'
[file] File size is 4795079 bytes
STREAM: [file] htest.ogv
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: Ogg
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for REAL
Checking for SMJPEG
==> Found video stream: 0
[Ogg] stream 0: video (Theora v3.2.1), -vid 0
======= VIDEO Format ======
  biSize 40
  biWidth 940
  biHeight 290
  biPlanes 3
  biBitCount 24
  biCompression 1868916852='theo'
  biSizeImage 817800
===========================
Ogg stream length (granulepos): 3571
Ogg demuxer : found 0 audio stream, 1 video stream and 0 text stream
Ogg file format detected.
VIDEO:  [theo]  940x290  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:940x290  fps:23.976  ftime:=0.0417
get_path('sub/') -> '/home/redsandro/.mplayer/sub/'
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
Disabling DPMS
DPMSDisable stat: 1
[VO_XV] Using Xv Adapter #0 (Intel(R) Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2048x2048
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x7fcb7e5d88a0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
INFO: Theora video init ok!
VDec: vo config request - 940 x 290 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 3.24:1 - prescaling to correct movie aspect.
VO Config (940x290->940x290,flags=0,'MPlayer',0x32315659)
VO: [xv] 940x290 => 940x290 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x434d5658 (XVMC) planar
using Xvideo port 77 for hw scaling
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
Audio: no sound
Freeing 0 unused audio chunks.
Starting playback...
*** [vo] Exporting mp_image_t, 944x304x12bpp YUV planar, 430464 bytes
Unicode font: 5025 glyphs.
Unicode font: 5025 glyphs.
Uninit video: theora  1%  0.0% 0 0 
Successfully enabled DPMS
vo: uninit ...

Exiting... (Quit)

```

```
$ mplayer -vc help | grep theo
theora      theora    working   Theora (free, reworked VP3)  [libtheora]
fftheora    ffmpeg    untested  FFmpeg Theora  [theora]
```

The mplayer probing errors are pretty normal. But maybe it makes a wrong choice, somehow just like every other player does, while not all of them are based on mplayer. Any hints on what to try with the -vo driver output?

---

### Post by Redsandro on 2011-04-08
You were right. It's a driver thing. I don't know anything about these, so which one is best?

```
	xmga	error (no playback)
	mga	error (no playback)
	tdfxfb	
	3dfx	
-	xv	Original error (like topicstart screenshot)
	vdpau	error (no playback) (should have known, nVidia thing)
*	x11	X11 WORKS
	xover	error (no playback)
*	gl	X11 WORKS
*	gl2	X11 WORKS
	dga	DGA error (no playback)
-	sdl	SDL Original error (like topicstart screenshot)
	fbdev	error (no playback)
	fbdev2	error (no playback)
	svga	error (no playback)
	aa	lol works but leaves terminal unusable
	caca	lol works
	v4l2	error (no playback)
	direcfb	error (no playback)
	dfbmga	
	xvidix	
	cvidix	
	null	
	xvmc	
	mpegpes	
	yuv4mpeg
```

Since xv is autodetected but not working, is it safe to say there's a bug in the videocard driver for Intel HD Video?

---

### Post by SeijiSensei on 2011-04-09
> **Redsandro said:**
> Since xv is autodetected but not working, is it safe to say there's a bug in the videocard driver for Intel HD Video?

I don't know.  I only ever use NVIDIA+VDPAU if I can help it.

I'm surprised xv doesn't work; I thought it was one of the most generic drivers.  Of the ones you identify as correct, perhaps gl2 makes the most sense.  x11 is quite old, and gl2 is probably a more recent OpenGL implementation than gl itself.

As for the location of the video driver drop-down menu, I gave you the wrong location.  On my smplayer [v.0.6.9 (SVN r3447)], the relevant menu is in Options > Preferences > Video.

In the past I've installed smplayer from [rvm's own PPA repository]("https://launchpad.net/~rvm/+archive/smplayer"), but it's been such a long time since he's updated it, the [release versions]("http://packages.ubuntu.com/lucid/smplayer") looks up-to-date.  Make sure you're running 0.6.9-1 if you want to be current.

---

### Post by Redsandro on 2011-04-09
Thanks for the information. I now have all players running correctly. Even the Gnome default player that nobody likes can be configured with the hidden program: gstreamer-properties.

MPlayer (-vo)
Video Driver: gl2

gstreamer-properties (for Totem / Gnome Video Player)
Video Driver: X Window System (No XV)

gxine (File > Configure > Preferences > Video (in Advanced Mode only))
Video Driver: xshm

VLC (Tools > Preferences > Video)
Video Driver:  OpenGL video output

Too bad I can't figure out which player I want to stick with. Mplayer based stuff seems best, but no nice gtk gui.

---

### Post by andrew.46 on 2011-04-09
> **Redsandro said:**
> Too bad I can't figure out which player I want to stick with. Mplayer based stuff seems best, but no nice gtk gui.

MPlayer actually does have a gtk gui but most do not build it as it has not been developed for some time and has many problems. Mind you I believe that the gnome MPlayer is actually the best gtk gui for MPlayer currently available but you are not keen on it?

---

### Post by Redsandro on 2011-04-09
That **Gnome player** I really don't like is **Totem** (default), but I haven't really given **Gnome Mplayer** much consideration. I don't really like that it's not just a GUI, it links *statically* to the complete MPlayer package.

This means that the multithreaded mplayer I installed is not working with Gnome Mplayer. It just uses it's own mplayer.

What is your media player of choice if not mplayer?

---

### Post by andrew.46 on 2011-04-09
> **Redsandro said:**
> What is your media player of choice if not mplayer?

Well I guess I have an interest in the commandline MPlayer, in part because I support a guide on these forums for building it:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

but I have more recently acquired a substantial interest in vlc, also with a guide:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

So my answer is that I use both but I believe you must really build your own to unlock the real power of both, a power that is often masked by Ubuntu packaging.

---

### Post by SeijiSensei on 2011-04-09
> **Redsandro said:**
> Too bad I can't figure out which player I want to stick with. Mplayer based stuff seems best, but no nice gtk gui.

What's wrong with **smplayer**?  Seems pretty nice to me. It's the only player I use.

---

### Post by Redsandro on 2011-04-10
> **andrew.46 said:**
> Well I guess I have an interest in the commandline MPlayer, in part because I support a guide on these forums for building it
I like **mplayer** too, because it's just very good. It could even play movies on my GP2x. But I really need a GUI.

> **SeijiSensei said:**
> What's wrong with **smplayer**?  Seems pretty nice to me. It's the only player I use.

Initially **SMplayer** looks kinda ugly, I wouldn't want the queen to see that I am using it. But I will give it another shot. I also use SMplayer on my phone (Maemo5/gtk) but it looks completely different on there.

On my Windows machine I use [MPC-HC]("http://mpc-hc.sourceforge.net/"). It looks completely simple, but it has the most features ever. I like that.

---

### Post by Redsandro on 2011-04-10
Also, I haven't really looked into it, but SMplayer seems to be developed by one person and last commit is over a year ago. I like my software to be in active development by multiple people.

Was Andrew talking about SMplayer?
> **andrew.46 said:**
> MPlayer actually does have a gtk gui but most do not build it as it has not been developed for some time and has many problems.

[SIZE="1"]-edit-

Sorry I accidentally replied in stead of edit![/SIZE]

---

