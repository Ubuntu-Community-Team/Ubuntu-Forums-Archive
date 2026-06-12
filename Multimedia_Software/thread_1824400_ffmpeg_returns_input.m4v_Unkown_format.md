---
title: "ffmpeg returns input.m4v: Unkown format"
date: 2011-08-13
forum: Multimedia Software
---

### Post by david.medine on 2011-08-13
My dad is a teacher and fairly computer challenged. He wants to be able to rip DVDs and then cut sections out to use as examples in his classes. Now, I don't want him to have to *buy* commercial software to do this, so I told him I would make a GUI frontend to command line programs to do this stuff for him. (He just got a MacBookPro and is struggling with the switch from Windows. I don't think that learning to use the terminal is in the cards for him.)

Anyway, I don't use ffmpeg too often, but have done what I wanted with it in the past. I installed it on his mac and it works great, but I am developing the GUI on my own machine. To convert the m4v (which handbrake gives you when you rip a DVD onto Mac -- I know you can rip DVDs with ffmpeg, but it is a million times simpler to do it with HandBrakeCl) to avi I am running the following command successfully on his computer:
```

> ffmpeg -sameq -i input.m4v -f avi (plus may other flags) output.avi

```However, when I run the identical command on my Ubuntu 10.10 machine I get the following:
```

FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf
--enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable
libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable
runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394
--enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 31 2011 18:53:20, gcc: 4.4.3
input.m4v: Unknown format

```From everything that I have read on the web pertaining to this problem, it seems like ffmpeg on linux should not have any trouble with m4v. I can confirm that all the mpeg4 formats are supported. According to 
```

> ffmpeg -formats

``` they are all there, so I am stumped. I also tried removing ffmpeg (which I installed from source) and re-installing from the Ubuntu repository, but still no joy. At least it works on my dad's machine, so I can compete the GUI in the meantime. But I want this to work on good operating systems as well as Steve Jobs' gear.

---

### Post by BicyclerBoy on 2011-08-13
This may not solve the problem but eventually you will come up against it..

You should install the medibuntu repository versions of the libav* libraries (7?).
The libav*s are the shared libs from ffmpeg..
The std repos versions are stripped.

I would not recommend use of .avi container for anything..

---

### Post by david.medine on 2011-08-18
thanks, I will try this
what containers do you recommend (I really don't know anything about video)

---

### Post by BicyclerBoy on 2011-08-19
Well answer depends on the windows codecs/filters/muxers etc..

I recommend matroska container mkv because it is the best & is an open source spec.

But mpeg4 PS containers/files should be universal
m4v is just a silly apple name for mpeg4/10 vcodec in mpeg4 container with option of AC3 audio (along with AAC & DRM stuff)

Windows boxes have problems with AAC audio by default.
Apple quicktime player or some free AAC decoder fixes that.

If you are using VLC on the windows box, there is no problem with anything.

Don't be fooled into using .avi container for anything..

---

### Post by david.medine on 2011-08-26
Well, I made the GUI in Java for my Dad, so he can slice up video files using ffmpeg as the backend and he likes it. I have to teach Java, which is the only reason I develop in it. I kept the container mp4 as he is on Mac. Eventually I will expand the GUI so that it can access all of ffmpeg's many options. Thanks for advice about containers. All this is moot since I still cannot get my machine to recognize m4vs and furthermore, it all of a sudden started freezing whenever I access the wireless card -- but that is another thread altogether.

Computers are really cool, but a constant source of problems in my life.

---

### Post by BicyclerBoy on 2011-08-26
The m4v issue should be fixed by using:
medibuntu repos
& then replacing the existing libav* packages (from ffmpeg) with
libav*-extras

But if you compile from source then your ffmpeg uses the static private self contained libav* (unstripped).

Note:
I have seen m4v associated with mpeg4-asp, but I believe this is incorrect.

---

### Post by Chronon on 2011-08-27
I think that m4v can be used for any mp4 container with a video stream.  m4a refers to mp4 containing only audio streams (and metadata).

---

