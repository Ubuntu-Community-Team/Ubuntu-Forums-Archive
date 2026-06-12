---
title: "Simple ffmpeg problem. Guru required."
date: 2011-05-21
forum: Multimedia Software
---

### Post by nickTaylor1181 on 2011-05-21
Hiya

I'm attempting to use ffmpeg as part of my post-shooting workflow. I use a Cannon T2i which shoots H.264 in a MOV wrapper... once the clips are out of the camera, I need to go through them and identify the usable bits of footage... store them in a folder called "clips". 

So. I use this:

ffmpeg -i test.MOV -vcodec copy -acodec copy -ss 00:00:05 -t 00:00:20 clips/test.MOV

This eg taking 20 seconds starting after 5 seconds.

Works fine... except that the sound appears to start about 1 second before the video.

I've tinkered with -async 1 etc... nothing seems to make a difference.

Any ideas on how to get the two in sync?



(ubuntu 9.10)

---

### Post by andrew.46 on 2011-05-22
It is a little odd that the time is out to start with. Your best bet is to make sure you are using the very latest FFmpeg:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and see if this resolves the problem. If not you could tinker with the *-itsoffset* option, I usually calculate the sound delay or advance by using SMPlayer --> Audio --> Delay. Slightly painful work though :(.

---

### Post by nickTaylor1181 on 2011-05-22
If I do ffmpeg -version I get

> FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 31 2011 18:50:06, gcc: 4.4.1
FFmpeg SVN-r19352-4:0.5+svn20090706-2ubuntu2.3
libavutil     49.15. 0 / 49.15. 0
libavcodec    52.20. 0 / 52.20. 0
libavformat   52.31. 0 / 52.31. 0
libavdevice   52. 1. 0 / 52. 1. 0
libavfilter    0. 4. 0 /  0. 4. 0
libswscale     0. 7. 1 /  0. 7. 1
libpostproc   51. 2. 0 / 51. 2. 0



but... my laptop is a finely balanced machine - I installed avidemux recently and it took about 3 days to get it working again. So um... the instructions on how to upgrade... and the 170 odd pages of follow-up problems are simply too much for one as simple as myself to contemplate.

Thanks though.

---

### Post by andrew.46 on 2011-05-22
That's fair enough, but perhaps you may have the *-itsoffset* option available in your version anyway? Might be worth a look...

---

### Post by nickTaylor1181 on 2011-05-22
Yea, I guess. Kindof fiddley though.

---

### Post by andrew.46 on 2011-05-22
> **nickTaylor1181 said:**
> Yea, I guess. Kindof fiddley though.

Indeed it is. Reminds me of:

[http://www.fatherpius.littleway.ca/MOSES2.jpg](http://www.fatherpius.littleway.ca/MOSES2.jpg)

:).

---

### Post by nickTaylor1181 on 2011-05-22
Yea... what spoiled creatures are we. We want everything, now... at the speed of thought, and thought controlled. What? Lift a finger? Are you mad?

There may be a pattern to the desync. Hopefully. Always out by the same amount perhaps. I'll need to experiment... because the alternative is to fire up Premiere Pro... which is like trying to do a u-turn with an oil-tanker.

---

### Post by andrew.46 on 2011-05-22
Mind you the real FFmpeg guru is away from the Forums for a short time, hopefully Fakeoutdoorsman will be back soon and he may have a better way of correcting AV sync with FFmpeg.

---

### Post by nickTaylor1181 on 2011-05-22
Well... there's a couple of ways it will go:


1) a terrifying and potentially catastrophic software upgrade

2) a process of trialing and erroring of indefinite duration

3) an instant fix

Being cursed with... you know... "lazy bones", I'm hoping for 3 - which isn't unreasonable, because short-cuts-to-3 are what the internet is really good at. Shared knowledge and all that.

---

### Post by andrew.46 on 2011-05-23
Can you post one of the offending files here? I would be interested to have a look...

---

### Post by nickTaylor1181 on 2011-05-23
.... aaaaaannnndd... 

now it works perfectly, and I don't know why.

