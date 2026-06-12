---
title: "WMV win32 issues"
date: 2010-05-19
forum: Multimedia Software
---

### Post by RyanfromtheShire on 2010-05-19
So I've done a fair amount of research on this, because it's a common challenge, but I am still having issues. I have the latest w32codecs installed, and I'm using mplayer, but I only get sound and no video. Usually it's people having issues with sound. When I open it with VLC, I get a picture but no sound.

This is the error message I get when opening the file:

[http://img38.imageshack.us/img38/1473/screenshotsd.png](http://img38.imageshack.us/img38/1473/screenshotsd.png)

Anyone know what I'm doing wrong here?

Thanks,
Ryan

---

### Post by mc4man on 2010-05-19
> Anyone know what I'm doing wrong here?
Not much  - try a specfic -vo. ( and one should mention what ubuntu release they're using...

It appears you're using 'gmplayer' - there should be a couple of choices in the preferences menu, try some. (xv, x11, gl, ect.

Or run mplayer from cli - 
mplayer -vo <insert one> /path/to/filename

running this should show available though some shouldn't be used

```
mplayer -vo help
```

Ex. here (blue are 'reasonable' tries
> 
doug@doug-desktop:~$ mplayer -vo help
MPlayer git-faea4ef-4.4.3 (C) 2000-2010 MPlayer Team
Available video output drivers:
	[COLOR="Blue"]xv[/COLOR]	X11/Xv
	[COLOR="Blue"]gl_nosw[/COLOR]	OpenGL no software rendering
	[COLOR="Blue"]x11[/COLOR]	X11 ( XImage/Shm )
	xover	General X11 driver for overlay capable video output drivers
	[COLOR="Blue"]gl[/COLOR]	OpenGL
	[COLOR="Blue"]gl2[/COLOR]	X11 (OpenGL) - multiple textures version
	dga	DGA ( Direct Graphic Access V2.0 )
	[COLOR="Blue"]sdl[/COLOR]	SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
	ggi	General Graphics Interface (GGI) output
	fbdev	Framebuffer Device
	fbdev2	Framebuffer Device
	svga	SVGAlib
	matrixview	MatrixView (OpenGL)
	aa	AAlib
	caca	libcaca
	v4l2	V4L2 MPEG Video Decoder Output
	dfbmga	DirectFB / Matrox G200/G400/G450/G550
	xvidix	X11 (VIDIX)
	cvidix	console VIDIX
	null	Null video output
	directfb	Direct Framebuffer Device
	mpegpes	MPEG-PES to DVB card
	yuv4mpeg	yuv4mpeg output for mjpegtools
	png	PNG file
	jpeg	JPEG file
	gif89a	animated GIF output
	tga	Targa output
	pnm	PPM/PGM/PGMYUV file

vlc should do wma2 audio ok - for wma3(pro) or wmal audio you'd need to build it yourself


You may wish to find a ppa for a more recent mplayer and pair it up with a frontend - smplayer or gnome-mplayer for example.

---

### Post by RyanfromtheShire on 2010-05-20
Oh ok, I set it to gl and it's working now. I knew it had to be a quick fix like that. Thanks for the help!

---

