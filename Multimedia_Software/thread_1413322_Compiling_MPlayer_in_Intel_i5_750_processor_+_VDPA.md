---
title: "Compiling MPlayer in Intel i5 750 processor + VDPAU?"
date: 2010-02-22
forum: Multimedia Software
---

### Post by Laxman_prodigy on 2010-02-22
Hi guys.

I have downloaded the Nvidia drivers from their site yesterday. Its 190.53....

My card is XFX Geforce 9600GT GDDR3 1GB and the processor is Intel i5 750 accompanied by 4GB DDR3 RAM.

I want to compile MPlayer fully supporting my system and graphics card. I read somewhere that VDPAU support will enhance the playback.

I found many threads but they seem to be quite old now. I use Ubuntu 9.10.

Please guide me as to how should I proceed while fully utilising my system for great playback.:confused:

---

### Post by andrew.46 on 2010-02-23
Hi Laxman,

> **Laxman_prodigy said:**
> 
I found many threads but they seem to be quite old now. I use Ubuntu 9.10.

Please guide me as to how should I proceed while fully utilising my system for great playback.:confused:

Perhaps this guide will provide at least a start:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

All the best,

Andrew

---

### Post by Laxman_prodigy on 2010-02-24
Thanks Andrew. I did that and it's nice but I can't hear anything. Why isn't there any audio in MPlayer while I have it in VLC.

What should I check?

---

### Post by andrew.46 on 2010-02-24
Hi Laxman,

> **Laxman_prodigy said:**
>  Why isn't there any audio in MPlayer while I have it in VLC.

Try running a file in the following manner:
```

mplayer -v <myfile>
```

obviously substituting <myfile> with the real name of *your* file and post the command + terminal output here.

All the best,

Andrew

---

### Post by Laxman_prodigy on 2010-02-24
Thanks. I actually figured it out one minute after I posted the query.

Thank you for the support.

---

### Post by Laxman_prodigy on 2010-02-24
Hi, Andrew

Again, I found a thread here in forums on how to enable multithreading while compiling Mplayer.

Now, is it possible that while following the guide you suggested I could also combine that "multithreading" thingy into it while compiling Mplayer?:D

---

### Post by andrew.46 on 2010-02-24
Hi Laxman,

> **Laxman_prodigy said:**
> Now, is it possible that while following the guide you suggested I could also combine that "multithreading" thingy into it while compiling Mplayer?:D

I have not experimented with MPlayer-mt but details can be seen here:

[http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html)

and it should work well enough with my guide when spliced in :).

Andrew

---

### Post by Laxman_prodigy on 2010-02-28
"Special note concerning vdpau support: As of r29823 the svn MPlayer requires Version 190.32 (or later) of the NVidia drivers to enable vdpau output, which effectively renders the Karmic NVidia drivers and libvdpau package obsolete.** To obtain vdpau output you will now need to obtain the latest drivers from NVidia and compile MPlayer against them, no extra options are needed as MPlayer will detect the drivers/libraries and enable vdpau support automagically."**


I already compiled it but I think vdpau support is not done. You said, "To obtain vdpau output you will now need to obtain the latest drivers from NVidia and compile MPlayer against them".

To do this i.e compiling MPlayer against NVidia drivers, did you list that code there too?

I mean, I did as you said and I have Mplayer running. Is vdpau support enabled? How should I check?

---

### Post by andrew.46 on 2010-02-28
Hi Laxman,

> **Laxman_prodigy said:**
>  Is vdpau support enabled? How should I check?

You may have seen MPlayer checking for the required libraries during *./configure *but if you missed this try the following:

```
mplayer -vo help
```

and this should reveal if you have compiled in vdpau support. And finally you can test the *-vo vdpau *on the commandline and MPlayer will tell you if it is not available to you...

All the best,

Andrew

---

### Post by Laxman_prodigy on 2010-03-09
Andrew.

I found somewhere in the thread about compiling through multi-threaded way. Is that different from this one?


If yes, can I combine both of these?
 
Thank you.:)

---

### Post by andrew.46 on 2010-03-09
Hi Laxman,

