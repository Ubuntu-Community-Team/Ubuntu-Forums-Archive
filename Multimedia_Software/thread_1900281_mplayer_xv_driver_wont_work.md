---
title: "mplayer xv driver wont work"
date: 2011-12-25
forum: Multimedia Software
---

### Post by vaah on 2011-12-25
Hi,

I wanted to watch video with mplayer on my ubuntu 10.04.3, but i got error saying 
```
  p, li { white-space: pre-wrap; }  [VO_XV] It seems there is no Xvideo support for your video card available.
 [VO_XV] Run 'xvinfo' to verify its Xv support and read
 [VO_XV] DOCS/HTML/en/video.html#xv!
 [VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
 [VO_XV] Try -vo x11.
 Error opening/initializing the selected video_out (-vo) device.

```

I've just upgraded my rig to i5 2500k with gigabyte ga-z68ma-d2h. I use onboard vga, i'm not sure what the intel series. This didnt happen on my old pc though I had radeon as vga. Do you think there's a relation to this? I can try put my old radeon graphic card, but then again it defeat the purpose of having onboard as I don't play game.

Please help me solve this problem guys.

---

### Post by andrew.46 on 2011-12-26
Perhaps try x11 as the error message has suggested:

```

[VO_XV] **[COLOR="Red"]Try -vo x11[/COLOR]**.

```

and test your copy of MPlayer as the message suggests to see what other video outputs are available to you.

---

### Post by Lampi on 2011-12-26
ga-z68ma-d2h ... turns out to be a sandy bridge board (intel Z68 chipset)

With a lucid kernel (2.6.32) you're out of luck, Sir - you need a kernel upgrade > 2.6.39

---

### Post by vaah on 2011-12-26
WOw it works after following your suggestion using x11, but it says "x11(Slow)". Should i be concerned with the word slow??
Thanks anyway I didn't know why it didn't cross my mind, maybe because XV always worked on my previous ubuntu until i upgraded my cpu and motherboard yesterday. Btw, I compiled the mplayer from source.

---

### Post by andrew.46 on 2011-12-26
> **vaah said:**
> WOw it works after following your suggestion using x11, but it says "x11(Slow)". Should i be concerned with the word slow??
Thanks anyway I didn't know why it didn't cross my mind, maybe because XV always worked on my previous ubuntu until i upgraded my cpu and motherboard yesterday. Btw, I compiled the mplayer from source.

It is not the fastest vo in the world but sounds like it works :). If you recompile make sure you have all the required development libraries in place, there is a guide for this somewhere on these forums I believe, and then see if xv then pops up under this list:

```

andrew@skamandros~$**[COLOR="Red"] mplayer -vo help[/COLOR]**
MPlayer SVN-r34440-4.6.2 (C) 2000-2011 MPlayer Team
Available video output drivers:
	**[COLOR="Red"]xv	X11/Xv[/COLOR]**
	gl_nosw	OpenGL no software rendering
	x11	X11 ( XImage/Shm )
	xover	General X11 driver for overlay capable video output drivers
	sdl	SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
	gl	OpenGL
	gl2	X11 (OpenGL) - multiple textures version
	dga	DGA ( Direct Graphic Access V2.0 )
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
	mng	MNG file

andrew@skamandros~$ 

```

---

### Post by vaah on 2011-12-26
> **Lampi said:**
> ga-z68ma-d2h ... turns out to be a sandy bridge board (intel Z68 chipset)

With a lucid kernel (2.6.32) you're out of luck, Sir - you need a kernel upgrade > 2.6.39
if I have to go to kernel 2.6.39 doesn't that mean i have to upgrade to ubuntu 11.10? or is there any other solution? I hate the unity thing thats why I dont wanna upgrade.

---