I just shot a couple of little clips because the ones I was having a problem with were a bit big to upload to the web... little ones worked... made a really long one. That one works now too.

I was shooting 25fps before... which I don't usually do, now it's 24fps. I was also editing files that were living on my windows drive (I dual-boot) rather than my linux one.

Neither of which should make a difference - but at least now I have something that works, I can inflict process-of-elimination on future de-syncery should it recur.

Thanks for all your help.



Nick

---

### Post by JohnMoras on 2011-05-28
Hey guys, sorry if this is irrelevant to the point discussed but i've been having some ffmpeg problems too. I'm running Natty and i was trying to convert an youtube video i've downloaded (.flv format) to a .mp3 file,with the following command: 

> ffmpeg -i original_video.flv requested_track.mp3

but all i get is that, and no conversion in the end:

> FFmpeg version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2000-2010 the Libav developers
  built on Mar 22 2011 15:35:22 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[flv @ 0x904f420]Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'XxBO_yeHdmY.flv':
  Metadata:
    duration        : 181
    starttime       : 0
    totalduration   : 181
    width           : 450
    height          : 360
    videodatarate   : 579
    audiodatarate   : 117
    totaldatarate   : 703
    framerate       : 25
    bytelength      : 15962457
    canseekontime   : true
    sourcedata      : B3E4B0A47HH1306536682587404
    purl            : 
    pmsg            : 
  Duration: 00:03:01.15, start: 0.000000, bitrate: 713 kb/s
    Stream #0.0: Video: h264, yuv420p, 450x360 [PAR 1:1 DAR 5:4], 593 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 119 kb/s
Output #0, mp3, to 'Pavlos.mp3':
    Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Encoder (codec id 86017) not found for output stream #0.0

i guess that the problem is the missing 86017 codec but i can't be quiet sure about it on the one hand and couldn't get to understand how i could install it (google search) on the other hand.

---

### Post by andrew.46 on 2011-05-28
> **JohnMoras said:**
> i guess that the problem is the missing 86017 codec but i can't be quiet sure about it on the one hand and couldn't get to understand how i could install it (google search) on the other hand.

Your copy of FFmpeg has had the ability to encode to mp3 removed. Good news is that this ability is easily restored:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

BTW when you have done this you might be best to add a bitrate to your command as you will find the default 64kb disappointing:

```

ffmpeg -i XxBO_yeHdmY.flv **[COLOR="Red"]-acodec libmp3lame -ab 128k[/COLOR]** Pavlos.mp3 

```

Hope this works for you :).

---

### Post by JohnMoras on 2011-05-28
Thanks for the quick response ;). But the problem insists:p!!!
I tried
> ffmpeg -i XxBO_yeHdmY.flv **[COLOR=Red]-acodec libmp3lame -ab 128k[/COLOR]** Pavlos.mp3

and i got that message in response: 
> FFmpeg version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2000-2010 the Libav developers
  built on Mar 22 2011 15:35:22 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[flv @ 0x9342420]Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'XxBO_yeHdmY.flv':
  Metadata:
    duration        : 181
    starttime       : 0
    totalduration   : 181
    width           : 450
    height          : 360
    videodatarate   : 579
    audiodatarate   : 117
    totaldatarate   : 703
    framerate       : 25
    bytelength      : 15962457
    canseekontime   : true
    sourcedata      : B3E4B0A47HH1306536682587404
    purl            : 
    pmsg            : 
  Duration: 00:03:01.15, start: 0.000000, bitrate: 713 kb/s
    Stream #0.0: Video: h264, yuv420p, 450x360 [PAR 1:1 DAR 5:4], 593 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 119 kb/s
Unknown encoder 'libmp3lame'

I do get the feeling that i still have the same problem but with the encoder described with name and not id number this time :p! Please enlight me asap

---

### Post by JohnMoras on 2011-05-28
Forget about the above post....i just read your response way too fast :P Thank you very much again :)

---

### Post by andrew.46 on 2011-05-28
> **JohnMoras said:**
> Forget about the above post....i just read your response way too fast :P Thank you very much again :)

You forgot to add the extra libavcodec library :). Good to see you have things going now though!

---

