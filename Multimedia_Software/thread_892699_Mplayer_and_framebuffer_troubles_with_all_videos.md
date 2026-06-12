---
title: "Mplayer and framebuffer troubles with all videos"
date: 2008-08-17
forum: Multimedia Software
---

### Post by chons on 2008-08-17
I have got some problems with watching videos through framebuffer.
There is an example of screen when I try watching one of the film:

[http://librarian.spb.ru/fbscreen.png](http://librarian.spb.ru/fbscreen.png)

There is no trubles with my framebuffer configuration, besause fbi links2 -driver fb works really good, but mplayer -vo fbdev or mplayer -vo fbdev

I have ask about this problem in russian community, but no one can answer.

About configuration: Ubuntu 8.04.1 vga=0x324 in menu.lst

```
Available video output drivers in mplayer:
	xmga	Matrox G200/G4x0/G550 overlay in X11 window (using /dev/mga_vid)
	mga	Matrox G200/G4x0/G550 overlay (/dev/mga_vid)
	tdfxfb	3Dfx Banshee/Voodoo3/Voodoo5
	3dfx	3dfx (/dev/3dfx)
	xv	X11/Xv
	x11	X11 ( XImage/Shm )
	xover	General X11 driver for overlay capable video output drivers
	gl	X11 (OpenGL)
	gl2	X11 (OpenGL) - multiple textures version
	dga	DGA ( Direct Graphic Access V2.0 )
	sdl	SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
	ggi	General Graphics Interface (GGI) output
	fbdev	Framebuffer Device
	fbdev2	Framebuffer Device
	svga	SVGAlib
	aa	AAlib
	caca	libcaca
	dxr3	DXR3/H+ video out
	v4l2	V4L2 MPEG Video Decoder Output
	xvidix	X11 (VIDIX)
	cvidix	console VIDIX
	null	Null video output
	xvmc	XVideo Motion Compensation
	mpegpes	Mpeg-PES to DVB card
	yuv4mpeg	yuv4mpeg output for mjpegtools
	png	PNG file
	jpeg	JPEG file
	gif89a	animated GIF output
	tga	Targa output
	pnm	PPM/PGM/PGMYUV file
	md5sum	md5sum of each frame
```



Any thoughts? I think, that there is some troubles with RGB channels.

---