### Post by vaah on 2011-12-26
> **andrew.46 said:**
> It is not the fastest vo in the world but sounds like it works :). If you recompile make sure you have all the required development libraries in place, there is a guide for this somewhere on these forums I believe, and then see if xv then pops up under this list:
```
andrew@skamandros~$**[COLOR=Red] mplayer -vo help[/COLOR]**
MPlayer SVN-r34440-4.6.2 (C) 2000-2011 MPlayer Team
Available video output drivers:
    **[COLOR=Red]xv    X11/Xv[/COLOR]**
    gl_nosw    OpenGL no software rendering
    x11    X11 ( XImage/Shm )
    xover    General X11 driver for overlay capable video output drivers
    sdl    SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
    gl    OpenGL
    gl2    X11 (OpenGL) - multiple textures version
    dga    DGA ( Direct Graphic Access V2.0 )
    fbdev    Framebuffer Device
    fbdev2    Framebuffer Device
    svga    SVGAlib
    matrixview    MatrixView (OpenGL)
    aa    AAlib
    caca    libcaca
    v4l2    V4L2 MPEG Video Decoder Output
    xvidix    X11 (VIDIX)
    cvidix    console VIDIX
    null    Null video output
    mpegpes    MPEG-PES to DVB card
    yuv4mpeg    yuv4mpeg output for mjpegtools
    png    PNG file
    jpeg    JPEG file
    gif89a    animated GIF output
    tga    Targa output
    pnm    PPM/PGM/PGMYUV file
    md5sum    md5sum of each frame
    mng    MNG file

andrew@skamandros~$ 

```
currently is listed as available:
```

augie@yuki:~/r8168-8.026.00
$ mplayer -vo help
MPlayer SVN-r34466-4.4.3 (C) 2000-2011 MPlayer Team
Available video output drivers:
    xv    X11/Xv
    gl_nosw    OpenGL no software rendering
    x11    X11 ( XImage/Shm )
    xover    General X11 driver for overlay capable video output drivers
    gl    OpenGL
    gl2    X11 (OpenGL) - multiple textures version
    fbdev    Framebuffer Device
    fbdev2    Framebuffer Device
    matrixview    MatrixView (OpenGL)
    v4l2    V4L2 MPEG Video Decoder Output
    xvidix    X11 (VIDIX)
    cvidix    console VIDIX
    null    Null video output
    mpegpes    MPEG-PES to DVB card
    yuv4mpeg    yuv4mpeg output for mjpegtools
    png    PNG file
    tga    Targa output
    pnm    PPM/PGM/PGMYUV file
    md5sum    md5sum of each frame

```

I noticed your mplayer is newer than mine? Where did you get that? Thanks.

---

### Post by andrew.46 on 2011-12-26
> **vaah said:**
> I noticed your mplayer is newer than mine? Where did you get that? Thanks.

I compile every couple of days from svn, but are you looking at the gcc version?

---

### Post by Lampi on 2011-12-26
@vaah: can you post the output of "xvinfo -short" ? Are you getting an adapter or "No adaptors present"?

I assume you'll get none with the Lucid kernel, it won't change with a new mplayer then.

---

### Post by vaah on 2011-12-26
> **Lampi said:**
> @vaah: can you post the output of "xvinfo -short" ? Are you getting an adapter or "No adaptors present"?

I assume you'll get none with the Lucid kernel, it won't change with a new mplayer then.
yes sir, seems like i got no adaptor present... so my only choice to properly fix this to upgrade to kernel 2.6.39 I guess?
is there anyway to do that without going to 11.10? I currently use 10.04 and i just installed this one yesterday too. :(
```

$ xvinfo -short
X-Video Extension version 2.2
screen #0
 no adaptors present

```

---

### Post by vaah on 2011-12-26
> **andrew.46 said:**
> I compile every couple of days from svn, but are you looking at the gcc version?
alright so the 4.6.2 is the gcc version yeah? LOL i didn't know. so Mine mplayer is newer because i just compiled mine this morning.

---

### Post by andrew.46 on 2011-12-26
> **vaah said:**
> alright so the 4.6.2 is the gcc version yeah? LOL i didn't know. so Mine mplayer is newer because i just compiled mine this morning.

Indeed :). BTW good to see a fellow Australian and MPlayer enthusiast on the Forums!

