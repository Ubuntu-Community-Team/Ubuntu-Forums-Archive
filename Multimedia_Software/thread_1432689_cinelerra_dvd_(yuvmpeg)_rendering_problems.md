---
title: "cinelerra dvd (yuvmpeg) rendering problems"
date: 2010-03-18
forum: Multimedia Software
---

### Post by ezergal on 2010-03-18
Hi,
I am a new user in ubuntu. I have managed so far to capture and edit some videos (not quite for fun) in karmic koala; i was a adobe premiere user back in windows days, and i am wishing not to go back in time. This is the thing: I have made my video editting in cinelerra and now wish to export to a dvd, now here i am suposed to export to yuvmpg (.m2v) and it goes on perfectly well until the end of the render in which it throws me back the following:

[I]int YUVStream::read_header(): y4m_read_stream_header() failed: bad header magic
int YUVStream::open_read(char*): Bad YUV4MPEG2 header: parameter out of range[/I]

Now, i took the precaution of opening cinelerra (actualy cinecutie) in the terminal, so here are the render details... (i only rendered inmediatly after opening cinelerra)

ezergal@puerto:~$ cinelerra
Cinelerra 2.1CV (C) 2006 Heroine Virtual Ltd.
Compiled on ven ott  2 22:09:47 UTC 2009

Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
read_toc: date mismatch
read_toc: date mismatch
Render::run 1
Render::run 2
Render::run 3
Render::run 4
Render::run 5
Render::run 6
Render::run 7
Render::run 8
Render::run 8.1
Render::run 8.2
Render::run 8.3
Render::run 9
Render::run 10
trying popen( ffmpeg -f yuv4mpegpipe -i - -y -target dvd -f mpeg2video /home/ezergal/citrico.m2v)
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
Input #0, yuv4mpegpipe, from 'pipe:':
  Duration: N/A, bitrate: N/A
    Stream #0.0: Video: rawvideo, yuv420p, 720x480, PAR 40:33 DAR 20:11, 29.97 tbr, 29.97 tbn, 29.97 tbc
Assuming NTSC for target.
Output #0, mpeg2video, to '/home/ezergal/citrico.m2v':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 40:33 DAR 20:11], q=2-31, 6000 kb/s, 90k tbn, 29.97 tbc
Stream mapping:
  Stream #0.0 -> #0.0
frame=17789 fps= 55 q=2.0 Lsize=  425986kB time=593.53 bitrate=5879.6kbits/s    
video:425986kB audio:0kB global headers:0kB muxing overhead 0.000000%
Render::run: Session finished.
Render::render 90
Render::run 11
Render::run 12
Render::run 100

And i am quite stucked... any help would be (you don't know how much) usefull. Thanks!

---

### Post by alegallo on 2010-03-18
did you check the tutorial by Akir4d about cooking a dvd? 
it's quite good, and also really simple
[http://akiradproject.net/tutorial](http://akiradproject.net/tutorial)

first of all, no audio, right?

---

### Post by ezergal on 2010-03-18
Yep, no audio. And the pipe reads the following  
*ffmpeg -f yuv4mpegpipe -i - -y -target dvd -f mpeg2video*

I removed *-ilme -ildct -hq* since the render just wouldn't start with them... my problem comes at last when it's rendered and it throws me back the info above.

---

