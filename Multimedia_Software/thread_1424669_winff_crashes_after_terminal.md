---
title: "winff crashes after terminal"
date: 2010-03-08
forum: Multimedia Software
---

### Post by sevenX on 2010-03-08
I am fairly new to linux and am having a problem with winff.  I am trying to convert movies to mpeg4 or more specifically formatted to play on my blackberry curve.  I followed installation guide from this tutorial [http://ubuntuforums.org/showthread.php?t=786095&highlight=winff](http://ubuntuforums.org/showthread.php?t=786095&highlight=winff). Everything installed and the program works but when I add a file and pick presets and hit convert the terminal pops up and says the following:

brice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
Input #0, avi, from '/home/colin/Videos/Kvai-Lynn's/Ni Hao, Kai-Lan - Kai-lan's Campout':
  Duration: 00:24:14.04, start: 0.000000, bitrate: 1126 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
Unknown encoder 'libfaac'
Press Enter to Continue

So I press Enter and the terminal closes, than... nothing happens just staring at the winff screen.


I really have no idea where to go with this.  I found a link from the forums earlier on these common crashes but cant seem to find it again.  If anyone can help point me in the right direction or help me solve the problem it would be greatly appriciated.

---

### Post by FakeOutdoorsman on 2010-03-08
> **sevenX said:**
> I followed installation guide from this tutorial [http://ubuntuforums.org/showthread.php?t=786095&highlight=winff](http://ubuntuforums.org/showthread.php?t=786095&highlight=winff). Everything installed and the program works but when I add a file and pick presets and hit convert the terminal pops up and says the following:
```
...
configuration: --extra-version=[color=#FF0000]4:0.5+svn20090706-2ubuntu2[/color]
...
```

This shows that you are using FFmpeg from the repository and not a FFmpeg that you compiled yourself.  Due to license issues, the repository FFmpeg for Karmic does not support encoding to AAC audio with *libfaac* as you are trying to do.  You can either compile FFmpeg as you said you did, or use the **libavcodec-extra-52** package supplied by the Medibuntu repository as described here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

If you followed the FFmpeg compilation guide that you linked to, then the first step should have removed the repository FFmpeg.  Or perhaps you did compile and install FFmpeg correctly, but maybe you re-installed the version from the FFmpeg repository.

---

