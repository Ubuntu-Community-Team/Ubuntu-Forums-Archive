---
title: "ffmpeg installed ? ubuntu 9.04"
date: 2009-04-30
forum: Multimedia Software
---

### Post by mysoogal on 2009-04-30
i think i installed ffmpeg

like this sudo apt-get install ffmpeg

, i tried to get thumbnail from mpeg video but not working. i installed some other media things from that win32code website etc :confused:

here is the output

```
yugo@ubuntu:~$ cd /home/yugo/Desktop
yugo@ubuntu:~/Desktop$ ffmpeg -v 0 -y -i diamondufo.mpeg -vframes 1 -ss 60 -vcodec mjpeg -f rawvideo -s 286x160 -aspect 16:9 video.jpg
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=    0 fps=  0 q=0.0 Lsize=       0kB time=10000000000.00 bitrate=   0.0kbits/s    
video:0kB audio:0kB global headers:0kB muxing overhead nan%
yugo@ubuntu:~/Desktop$ 

```

how come i do not get thumbnails ? 



here is the ffmpeg commands i use


```
customized input 

   1.	
 	 ffmpeg -v 0 -y -i diamondufo.mpeg -vframes 1 -ss 60 -vcodec mjpeg -f rawvideo -s 286x160 -aspect 16:9 video.jpg

	 


$input unvictimized 

   1.
     	 ffmpeg -v 0 -y -i $VIDEOFILE -vframes 1 -ss 4 -vcodec mjpeg -f rawvideo -s 86x60 -aspect 4:3 $THUMBNAILFILE

	' dynamic input to be used with php script to create your own thumbs


encode to flv

	2. 

	ffmpeg -i diamondufo.mpeg -ar 22050 -f flv -s 428x240 -y 

myvideo.flv
```

---

### Post by mysoogal on 2009-04-30
sorry it seems, the commands for ffmpg were not right

this command gave me return of thumbnail.:KS

ffmpeg -v 0 -y -i video.mpeg -vframes 1 -ss 4 -vcodec mjpeg -f rawvideo -s 86x60 -aspect 4:3 video.jpg


seem to work good 

admins can delete this post.

---

