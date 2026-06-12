---
title: "WinFF Issue since upgrading to 10.04"
date: 2010-08-07
forum: Multimedia Software
---

### Post by jlabomb on 2010-08-07
I have had an issue with WINFF since 10.04. Nothing seems to work in it at all. I am trying to convert a OGV file to a mpg MPEG2 file using DVD NTSC HQ Wide-screen. The version of FFMPEG I have is 4:0.5.1-1ubuntu1. I have found some posts that to update FFMPEG but it did not help any so I went back to the original. I really need to get this working, I do a lot of video work and am lost without WINFF.

This is what I get in the terminal


FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
[theora @ 0xf90890]7 bits left in packet 82
Input #0, ogg, from '/home/james/Videos/rip/Precious.ogv':
  Duration: 01:49:53.45, start: 0.000000, bitrate: 3222 kb/s
    Stream #0.0: Video: theora, yuv420p, 720x480, PAR 32:27 DAR 16:9, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: vorbis, 44100 Hz, stereo, s16, 128 kb/s
Output #0, dvd, to '/home/james/Desktop/MP3 Player/Precious.mpg':
    Stream #0.0: Video: mpeg2video (hq), yuv420p, 720x480 [PAR 32:27 DAR 16:9], q=2-31, 8000 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[theora @ 0xf90890]7 bits left in packet 82
Press [q] to stop encoding
Segmentation fault0 q=2.0 size=       0kB time=13.71 bitrate=   0.0kbits/s    
Press Enter to Continue


Any ideas?

---

### Post by kostkon on 2010-08-08
First, you could try to reinstalling it, thus give:
```
sudo apt-get install ffmpeg --reinstall
```
afterwards, give the following to make sure that you have the unrestricted versions of the following libs:
```
sudo apt-get install libavcodec-extra-52 libavdevice-extra-52 libavfilter-extra-0 libavformat-extra-52 libavutil-extra-49 libpostproc-extra-51 libswscale-extra-0
```
Then, try to do the conversion again.

A good option, after doing the above, would be to get the version of FFMPEG provided by the [*Medibuntu* repo]("http://medibuntu.org/"). Thus after adding the repo, open the update manager to update all the FFMPEG related packages.

---

### Post by jlabomb on 2010-08-08
I tried your suggestions with no success. Anything else I can try?

---

### Post by Rumpty on 2010-08-08
> **jlabomb said:**
> I tried your suggestions with no success. Anything else I can try?

Hello jlabomb. Bit of a challenge, this ffmpeg stuff! I have been trying to get it going with kdenlive, creating H264 files and all that, but I just can't get it to work.

One trouble is that after working through the suggestions in a long thread, you wonder if the ideas at the start of the thread, which might be many months ago, still apply?

Sorry that I'm no help - just moral support.

---

### Post by jlabomb on 2010-08-08
Yeah, I never had problem with it till 10.04. Hopefully someone will come across a solution. Thanks for the support.

---

### Post by FakeOutdoorsman on 2010-08-08
You could either provide a sample of the input that is causing the segmentation fault and I'll investigate it, or you could compile a recent version of FFmpeg, and if it crashes it may be worth reporting the crash to FFmpeg as a bug.

If you simply want to provide a sample, and your input is too large to conveniently upload, you can create a small sample. Open up Terminal, navigate to the directory containing *Precious.ogv* and enter:
```
dd if=Precious.ogv of=sample.ogv bs=1024 count=900
tar czvf sample.tar.gz sample.ogv
```
Now run *sample.ogv* through WinFF.  If it causes a crash then attach the file *sample.tar.gz* to your reply on this forum.  If it is something that you would rather not share then you can either PM it to me or just compile FFmpeg and see if a more recent version can handle this input.  You can basically cut and paste these instructions:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

After you follow that guide you can try re-encoding *Precious.ogv*.  You may have to edit your WinFF presets and change any instances of *kb* to *k*, such as *-b 800kb* to *-b 800k*.

---

### Post by Linuxforall on 2010-08-08
Upgrade to latest Winff via their repository, the instructions are at their site, then download and update the presets. Make sure medibuntu repos is on.

---

### Post by jlabomb on 2010-08-13
I think my current problem is just that file. When I upgraded to 10.04 at first I could not convert anything but now it is just that one file. I ripped it with Thoggen and I never had trouble before. I think I will just give up on that file since everything else is working in WinFF. Thanks for all the help.

---

