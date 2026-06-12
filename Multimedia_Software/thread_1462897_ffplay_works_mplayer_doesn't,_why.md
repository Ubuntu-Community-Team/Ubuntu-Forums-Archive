---
title: "ffplay works mplayer doesn't, why?"
date: 2010-04-26
forum: Multimedia Software
---

### Post by Reza Rob on 2010-04-26
I have Hardy with latest updates.  ffplay works flawlessly on youtube flv and also an mp3 music file.  Both mplayer and moviePlayer are broken and have the same problem:  frozen, dead, picture.  Why is that?

----------------------------------------------
:~$ ffplay -stats f.flv 
Input #0, flv, from 'f.flv':=    0KB vq=    0KB sq=    0B    
  Duration: 00:09:41.1, start: 0.000000, bitrate: 64 kb/s
  Stream #0.0: Video: flv, yuv420p, 320x180, 24.00 fps(r)
  Stream #0.1: Audio: mp3, 22050 Hz, mono, 64 kb/s
   8.55 A-V:  0.005 aq=   80KB vq=  313KB sq=    0B    
--------------------------------------------------
:~$ mplayer f.flv 
MPlayer 1.0rc2-4.2.4 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.60GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing f.flv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x180  0bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
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
VDec: vo config request - 320 x 180 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x180 => 320x180 Planar YV12 
A:   0.0 V:   0.2 A-V: -0.202 ct: -0.012   5/  5 ??% ??% ??,?% 0 0 
-----------------------------------------------------

Thanks a lot.

Reza.

---

### Post by andrew.46 on 2010-04-26
Hi Reza Rob,

Have you tried experimenting with different audio and video out devices? For example:

```
mplayer -vo x11 f.flv 
mplayer -ao alsa f.flv 
```

or combinations of these...

All the best,

Andrew

---

### Post by Reza Rob on 2010-04-26
> **andrew.46 said:**
> ```
mplayer -vo x11 f.flv 
mplayer -ao alsa f.flv 
```

or combinations of these...


mplayer -ao alsa file.mp3 
works great.  But mplayer -vo x11 file.flv still fails.

What do you mean "combinations of these?"  What else can I try?  Isn't there a definitive way to tell which options to use?  This is a standard gnome install.  If I can't get it to work, no ordinary end user can make it work either.  Shouldn't it just work out-of-the-box?

I really want to learn _why_ this doesn't work automatically, and what the issues are?

Thanks a lot for responding.

Reza.

---

### Post by andrew.46 on 2010-04-26
Hi Reza Rob,

Well, usually the problem in such cases is that MPlayer is using a video or audio out device that for some reason is not working on your system. As a troubleshooting method you can manually try a few different video or audio out devices until you have found a working combination and then make these the new defaults for your system. This way you do not have to type them in all the time :).

Video out devices available to your copy of MPlayer can be seen as follows:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vo help[/COLOR]**
MPlayer SVN-r31097-4.3.3 (C) 2000-2010 MPlayer Team
Available video output drivers:
	xv	X11/Xv
	gl_nosw	OpenGL no software rendering
	x11	X11 ( XImage/Shm )
	xover	General X11 driver for overlay capable video output drivers
	gl	OpenGL
	gl2	X11 (OpenGL) - multiple textures version
	dga	DGA ( Direct Graphic Access V2.0 )
	sdl	SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
	fbdev	Framebuffer Device
	fbdev2	Framebuffer Device
	svga	SVGAlib
	matrixview	MatrixView (OpenGL)
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

Some of these are quite specialised but the ones you would try would be xv, gl and x11. The same for audio out:

```

andrew@skamandros~$**[COLOR="Red"] mplayer -ao help[/COLOR]**
MPlayer SVN-r31097-4.3.3 (C) 2000-2010 MPlayer Team
Available audio output drivers:
	oss	OSS/ioctl audio output
	alsa	ALSA-0.9.x-1.x audio output
	esd	EsounD audio output
	sdl	SDLlib audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output

```

Here you try oss or alsa, you obviously have pulse as well which is not available on my system. And yes on Ubuntu you would normally expect this to work out of the box but this is obviously not happening in your case, hence the Trial and Error approach :).

Is it possible or you to post this file somewhere? I suspect the file is ok if FFplay can run it but it would be nice to be sure and I will admit that it is a little odd that MPlayer gives no error message... Another note is that Ubuntu managed to break libavcodec briefly over the last few days, now rectified I believe, so perhaps try an update before committing too much time to experimentation with MPlayer.

Andrew

---

### Post by Reza Rob on 2010-04-26
Thanks a lot for your help Andrew.  

> **andrew.46 said:**
> 
Here you try oss or alsa, you obviously have pulse as well which is not available on my system. And yes on Ubuntu you would normally expect this to work out of the box but this is obviously not happening in your case, hence the Trial and Error approach :).


Actually, I just tried the same mplayer -ao alsa on the flv file and it worked!  Wonderful.  

> 
Is it possible or you to post this file somewhere? 


The flv file in question is a youtube-dl downloaded copy of part 6 or so of the Steven Weinberg - Richard Dawkins interview.  Should be easy to find.

FYI,  the system I was using was an old intel mobo D865GBF with this on board device:
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

Regards,
Reza.

---

### Post by andrew.46 on 2010-04-27
Hi Reza,

Excellent news :). You have a few choices now, if you are keen on the commandline MPlayer you can place the following in ~/.mplayer/config:

```
ao=alsa
```

or if you are keen on a gui I would suggest SMPlayer rather than the default GMPlayer:
```

sudo apt-get install smplayer
```

and put alsa as the audio out device:

Options --> Peferences --> General --> Audio --> Output Driver

And hopefully then you are set :).

All the best,

Andrew

---

### Post by Reza Rob on 2010-04-27
> **andrew.46 said:**
> 
Excellent news :). You have a few choices now, if you are keen on the commandline MPlayer you can place the following in ~/.mplayer/config:

[... some great info ...]


Once again Andrew, your help is much appreciated.

Reza.

---

