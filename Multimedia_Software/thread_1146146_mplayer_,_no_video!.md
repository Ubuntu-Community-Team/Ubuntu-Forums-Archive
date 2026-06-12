---
title: "mplayer , no video!"
date: 2009-05-02
forum: Multimedia Software
---

### Post by Xpire on 2009-05-02
Hi guys, 

I'm a newbie to this whole Ubuntu and terminal thing so go easy on me :D
Just installed mplayer and tried running a couple of my video files to find that there isn't any video output :(

This is what happens when i run mplayer:
> 
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  994.7 kbps (121.4 kbyte/s)
Clip info:
 Software: transcode-1.0.2
Can't open /dev/fb0: No such file or directory
[fbdev2] Can't open /dev/fb0: No such file or directory
VO: [v4l2] No such file or directory
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
[cyberblade] Error occurred during pci scan: Operation not permitted
[mach64] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[nvidia_vid] Error occurred during pci scan: Operation not permitted
[pm3] Error occurred during pci scan: Operation not permitted
[radeon] Error occurred during pci scan: Operation not permitted
[rage128] Error occurred during pci scan: Operation not permitted
[s3_vid] Error occurred during pci scan: Operation not permitted
[SiS] Error occurred during pci scan: Operation not permitted
[unichrome] Error occurred during pci scan: Operation not permitted
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [null] 624x352 => 624x352 Planar YV12 
A:  21.5 V:  21.5 A-V: -0.000 ct:  0.000 516/516 10%  0%  2.1% 0 0                                                 

I've got all the codecs in ~/usr/local/lib/codecs , but i'm not sure if thats the problem or not... 
Could it be something to do with X? 

Thanks in advance!

---

### Post by Xpire on 2009-05-02
It's only been 12 hours and my threads on page 5 :(

Anyone ???

---

### Post by xc3RnbFO8P on 2009-05-03
Try **sudo mplayer**....

---

### Post by andrew.46 on 2009-05-03
Hi Xpire,

Have you tried:

```
mplayer -vo xv mymovie.avi
```

I am not familiar with 'ubuntu netbook remix' but it looks like MPlayer is failing on the video out so you would usually try a different one like 'xv' or 'x11'.

Andrew

---

### Post by Xpire on 2009-05-03
Thanks for replying!

Yeah I've tried that already.

Here's what happens with 'x11'
> AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  994.7 kbps (121.4 kbyte/s)
Clip info:
 Software: transcode-1.0.2
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   1.9 (01.9) of 22819.5 ( 6:20:19.4)  1.8%  

And 'xv'..
> AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  994.7 kbps (121.4 kbyte/s)
Clip info:
 Software: transcode-1.0.2
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   2.0 (02.0) of 22819.5 ( 6:20:19.4)  2.0%                                                                                


Any other ideas?

---

### Post by andrew.46 on 2009-05-03
Hi Xpire,

> **Xpire said:**
> Any other ideas?

Well I suspect it will all come down to my total lack of knowledge of how MPlayer is packaged for the netbook remix :-). To see what -vo devices *are* available to you run:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vo help[/COLOR]**
MPlayer SVN-r29242-4.2.4 (C) 2000-2009 MPlayer Team
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

and then try these in turn, except of course for such wild ones as caca, aa, jpeg and the like :-).

Andrew

---

### Post by Xpire on 2009-05-07
:( Nope, I tried all of them and none of them worked...
Have i simply not installed it correctly? It could be one of the components that would have been required to be pre-installed prior to the installation of mplayer...

---

### Post by andrew.46 on 2009-05-07
Hi Xpire,

Certainly something is broken but my complete lack of knowledge concerning this branch of Ubuntu (netbook remix) really means I cannot really guess at what it might be.  There must be a few MPLayer users here with the netbook remix?

Andrew

---

### Post by stefangr1 on 2009-05-07
Maybe you can try to remove MPlayer, install some X11 development packages (xorg-dev), than reinstall MPlayer, and see if that helps.

What you could also do, though it can be a little time consuming, is compile mplayer-svn from source.

---

