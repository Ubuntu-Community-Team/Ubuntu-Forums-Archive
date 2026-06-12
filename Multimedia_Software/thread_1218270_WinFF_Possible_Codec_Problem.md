---
title: "WinFF Possible Codec Problem"
date: 2009-07-20
forum: Multimedia Software
---

### Post by rchar66 on 2009-07-20
I'm having a problem getting WinFF to convert any video file into any other video format. I get the following message regardless of what file I try to convert.

```
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

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (5994/125) -> 23.98 (24000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/richard/Videos/hdnation--0001--welcome--hd.h264.mp4':
  Duration: 00:19:33.84, start: 0.000000, bitrate: 1660 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 1280x720, 23.98 tbr, 23.98 tbn, 47.95 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16
    Stream #0.2(eng): Data: rtp  / 0x20707472
    Stream #0.3(eng): Data: rtp  / 0x20707472
Unable to parse option value "trell": undefined constant or missing (
Invalid value '+4mv+trell' for option 'flags'
Press Enter to Continue
```

This just started to happen when I upgraded to Jaunty (9.04).

Would installing 'libavcodec-unstripped-52' help?

This was suggested in another post I found and the person had a very similar error message like mine.

Any ideas?:confused:

Richard

---

### Post by rchar66 on 2009-07-20
bump

---

### Post by rchar66 on 2009-07-20
Does anyone have even a slight clue? I've been trying to figure this out for a while now with no luck.

I thought installing 'libavcodec-unstripped-52' might help, but upon investigating, it is already installed.

So, the search goes on for a cure!

---

### Post by timsdeepsky on 2009-07-20
I had this problem before....
Installing ffmpeg from source solved this for me....
[http://ubuntuforums.org/showthread.php?t=786095&highlight=unknown+encoder+libx264]("http://ubuntuforums.org/showthread.php?t=786095&highlight=unknown+encoder+libx264")
Hope this helps....
I also had to "lock"my ffmpeg after this as the updates were over writing things and giving me the same troubles later....

---

### Post by paul.gevers on 2009-07-21
> **rchar66 said:**
> 
This just started to happen when I upgraded to Jaunty (9.04).

This is the cause for the trouble. The Intrepid presets were for the older version of ffmpeg. Winff stores it's preset in your home folder: /home/<user>/.winff/presets.xml Unfortunately, we are not able to touch it there, as you might have created presets of your own. Removing that file should solve your problems.

If it does not help, feel free to ask again.

---

### Post by rchar66 on 2009-07-21
Thanks Paul,

I'll give that a try and then post back here with the results, if it works or not.

Richard

---

### Post by rchar66 on 2009-07-21
Paul,

Your suggestion worked!!!:D

Thank's alot for your help! You don't know how happy I am. I use WinFF a lot to convert files so I was really bummed when I started having a problem with it in 9.04.

Thanks again!

Richard

---

