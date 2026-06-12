---
title: "Mplayer can't play videos"
date: 2009-06-06
forum: Multimedia Software
---

### Post by Aeren on 2009-06-06
I have quite a big problem with mplayer. Whenever I launch a video (no matter which extension), it shows me the following error message :
```
Error opening/initializing the selected video_out (-vo) device.

```
I have checked that it is using the Xv codecs and not the Matrox one, so it rules out one source of the bug. The other one i've read about is if another program is using the Xv codec, but I don't have any way of checking it. I'm supposing it's not that bug either since I tried to use mplayer right after a restart!

I honestly don't know what might be the cause of this. If anyone can help...

---

### Post by malimrav on 2009-06-06
First Remove MPlayer through synaptic pakage manager (mark to complete removal)
Then install the proper codecs like:
sudo apt-get install medibuntu-keyring

sudo apt-get update

sudo apt-get install w64codecs libdvdcss2 (IF YOUR SYSTEM IS X86 THEN INSTEAD OF w64codecs, w32codecs)

sudo apt-get install ubuntu-restricted-extras

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

sudo apt-get install mencoder

sudo apt-get instlall vlc mplayer

so it should work now.

---

### Post by andrew.46 on 2009-06-06
Hi Aeren,

> **Aeren said:**
> 
```
Error opening/initializing the selected video_out (-vo) device.

```


You may very well have no further problem with MPlayer after following malimrav's advice, although I am not so sure that gstreamer plugins will help MPlayer. BTW don't forget to ad the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu") to your sources.list first. If you have trouble still have a look at the -vo options you have in this manner:

```

andrew@skamandros~$ **[COLOR="Purple"]mplayer -vo help[/COLOR]**
MPlayer SVN-r29350-4.2.4 (C) 2000-2009 MPlayer Team
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

and experiment a little with the various outputs, xv and x11 being the usual safest options, and avoiding the looney-tunes ones like caca, aa and the rest :-).

These can be selected on the commandline as follows:

```
mplayer -vo x11 *myfile.avi*
```

All the best,

Andrew

---

### Post by Aeren on 2009-06-07
Well, in the end I didn't even have to do anything. I still don't understand what happened, but now it just works fine. Maybe while installing other programs one of the plugins indirectly resolved the problem...
Btw, the Medibuntu repository was already added. Thanks anyway for your replies, it might be useful for others.

---

