---
title: "[hardy] Some WMV Files Don't Play"
date: 2009-02-18
forum: Multimedia Software
---

### Post by Izek on 2009-02-18
Some WMV Files I have won't play, and when I right-click and go to properties on these files, a message pops up saying "Creating Properties Window." Is there any way to fix this? Or will I have to go back to windows?

mplayer plays the audio for these files, but won't play the video, totem doesn't play anything.

I have w64codecs, etc. all needed to play these things. I can't give the file as I'm not allowed to distribute it.

---

### Post by jerome1232 on 2009-02-18
I'm willing to bet the ones that aren't playing have wmav3 encoded audio in them. mplayer should be able to play them, and if you want mencoder can convert the audio to wmav2 so they will be playable in you favorite media player.

Here's a recent thread I was in that shows how to use mencoder to convert the files if you like.

[http://ubuntuforums.org/showthread.php?t=1061594](http://ubuntuforums.org/showthread.php?t=1061594)

--edit-- for some reason I didn't see that you said mplayer won't play the video, that's strange, I'm not sure what to do in that case.

---

### Post by Izek on 2009-02-18
This file isn't the reason why mplayer won't play the video. mplayer gives the error "error opening/initializing the selected video_out (-vo) device." It does this for all files.

---

### Post by andrew.46 on 2009-02-20
Hi Izek,

> **Izek said:**
> This file isn't the reason why mplayer won't play the video. mplayer gives the error "error opening/initializing the selected video_out (-vo) device." It does this for all files.

Good news: this error is addressed in the MPlayer FAQs:

[http://www.mplayerhq.hu/DOCS/HTML/en/faq.html#id2612932](http://www.mplayerhq.hu/DOCS/HTML/en/faq.html#id2612932)

All the best,

Andrew

---

### Post by Izek on 2009-02-20
And what should I put in place of selected_vo?

---

### Post by andrew.46 on 2009-02-20
Hi Izek,

> **Izek said:**
> And what should I put in place of selected_vo?

Well to use my own system as an example the selections could be:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vo help[/COLOR]**
MPlayer SVN-r28672-4.2.4 (C) 2000-2009 MPlayer Team
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

So I could try:

```
$ mplayer -vo xv myfile.avi
```

where 'myfile.avi' would need to be changed to reflect the name of your own file. If this produced a decent video on my screen I would add 

```
vo = xv
```

to the file ~/.mplayer/config. This should get you out of trouble hopefully.

Andrew

---

