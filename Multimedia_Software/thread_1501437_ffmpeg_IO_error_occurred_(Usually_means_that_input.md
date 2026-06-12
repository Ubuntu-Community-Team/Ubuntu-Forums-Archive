---
title: "ffmpeg: I/O error occurred (Usually means that input file is truncated ...)"
date: 2010-06-04
forum: Multimedia Software
---

### Post by frankrens on 2010-06-04
I'm using gphoto2 to create a series of time lapse photos using my Canon SX100IS. The images are created and can be viewed and I'm trying to create an mpeg from them using the following command: 

ffmpeg -f image2 -i IMG_%04d.JPG -sameq FirstMovie

and get this result:

FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
/home/frank/Test/IMG_%04d.JPG: I/O error occurred
Usually that means that input file is truncated and/or corrupted.

Any idea what I'm doing wrong?

---

### Post by reign85 on 2012-05-10
HEY, I get the same issue...

did you find any solve?


I try to make a flv video with 493 pics file

for this i do a shell script to get symbolical links like it's needed:

(...)
lrwxrwxrwx 1 root root 20 May  9 15:04 img489.jpg -> m120509153104700.jpg
lrwxrwxrwx 1 root root 20 May  9 15:04 img490.jpg -> m120509153108151.jpg
lrwxrwxrwx 1 root root 20 May  9 15:04 img491.jpg -> m120509153113247.jpg
lrwxrwxrwx 1 root root 20 May  9 15:04 img492.jpg -> m120509153116781.jpg
lrwxrwxrwx 1 root root 20 May  9 15:04 img493.jpg -> m120509153119740.jpg


However, when i execute the ffmpeg cmd:
ffmpeg -r 25 -an -b 360k -i img%03d.jpg -s 800x600 -f flv video.flv

in my directory:
www/tmp


i get this error:
FFmpeg version SVN-r0.5.6-4:0.5.6-3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.6-3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 31 2011 15:16:11, gcc: 4.4.5
img%03d.jpg: I/O error occurred
Usually that means that input file is truncated and/or corrupted.

all my files get 777 access...

Can you help me? it appear many users get the same problem, but i don't find any solves

thank you so much.

---

### Post by FakeOutdoorsman on 2012-05-11
Try using cat to feed the original images to ffmpeg:
```
cat *.jpg | ffmpeg -f image2pipe -vcodec mjpeg -i - output
```
Also, you're applying *-b 360k* as an input option (although ffmpeg may be applying it as an output option anyway). Move it past *-i img%03d.jpg* to apply the option to the output.

---

