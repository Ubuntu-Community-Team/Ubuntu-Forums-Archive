---
title: "Convert .avi to .mov with ffmpeg?"
date: 2010-07-29
forum: Multimedia Software
---

### Post by braniac5 on 2010-07-29
I'm making little animated bits in GIMP with the gap package. I can only get GIMP to encode the files as .avi. Problem here is that when I try to use any converter, it compresses 80MB files down to 1MB-4MB files and, unsurprisingly, the video quality is terrible. WinFF and ffmpeg (via terminal) output at a drastically reduced size. Is there some way to keep the files big/big-ish? I don't want to lose any detail.

---

### Post by andrew.46 on 2010-08-01
Hi braniac5,

Could you show the FFmpeg command that you have used and the full terminal output?

Andrew

---

### Post by braniac5 on 2010-08-01
This is the one that produces the highest quality video (about 5.6MB) though it still reduces the size of the video by about 1/5:

computo@computo-laptop:~/Desktop$ ffmpeg -i test.avi -target ntsc-dvd -s 1280x720 test.mov
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
Input #0, avi, from 'test.avi':
  Duration: 00:00:08.05, start: 0.000000, bitrate: 27897 kb/s
    Stream #0.0: Video: mjpeg, yuvj422p, 1280x720, 18 tbr, 18 tbn, 18 tbc
Output #0, dvd, to 'test.mov':
    Stream #0.0: Video: mpeg2video, yuv420p, 1280x720, q=2-31, 6000 kb/s, 90k tbn, 29.97 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=  240 fps= 21 q=2.0 Lsize=    5492kB time=7.97 bitrate=5641.7kbits/s    
video:5370kB audio:0kB global headers:0kB muxing overhead 2.270263%

---

### Post by braniac5 on 2010-08-01
And this one I've tried as well (on a different video), which works okay but also reduces the size of the file by about 1/5: 

computo@computo-laptop:~/Desktop$ ffmpeg -i test.avi -sameq -s 1280x720 test.mov
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
Input #0, avi, from 'test.avi':
  Duration: 00:00:05.38, start: 0.000000, bitrate: 40443 kb/s
    Stream #0.0: Video: mjpeg, yuvj422p, 1280x720, 18 tbr, 18 tbn, 18 tbc
Output #0, mov, to 'test.mov':
    Stream #0.0: Video: mpeg4, yuv420p, 1280x720, q=2-31, 200 kb/s, 90k tbn, 18 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=   97 fps= 21 q=4.0 Lsize=    3822kB time=5.39 bitrate=5809.6kbits/s    
video:3820kB audio:0kB global headers:0kB muxing overhead 0.039342%

---

### Post by jsstn on 2010-08-01
have you tried setting the bitrate of the output file explicitly? it can be done with the -b flag (you may have noticed that your resulting bitrate is about one seventh of your initial bitrate).
also try forcing a quality of one: -qmax 1 [-qmin 1] (this problably won't work, as your -sameq doesn't give the desired output). -max/minrate does the same for bitrate.

---

### Post by andrew.46 on 2010-08-02
Hi Braniac,

Any particular reason for the .mov format? Anyway I believe you can put h264 video in such a container in which case I would suggest a quick look at Fakeoutdoorsman's guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and this way you get to use some presets that should make your life a lot easier.

Andrew

---

### Post by braniac5 on 2010-08-04
> **jsstn said:**
> have you tried setting the bitrate of the output  file explicitly? it can be done with the -b flag (you may have noticed  that your resulting bitrate is about one seventh of your initial  bitrate).
also try forcing a quality of one: -qmax 1 [-qmin 1] (this problably  won't work, as your -sameq doesn't give the desired output).  -max/minrate does the same for bitrate.

Whenever I try to set a bitrate with -b ffmpeg seems to ignore it. I will give -qmax a try (and thanks for the help, by the way - I'm quite fond of the Ubuntu community). 


> **andrew.46 said:**
> Hi Braniac,

Any particular reason for the .mov format? Anyway I believe you can put h264 video in such a container in which case I would suggest a quick look at Fakeoutdoorsman's guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and this way you get to use some presets that should make your life a lot easier.

Andrew

I will definitely check this out. For now I'm going to stick with "$ ffmpeg -i test.avi -sameq -s 1280x720 test.mov" and test the other methods later - it produces the best results (the target ntsc-dvd produces some weird wavering effects on the background) and is decent-enough quality for what I need at the moment. I'll feel more comfortable fiddling with ffmpeg once the project's done. 

The animations I'm doing need to be opened/edited in Final Cut on a friend's Mac. He is the opposite of tech savvy and I (obviously) use an Ubuntu machine.

---