> **Laxman_prodigy said:**
> I found somewhere in the thread about compiling through multi-threaded way. Is that different from this one?

Unfortunately I know very little about the multi-threaded MPlayer so I can offer little advice except tp point you to the MPlayer site that mentions [the details]("http://www.mplayerhq.hu/design7/news.html")...

All he best,

Andrew

---

### Post by Laxman_prodigy on 2010-03-11
Thank you Andrew.

I have done exactly as you said and I would be very glad if you help me with this settings in the SMplayer preference:

Video: Output driver: vdpau or xv or what? 

When I do vdpau, there is no video only sound. With xv it runs good. It is making me believe vdpau is not enabled. Kindly shed the ignorance/

Thank you.

---

### Post by andrew.46 on 2010-03-11
Hi Laxman_prodigy,

Certainly if xv works the best this would be the best choice. You can see what is available on your system by running:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vo help[/COLOR]**
MPlayer SVN-r30881-4.3.3 (C) 2000-2010 MPlayer Team
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

Andrew

---

### Post by Laxman_prodigy on 2010-03-12
Thank you for the reply, Andrew.
This is what I got from the terminal:

MPlayer SVN-r30881-4.3.4 (C) 2000-2010 MPlayer Team
Available video output drivers:
    vdpau    VDPAU with X11  (Does this mean that vdpau is enabled?)
    xv    X11/Xv
    gl_nosw    OpenGL no software rendering
    x11    X11 ( XImage/Shm )
    xover    General X11 driver for overlay capable video output drivers
    gl    OpenGL
    gl2    X11 (OpenGL) - multiple textures version
    dga    DGA ( Direct Graphic Access V2.0 )
    sdl    SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
    fbdev    Framebuffer Device
    fbdev2    Framebuffer Device
    svga    SVGAlib
    matrixview    MatrixView (OpenGL)
    aa    AAlib
    caca    libcaca
    v4l2    V4L2 MPEG Video Decoder Output
    directfb    Direct Framebuffer Device
    dfbmga    DirectFB / Matrox G200/G400/G450/G550
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

It works perfectly fine with "xv" but not with "vdpau". Does "xv" consist of "vdpau" enabling or Mplayer takes it automatically? 

Since I cannot enable that "vdpau" under video output drivers; I really am getting irritated.:P
Is it not required?

---

### Post by Laxman_prodigy on 2010-03-15
Please reply soon Andrew.

---

### Post by andrew.46 on 2010-03-15
Hi Laxman,

> **Laxman_prodigy said:**
> Please reply soon Andrew.

Sorry, the 'real world' has been intruding :). If MPlayer still fails with:

```
mplayer -vo vdpau -vc ffh264vdpau **[COLOR="Red"]< my_file >[/COLOR]**
```

where < my_file > is the name of *your* file you might have a good case for removing your build of MPlayer and considering using this PPA:

Nvidia Vdpau Team PPA 
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

This contains the nvidia drivers, mplayer and smplayer in the one PPA. Hopefully this will enable vdpau on your system and make your life a lot easier :).

Andrew

---

### Post by Laxman_prodigy on 2010-03-17
Thanks Andrew.

I will do it and report the results soon.:D

---

### Post by Laxman_prodigy on 2010-03-18
After this command, 
mv -v $HOME/.mplayer/config $HOME/.mplayer/config_bak

I get this:

daulat@Buntaland:~/mplayer$ mv -v $HOME/.mplayer/config $HOME/.mplayer/config_bak
mv: cannot stat `/home/daulat/.mplayer/config': No such file or directory

What is happening here?:(

---

### Post by andrew.46 on 2010-03-18
Hi Laxman,

> **Laxman_prodigy said:**
> 
```
mv: cannot stat `/home/daulat/.mplayer/config': No such file or directory
```

What is happening here?:(

This simply means that you have no pre-existing MPlayer configuration file in place and can proceed to create one. This is simply a safeguard so that a configuration file that somebody has carefully written is not overwritten.

Andrew

---

### Post by Laxman_prodigy on 2010-03-20
Thanks Andrew.:)

---

### Post by Laxman_prodigy on 2010-03-21
Hi Andrew.

