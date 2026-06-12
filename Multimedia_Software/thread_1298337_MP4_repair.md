---
title: "MP4 repair?"
date: 2009-10-22
forum: Multimedia Software
---

### Post by yester64 on 2009-10-22
Hi, i found out that one of my mp4 movies does not play but every other will.
Is there a way to repair the file?:confused:

---

### Post by FakeOutdoorsman on 2009-10-22
What does FFmpeg say about your file?
```
ffmpeg -i your_input_file_that_does_not_play.mp4
```
Replace *your_input_file_that_does_not_play.mp4* with the actual name of your broken MP4 file.  You would be surprised about how many people just enter my example command without changing the input file name.

---

### Post by yester64 on 2009-10-22
> **FakeOutdoorsman said:**
> What does FFmpeg say about your file?
```
ffmpeg -i your_input_file_that_does_not_play.mp4
```Replace *your_input_file_that_does_not_play.mp4* with the actual name of your broken MP4 file.  You would be surprised about how many people just enter my example command without changing the input file name.

It told me that 'moov atom' is not found. But strangely all other files work fine. Mmm..
i will try that command and say if it solved the problem. Thanks you already.

joerg@joerg-desktop:/media/sdb1/MP4/1$ ffmpeg -i myfile.mp4"
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
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x8ee8ac0]moov atom not found
myfile.mp4: Error while opening file

thats what came out

---

### Post by vinutux on 2009-10-23
Check what type codec are using it ...right click file > properties Audio/Video Tab

Is That xvid or divx This tool helps you **[DivFix ++ ]("http://divfixpp.sourceforge.net/")**

Download it for here [http://sourceforge.net/projects/divfixpp/files/]("http://sourceforge.net/projects/divfixpp/files/")

---

### Post by yester64 on 2009-10-23
Thats tag is empty. It only says unknown. ???
Let me check the file on the windows side.

---

### Post by FakeOutdoorsman on 2009-10-23
> **yester64 said:**
> It told me that 'moov atom' is not found. But strangely all other files work fine. Mmm..
i will try that command and say if it solved the problem. Thanks you already.

joerg@joerg-desktop:/media/sdb1/MP4/1$ ffmpeg -i myfile.mp4"
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
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x8ee8ac0]moov atom not found
myfile.mp4: Error while opening file

thats what came out

That's a new error for me.  I would guess that it is most likely a damaged file or perhaps a reference file where it is simply pointing to another file (from [[libav-user] moov atom not found](http://lists.mplayerhq.hu/pipermail/libav-user/2009-April/002829.html)).  Can MPlayer play this file?  Show the output of a simple FFmpeg conversion:
```
ffmpeg -i myfile.mp4 output.mp4
```
How big is this file?
```
ls -alh myfile.mp4
```

---

### Post by nero76 on 2011-04-20
> **yester64 said:**
> Hi, i found out that one of my mp4 movies does not play but every other will.
Is there a way to repair the file?:confused:

This tool can repair corrupt mp4 files:

[http://grauonline.de/cmsimple2_6/en/?Solutions:HD_Video_Repair_Utility](http://grauonline.de/cmsimple2_6/en/?Solutions:HD_Video_Repair_Utility)

To run in Ubuntu, we have tested the PC binary using 'wine' and it works (wine guiscript.exe). The tool requires a non-broken sample of the same camera. Using that sample file it can repair your broken movie file.

---