---

### Post by Lampi on 2011-12-26
possibly, you can still try to understand why it's failing with the Lucid kernel - some Xorg.0.log errors might come in handy:
```
egrep "(EE)|(WW)" /var/log/Xorg.0.log
```

---

### Post by vaah on 2011-12-26
> **andrew.46 said:**
> Indeed :). BTW good to see a fellow Australian and MPlayer enthusiast on the Forums!
thanks for your help buddy at least I can watch movie until i have time to upgrade if i'm left with no other choice.

---

### Post by vaah on 2011-12-26
> **Lampi said:**
> possibly, you can still try to understand why it's failing with the Lucid kernel - some Xorg.0.log errors might come in handy:
```
egrep "(EE)|(WW)" /var/log/Xorg.0.log
```
Hi Lampi, this is the output you want.
```
$ egrep "(EE)|(WW)" /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
(WW) Falling back to old probe method for fbdev
(WW) VESA(0): Unable to estimate virtual size

```

if you don't mind me asking, i also have problem with the sound setting. I can't have the motherboard to produce 5.1 output sound. The only working channel is the front channel. not the rear or centre speaker. is this related to sandy bridge problem? i had no problem with my previous P35 conroe rig. Now it seems ubuntu doesn't work out of the box now. I have to tweak with the ssd thing too.

---

### Post by Lampi on 2011-12-26
5.1 used to be difficult, but it shouldn't be anymore:

go to sound preferences, click the device to configure,then select a surround sound profile from the drop down box.

can you attach /var/log/Xorg.0.log or post it at pastebin? I didn't see the results I expected wth the egrep line.

Worst case you can still go back and plug-in the radeon card, those are nicely supported.

---

### Post by vaah on 2011-12-26
> **Lampi said:**
> 5.1 used to be difficult, but it shouldn't be anymore:

go to sound preferences, click the device to configure,then select a surround sound profile from the drop down box.

can you attach /var/log/Xorg.0.log or post it at pastebin? I didn't see the results I expected wth the egrep line.

Worst case you can still go back and plug-in the radeon card, those are nicely supported.
@Lampi: Yeah I already did that and no luck, is there like special sound driver for this?

I already put the output of xorg at [http://pastebin.com/MVkk4hSK](http://pastebin.com/MVkk4hSK)

Yeah worst case, i'll just put back my hd2400 radeon card, it's old but does the job.

---

### Post by Lampi on 2011-12-26
Maybe some mixer setting is still muted?

Thanks for the pastebin post, you can see from line 117-121 your xorg intel driver lacks sandy bridge support.

Support was released with kernel 2.6.37, but it's still ongoing work. So I assume you're a lot easier of with the radeon card.

---

### Post by vaah on 2011-12-26
> **Lampi said:**
> Maybe some mixer setting is still muted?

Thanks for the pastebin post, you can see from line 117-121 your xorg intel driver lacks sandy bridge support.

Support was released with kernel 2.6.37, but it's still ongoing work. So I assume you're a lot easier of with the radeon card.
@Lampi: Yeah I'm better off with discrete graphic card at the moment, though x11 works instead of xv. so no worries.
Now what's left is the sound problem. I have similar problem with this guy. [http://askubuntu.com/questions/54265/how-to-configure-5-1-surround-sound-through-three-3-5-mm-jacks](http://askubuntu.com/questions/54265/how-to-configure-5-1-surround-sound-through-three-3-5-mm-jacks)

I made a new thread, maybe you can help me out? [http://ubuntuforums.org/showthread.php?p=11565693#post11565693](http://ubuntuforums.org/showthread.php?p=11565693#post11565693)

---

