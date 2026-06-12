---
title: "OpenCV w/ FFMPEG enabled"
date: 2009-03-17
forum: Multimedia Software
---

### Post by darkzerox on 2009-03-17
Hi guys,

I know I've complained a bit about OpenCV before, but I'm getting a new error when trying to compile an SVN checkout of OpenCV with FFMPEG enabled.

Here's the error:
```
[ 85%] Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap_ffmpeg.o
~/Desktop/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function &#8216;virtual bool CvVideoWriter_FFMPEG::open(const char*, int, double, CvSize, bool)&#8217;:
~/Desktop/opencv/src/highgui/cvcap_ffmpeg.cpp:1167: warning: &#8216;AVFormatContext* av_alloc_format_context()&#8217; is deprecated (declared at /usr/local/include/libavformat/avformat.h:873)
~/Desktop/opencv/src/highgui/cvcap_ffmpeg.cpp:1167: warning: &#8216;AVFormatContext* av_alloc_format_context()&#8217; is deprecated (declared at /usr/local/include/libavformat/avformat.h:873)
~/Desktop/opencv/src/highgui/cvcap_ffmpeg.cpp:1203: error: &#8216;PIX_FMT_RGBA32&#8217; was not declared in this scope

```

I'm compiling it with:
```
cmake .
make
```

as the INSTALL file suggests.  I can't find PIX_FMT_RGBA32 defined anywhere, not even in pixfmt.h, and Google isn't turning up any meaningful results.  Has ffmpeg removed this definition in a recent version, or is this a bug in OpenCV?

I'm not sure how to get around this problem :(

FFMPEG info:
```
FFmpeg version SVN-r18019, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-x11grab --enable-libdc1394 --enable-shared
  libavutil     50. 0. 0 / 50. 0. 0
  libavcodec    52.21. 0 / 52.21. 0
  libavformat   52.31. 1 / 52.31. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 16 2009 14:47:15, gcc: 4.3.2
```

---

### Post by FakeOutdoorsman on 2009-03-17
Welcome to the bleeding-edge!  Open cvcap_ffmpeg.cpp and change PIX_FMT_RGBA32 to PIX_FMT_RGB32 (line 1203).  Looks like 1.1pre1 and SVN have the same line.

I haven't tested this.  Perhaps a tutorial for compiling OpenCV with SVN FFmpeg would be useful.  I suppose I should start by figuring out what OpenCV is and does.

---

### Post by FakeOutdoorsman on 2009-03-17
Ok, I don't know if that will actually work, but as for the warning:
```
&#8216;AVFormatContext* av_alloc_format_context()&#8217; is deprecated
```
The source of avformat.h says:
```
 * @deprecated Use avformat_alloc_context() instead.
```

---

### Post by darkzerox on 2009-03-17
Ah! My saviour returns!

I'm curious how you would know to change PIX_FMT_RGBA32 to PIX_FMT_RGB32 if you've never used OpenCV before? I was thinking I could use another definition, but I wasn't sure what would be suitable. Why not PIX_FMT_RGBA?

OpenCV is a computer vision library. It has more algorithms than I can list, but in particular, I'm using it for face detection and optical flow computation. Very useful stuff for image processing.

The problem with bleeding-edge is that this worked two weeks ago, and now it's giving me issues :p Earlier versions however, have a couple bugs that I can't work around.

---

### Post by darkzerox on 2009-03-17
Just an FYI in case anyone else runs into this problem, if you get the run-time error when trying to open a videp:

> (ERROR)icvOpenAVI_XINE(): Unable to initialize video driver.

You need to sudo apt-get install libxine1 and/or xine-console. Not sure which one made it work (probably the former), but if not, try the latter. Took me a long time to figure this out.

Also, early tests seem to show fewer errors WITHOUT xine and gstreamer. FFMPEG seems to work better for opening videos, although I have yet to find a reliable way to get the number of frames in an AVI.

---

### Post by FakeOutdoorsman on 2009-03-17
> **darkzerox said:**
> Ah! My saviour returns!

