---
title: "mplayer with VDPAU on Mythbuntu 10.04"
date: 2010-06-22
forum: Mythbuntu
---

### Post by Slate8 on 2010-06-22
I feel like a bit of a dummy but I am new to all this VDPAU stuff and can't figure out how to get mplayer to playback using VDPAU rather than putting the load on my CPU.

I have Mythbuntu 10.04 installed and the Internal player uses VDPAU to play 1080p movies without issue. I have searched a bit and tried a few different mplayer switches but can't seem to get it to behave.

Can any one tell me how they get mplayer to decode via VDPAU on their setup? Do I still need to compile mplayer to work with VDPAU on 10.04?

Any pointers greatly appreciated.

---

### Post by ian dobson on 2010-06-22
Hi,

Try something like this:-

mplayer  -vo vdpau 

mplayer in 10.04 is compiled with vdpau support.


regards
Ian Dobson

---

### Post by Slate8 on 2010-06-23
Thanks for the info. I tried that before but had another go last night after seeing your reply but still no luck I'm afraid. My 1080p mkv which plays smoothly via the internal player was jumpy and maxing out the CPU.

Really not sure what I am doing wrong - any other suggestions? :(

---

### Post by ian dobson on 2010-06-23
Hi,

what you you seen in the /var/log/myth/mythfrontend.log when you try playing a video through mplayer.

also try from the terminal prompt:-
mplayer -vo help
you should see something like
mplayer -vo help
```
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
Available video output drivers:
        xmga    Matrox G200/G4x0/G550 overlay in X11 window (using /dev/mga_vid)
        mga     Matrox G200/G4x0/G550 overlay (/dev/mga_vid)
        tdfxfb  3Dfx Banshee/Voodoo3/Voodoo5
        3dfx    3dfx (/dev/3dfx)
        xv      X11/Xv
        vdpau   VDPAU with X11
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        gl      X11 (OpenGL)
        gl2     X11 (OpenGL) - multiple textures version
        dga     DGA ( Direct Graphic Access V2.0 )
        sdl     SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        svga    SVGAlib
        aa      AAlib
        caca    libcaca
        v4l2    V4L2 MPEG Video Decoder Output
        directfb        Direct Framebuffer Device
        dfbmga  DirectFB / Matrox G200/G400/G450/G550
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        xvmc    XVideo Motion Compensation
        mpegpes MPEG-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        jpeg    JPEG file
        gif89a  animated GIF output
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame
```

Regards
Ian Dobson

---

### Post by newlinux on 2010-06-23
> **Slate8 said:**
> Thanks for the info. I tried that before but had another go last night after seeing your reply but still no luck I'm afraid. My 1080p mkv which plays smoothly via the internal player was jumpy and maxing out the CPU.

Really not sure what I am doing wrong - any other suggestions? :(

for mkv (assuming it's x264) try:

```

mplayer -vo vdpau -vc ffh264vdpau
```

---

### Post by Slate8 on 2010-07-09
Thanks for all the suggestions - I finally had a chance to try all the above.

"mplayer -vo vdpau -vc ffh264vdpau" did work for me; mplayer only uses ~20% CPU when playing a 1080p movie. However, on the higher bitrate films the framerate is a little choppy in places and the audio goes out of sync. (sad face)

The internal player doesn't seem to have these problems so I'm not really sure what to try next.

I was hoping to use mplayer for it's superior embedded subtitle support and volume normalization but just can't seem to get it to play files well using VDPAU.

Any other suggestions welcome because I'm not sure where the issue could be.

Here is my output of mplayer -vo help
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

---

