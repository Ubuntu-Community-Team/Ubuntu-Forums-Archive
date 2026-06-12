---
title: "Nvidia Driver"
date: 2010-04-06
forum: Multimedia Software
---

### Post by ewe on 2010-04-06
I think I'm having a problem with my video driver. How do I check it? My card is nvidia GeForce9500 gt.

---

### Post by tommcd on 2010-04-06
First, did you enable the nvidia driver for your card. Here is the easy way to do it:
Go to: system > administration > hardware drivers, and see if it offers to install and enable the nvidia driver for you. It should detect your video card and offer to install the driver. Then reboot after it finishes installing the driver (just to be sure) and see if you got 3D enabled. To check if 3D is enabled, open a terminal (applications > accessories > terminal) and run:
```
glxinfo | grep -i direct
```
It should report: [B]direct rendering: Yes
[/B]

---

### Post by ewe on 2010-04-06
> **tommcd said:**
> First, did you enable the nvidia driver for your card. Here is the easy way to do it:
Go to: system > administration > hardware drivers, and see if it offers to install and enable the nvidia driver for you. It should detect your video card and offer to install the driver. Then reboot after it finishes installing the driver (just to be sure) and see if you got 3D enabled. To check if 3D is enabled, open a terminal (applications > accessories > terminal) and run:
```
glxinfo | grep -i direct
```
It should report: [B]direct rendering: Yes
[/B]yes, I have direct rendering. My problem is I cannot get mplayer to give a proper full-screen rendering for certain streams.

---

### Post by tommcd on 2010-04-06
> **ewe said:**
>  My problem is I cannot get mplayer to give a proper full-screen rendering for certain streams.
What exactly do you mean with "proper full screen rendering"? What is improper about it? Can you provide a link to these streams?
Please be as specific as possible when describing your problem(s). Your first post sounded like you were asking how to install the nvidia driver.
Also, in MPlayer's preferences, under the video tab, which driver are you using? I have a nvidia 8600GT graphics card. I am currently using **gl2 X11(Open GL)** on Slackware 13, and everything looks good to me. Try the different options listed there on the video driver tab in MPlayer and see if you get better results. You can always change it back to whatever it was originally if things do not improve.
Also, try running MPlayer from the terminal and see what the output in the terminal says. There may be some clues in the terminal output for MPlayer that may indicate what is wrong. To play a stream from a website from the terminal with MPlayer just run:
```
mplayer http://url_of_your_stream
```

---

### Post by ewe on 2010-04-06
heres my output from mplayer -vo help.> MPlayer SVN-r31016-4.4.1 (C) 2000-2010 MPlayer Team
Available video output drivers:
x11	X11 ( XImage/Shm )
xover	General X11 driver for overlay capable video output drivers
fbdev	Framebuffer Device
fbdev2	Framebuffer Device
v4l2	V4L2 MPEG Video Decoder Output
directfb	Direct Framebuffer Device
dfbmga	DirectFB / Matrox G200/G400/G450/G550
xvidix	X11 (VIDIX)
cvidix	console VIDIX
null	Null video output
mpegpes	MPEG-PES to DVB card
yuv4mpeg	yuv4mpeg output for mjpegtools
png	PNG file
jpeg	JPEG file
tga	Targa output
pnm	PPM/PGM/PGMYUV file
md5sum	md5sum of each frame I was getting a scrunched picture and am thinking it could be my video card or driver. I see that this version of mplayer is 64bit and I have Ubuntu 9.10 (32bit) installed. Could that be a problem?

sorry for the confusion, but I'm tryng to figure out what my problem might be.

Thanks for the help!

---

### Post by tommcd on 2010-04-07
> **ewe said:**
> heres my output from mplayer -vo help.
Here is my output from "mplayer -vo help" on Slackware with the nvidia 190.42 driver:
```

bash-3.1$ mplayer -vo help
MPlayer r29390-4.3.3 (C) 2000-2009 MPlayer Team
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
I get essentially the same output on my laptop running Ubuntu 9.10, and my laptop uses an intel 945GM graphics. You seem to missing the "gl2" and "gl2" drivers for some reason.
On Slackware I am using "gl2 X11(Open GL)" in MPlayer. On my laptop with Ubuntu and the intel graphics I am using "xv X11/Xv". They both look fine to me. 
So which video driver are you using in MPlayer? Have you tried different drivers in MPlayer?
> **ewe said:**
> 
I was getting a scrunched picture and am thinking it could be my video card or driver.
Can you post a screenshot of this? If by "scrunched picture" you mean that the picture is small, you can stretch the picture to fill the screen if you want to.
> **ewe said:**
> 
 I see that this version of mplayer is 64bit and I have Ubuntu 9.10 (32bit) installed. Could that be a problem?

Where did you get the version of MPlayer you are using? Is it the standard MPlayer from the Ubuntu 9.10 32bit repos? Ord o you have some ppa repo for MPlayer in your sources.list or something?
You would not be able to install 64bit MPlayer on 32bit Ubuntu. The 64bit Ubuntu can install 32bit compatibility libraries to use 32bit packages on 64bit Ubuntu, but it does not work the other way. That is, you can't install 64bit software on a 32bit OS.

---

