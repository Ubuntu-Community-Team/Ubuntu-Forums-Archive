---
title: "Poor performance in VLC and MPlayer"
date: 2010-07-26
forum: Multimedia Software
---

### Post by Boopop on 2010-07-26
Hi all, 

Just reinstalled Ubuntu after a hiatus of a few years on an account of a lack of X-Fi drivers (thanks creative). Anyway, all was going along fine until today I noticed that both VLC and MPlayer don't like it when I go full screen. 

When VLC freezes, and while the audio continues to play, the image that was on VLC when it froze goes full screen. A few seconds later the video sorts itself out.

With MPlayer, it goes to full screen, and then the video plays at about 10fps or something for a good 5 seconds, and then it sorts itself out.

This is very strange behaviour and I'd really like it fixed, any help would be much appreciated!

---

### Post by VH-BIL on 2010-07-26
Do you have the right video drivers installed.

---

### Post by Boopop on 2010-07-26
I'm using a HD4870, and I've got the Catalyst drivers installed as suggested by Ubuntu itself.

---

### Post by VH-BIL on 2010-07-26
Have you tried with and without compiz running.

---

### Post by Boopop on 2010-07-26
Nope, how do I disable Compiz? And if it is that, does that mean I can't run video players properly without Compiz running, or is there a fix?

---

### Post by VH-BIL on 2010-07-26
We have to find the problem first. you can download the fusion-icon from synaptic which allows you to turn off compiz. When you run it, it will put a icon in the system area. right click it then, select window manager, then click metacity.

---

### Post by VH-BIL on 2010-07-26
you can also try different video renderer's in mplayer by typing ```
mplayer -vo <renderer> <video file>
```

You can get a list of renderer's by typing
```
mplayer -vo help
```

Which on my computer returns:
```
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
Available video output drivers:
	xmga	Matrox G200/G4x0/G550 overlay in X11 window (using /dev/mga_vid)
	mga	Matrox G200/G4x0/G550 overlay (/dev/mga_vid)
	tdfxfb	3Dfx Banshee/Voodoo3/Voodoo5
	3dfx	3dfx (/dev/3dfx)
	xv	X11/Xv
	vdpau	VDPAU with X11
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
	directfb	Direct Framebuffer Device
	dfbmga	DirectFB / Matrox G200/G400/G450/G550
	xvidix	X11 (VIDIX)
	cvidix	console VIDIX
	null	Null video output
	xvmc	XVideo Motion Compensation
	mpegpes	MPEG-PES to DVB card
	yuv4mpeg	yuv4mpeg output for mjpegtools
	png	PNG file
	jpeg	JPEG file
	gif89a	animated GIF output
	tga	Targa output
	pnm	PPM/PGM/PGMYUV file
	md5sum	md5sum of each frame

```
try sdl, gl, gl2, xv, x11,

---

### Post by Boopop on 2010-07-26
> **VH-BIL said:**
> We have to find the problem first. you can download the fusion-icon from synaptic which allows you to turn off compiz. When you run it, it will put a icon in the system area. right click it then, select window manager, then click metacity.

Yep, that seems to be it, thanks. Now what? Is there something I can do to get Compiz to play nicely with VLC?

---

### Post by VH-BIL on 2010-07-26
I did some searching for you but it does not look good. I will not buy an ATI video card. Here is a quote from another thread in Ubuntu forums I found while I was searching for you:
> **VeN0mizer said:**
> You can blame ATI for the really @$&*(@#$& driver quality. They only fix about one to two minor bugs a month with their drivers. Sometimes I swear they have their company janitors working on them. My desktop has an nvidia card and it runs FLAWLESSLY. I can run WoW with compiz with no hitches whatsoever. However, with my laptop, I too get flickering and odd effects. If I could rip this POS video controller off of my laptops motherboard and replace it, I'd do it in a heartbeat....keep looking for driver updates from ATI man, it's all the advice I can give you atm :/

I suggest trying different video output renderer's in mplayer while using comppiz. You can do it in the GUI version if you dont like the command line. try sdl, gl, gl2, xv and x11.

Let me know how you go. I am going to crash now it is 4:30am here. I will check this when I wake up.

---

### Post by tzily on 2010-07-26
What type of video are you playing? it can't be that screwed if it's xvid... Must be a conflict or something.
I'm only into hd files, and on the huge bitrate ones, the last VLC + the SDL output(manual installed in synaptic), i've managed to get the best performance.

---

### Post by VH-BIL on 2010-07-26
> **tzily said:**
> What type of video are you playing? it can't be that screwed if it's xvid... Must be a conflict or something.
I'm only into hd files, and on the huge bitrate ones, the last VLC + the SDL output(manual installed in synaptic), i've managed to get the best performance.

If you have an ATI card can you explain to Boopop how you got this performance in Compiz?

---

### Post by Boopop on 2010-07-26
Thanks for the help VH-BIL, I've tried using different renderers on VLC, and the SDL output you suggested tzily, SDL output turned out to work even worse =/

Any other ideas?

---

### Post by VH-BIL on 2010-07-26
I can just suggest you try them in mplayer. if tzily can not help you or no one else in this thread. Create a new thread now you know the problem such as Poor performance in video with ATI and Compiz or something...

I am using nVidia.

---

### Post by tzily on 2010-07-26
Oh, I'm on nvidia myself and i've disabled compiz since day 1. sorry

---