I'm curious how you would know to change PIX_FMT_RGBA32 to PIX_FMT_RGB32 if you've never used OpenCV before?
A search for *"PIX_FMT_RGBA32" "was not declared in this scope"* lead me to this page:
[[gelöst] osdpip-0.0.10 mit aktuellem ffmpeg (REV. 17984)](http://www.vdr-portal.de/board/thread.php?postid=800936)

However, I didn't do any testing.

---

### Post by darkzerox on 2009-03-22
Ah... I probably skipped that page because it wasn't in english. Thanks again FakeOutdoorsman, really appreciate it :)

---

### Post by xavierda on 2009-03-22
> **darkzerox said:**
> Ah... I probably skipped that page because it wasn't in english. Thanks again FakeOutdoorsman, really appreciate it :)

darkzerox, I just came across the same error message! :(

I have had real problems getting OpenCV (Rev 1649), ffmpeg (rev 18140) and Ubuntu 8.10 (kernel 2.6.27-11-generic) to work nicely together with my Logitech Webcam 9000 Pro.

It has been a case of getting 2 of the 3 going. Fix the problem issue and something else breaks - typical! Hehe

Basically, I want to be able to use standard webcam apps but there are issues with the latest kernel I haven't been able to quite resolve. Ekiga works reliably, but others (such as guvcview) don't.

What kernel, OpenCV SVN rev, ffmpeg SVN rep did you eventually manage to compile?

FakeOutdoorsman, for ffmpeg, I followed the guide you gave in the other thread: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

The only diff is adding --enable-shared to the configure line, to make it work with OpenCV.

I'm so close to getting everything working nicely, so any help getting over this last stumbling block would be great!

Regards,

Xav.

---

### Post by darkzerox on 2009-03-23
ffmpeg SVN-r18019
opencv 1644
Ubuntu 8.10 (kernel 2.6.27-11-generic)

You're getting a problem with xine? Or building OpenCV? Remember to build opencv with cmake. Otherwise, I eventually decided to disable xine and gstreamer for OpenCV. FFMPEG alone gives fewer errors & warnings (if you can get it working).

---

### Post by xavierda on 2009-03-24
> **darkzerox said:**
> ffmpeg SVN-r18019
opencv 1644
Ubuntu 8.10 (kernel 2.6.27-11-generic)

You're getting a problem with xine? Or building OpenCV? Remember to build opencv with cmake. Otherwise, I eventually decided to disable xine and gstreamer for OpenCV. FFMPEG alone gives fewer errors & warnings (if you can get it working).

Hi darkzerox, thanks for replying. The issue I reported above was related to compiling OpenCV against the latest SVN release of ffmpeg. I tried the revisions you specified on Ubuntu 8.04.2 and was able to compile OpeCV successfully, although there were some issues. And yes, I used the cmake method.

Have you tried any of the sample programs? Did cvtest and cxcoretest complete successfully? If you did an out-of-place build in the recommended release directory, these will be in release/bin. Were you able to run the lkdemo (requires webcam) sample okay? When I run the demo, the image comes up (I had to run it with sudo for anything to display, which is strange and hints at a driver issue) but will crash out at some indeterminate period later with a JPEG corruption error.

So OpenCV compiles, but I don't really trust it yet to do any development. The tests failing may just indicate instability in the lib in general and be nothing to worry about. I might follow this up on the OpenCV forum.

I'm in the process of trying your revisions again on a clean install of 8.10 and will see if I get the same results.

Xav.

---

### Post by mikecrowe2 on 2009-06-16
Hi Xav, I'm having the very same issue.
Did you manage to resolve the jpeg errors?

Thanks,
Mike

---

### Post by xavierda on 2009-06-17
> **mikecrowe2 said:**
> Hi Xav, I'm having the very same issue.
Did you manage to resolve the jpeg errors?

Thanks,
Mike

Hi Mike. For webcams that use the uvcvideo driver (such as some Logitech webcams) you should try and install the latest version from the [LinuxTV V4L-DVB]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers") repo.

That worked a treat for the 9000 Pro. Since then, I have switched to the Sphere AF, which seems better supported.

Regards,

Xav.

---

### Post by mikecrowe2 on 2009-06-17
Thanks Xav. I'm still having the same issue with the latest version though on my Macbook's iSight.

I might try a different camera.

Thanks for your help,
Mike

---

### Post by jpoikela on 2009-06-30
> **darkzerox said:**
> Just an FYI in case anyone else runs into this problem, if you get the run-time error when trying to open a videp:



You need to sudo apt-get install libxine1 and/or xine-console. Not sure which one made it work (probably the former), but if not, try the latter. Took me a long time to figure this out.

Also, early tests seem to show fewer errors WITHOUT xine and gstreamer. FFMPEG seems to work better for opening videos, although I have yet to find a reliable way to get the number of frames in an AVI.

Thanks, darkzerox. libxine1 took me one step further! :)

I took a version tagged "latest_tested_snapshot" version 1795.

- I could not get opencv to compile --with-gstreamer. Maybe wrong version..?

- Python support also caused some problems (SWIG-generated files being out of date?) That I was able to correct manually.

---