I think I have messed it all up. Now I try to make myself clear. I am trying on another system with 8500GT card.

I have installed Nvidia 195' version as per their method.

Now, I am going to follow your "no-gui guide" to see again if "VDPAU" works for me.


Wish me luck today.

---

### Post by Laxman_prodigy on 2010-03-22
Hi Andrew.:)

So, this is what I get:

```
laxman@Cray-Jaguar:~$ mplayer -vo vdpau -vc ffh264vdpau /home/laxman/Videos/Hollywood/Transformers.mp4 
MPlayer SVN-r30945-4.3.4 (C) 2000-2010 MPlayer Team

Playing /home/laxman/Videos/Hollywood/Transformers.mp4.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [H264]  1280x528  24bpp  23.976 fps  1819.9 kbps (222.2 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 1
 compatible_brands: isom
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, s16le, 327.9 kbit/7.12% (ratio: 40990->576000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
[AO_ALSA] alsa-lib: pcm_hw.c:1327:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] Playback open error: Device or resource busy
[AO ESD] latency: [server: 0.24s, net: 0.00s] (adjust 0.24s)
AO: [esd] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video

```

---

### Post by andrew.46 on 2010-03-22
Hi Laxman,

Could you run the following for me?

```
sudo find /usr -iname 'libvdpau_nvidia.so'
```

and can I ask if you are running 64 or 32 bit Ubuntu?

Thanks,

Andrew

---

### Post by Laxman_prodigy on 2010-03-22
Hi Andrew.

Here it is:
```
laxman@Cray-Jaguar:~$ sudo find /usr -iname 'libvdpau_nvidia.so'
[sudo] password for laxman: 
/usr/lib32/libvdpau_nvidia.so
/usr/lib/libvdpau_nvidia.so

```

I am using 64-bit Ubuntu.:)

---

### Post by andrew.46 on 2010-03-22
Hi Laxman_prodigy,

I suspect I am the wrong man to diagnose a problem with 64bit Ubuntu and nVidia drivers as I possess neither :(. In fact as a sidenote this is part of the reason I am stepping back substantially from my Forums work with MPlayer and vlc...

Having said that, on a 64bit system do the libraries actually live in a directory marked /usr/lib64 rather than /usr/lib32 ? I have a suspicion there must be a missing symbolic link to the libvdpau library from the correct 64bit library location but without such an installation I cannot really check...

Can I suggest that you assemble the information you have already and start a new thread? I am going to be of little help to you by the look of it and it looks like the experts with working 64bit installations of nVidia drivers are not wattching this thread :).

All the best,

Andrew

---

### Post by Laxman_prodigy on 2010-03-23
Hi Andrew.

Thank you. I will do that.

---

### Post by Laxman_prodigy on 2010-03-23
Hi Andrew.:)

I forgot one thing to ask.

You suggested me to add Nvidia Vdpau Team PPA.

I have already installed Nvidia driver version 195 from the site of Nvidia and installed as per their instruction.

Now, after adding this ppa, do I need to uninstall this one and install their version?

If yes,

Please suggest me the exact packages to download from their site. I just can't figure out.

---

### Post by andrew.46 on 2010-03-23
Hi laxman,

> **Laxman_prodigy said:**
> 

You suggested me to add Nvidia Vdpau Team PPA.

I have already installed Nvidia driver version 195 from the site of Nvidia and installed as per their instruction.


I would suggest remain for the moment with the drivers from the Nvidia site and get those working with MPlayer. 

All the best,

Andrew

---

### Post by Laxman_prodigy on 2010-03-28
Hi Andrew.

I have now figured it out that my graphics card is faulty.

And the "no-gui mplayer guide" which you suggest me at the beginning of this thread works with vdpau support in my brother's PC. I compiled it as per your instructions and it now works which means that it will work if I get a new graphics card.

Thank you Andrew. You hung up here to help me.:)

---

### Post by andrew.46 on 2010-03-28
Hi Laxman,

Good to see that you finally sorted the whole thing out :). And all the best with your new graphics card when you pick it up, there are some nice ones out there now!

All the best,

Andrew

---

