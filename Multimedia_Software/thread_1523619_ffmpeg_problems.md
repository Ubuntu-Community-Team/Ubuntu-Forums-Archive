---
title: "ffmpeg problems"
date: 2010-07-03
forum: Multimedia Software
---

### Post by kung fu buntu on 2010-07-03
I used to have a working copy of ffmpeg, but after a few upgrades it seems it got broken.


> ffmpeg -f x11grab -s 1280x1024 -r 30 -b 100k -bf 2 -g 300 -i $DISPLAY.0 -aspect 1280:1024 -sameq   -an -vcodec libxvid  MyScreencast.avi
...
[libxvid @ 0x13c4d60]Invalid pixel aspect ratio 0/1
Video encoding failed
I also tried using 1.25 for the aspect ratio, but got the same error message.

If I try to use x264...
> ffmpeg -f x11grab -s 1280x1024 -r 30 -b 100k -bf 2 -g 300 -i $DISPLAY.0 -aspect 1280:1024 -sameq   -an -vcodec libx264  MyScreencast.avi
...
[libx264 @ 0x765d60]broken ffmpeg default settings detected
[libx264 @ 0x765d60]use an encoding preset (vpre)             
  Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height


> $ ffmpeg
FFmpeg version SVN-r23386, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun  3 2010 11:33:42 with gcc 4.4.4
  configuration: --enable-libdc1394 --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --enable-avfilter-lavf --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --enable-libvpx --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
  libavutil     50.16. 0 / 50.16. 0
  libavcodec    52.73. 0 / 52.73. 0
  libavformat   52.67. 0 / 52.67. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Hyper fast Audio and Video encoder



Any idea on how can I fix this?

BTW, I'm using debian with debian-multimedia packages.

---

### Post by FakeOutdoorsman on 2010-07-04
You need to add a preset when using libx264, such as *-vpre lossless_ultrafast*.  Have you seen this guide?

[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026)

Gives excellent results.

---

