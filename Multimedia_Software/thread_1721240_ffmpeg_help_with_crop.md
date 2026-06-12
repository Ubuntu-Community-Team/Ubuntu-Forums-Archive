---
title: "ffmpeg help with crop"
date: 2011-04-04
forum: Multimedia Software
---

### Post by Dimoutlook on 2011-04-04
Hi to All

I'm really lost on how to crop a simple letterbox video, nothing so far has worked. I still have the black bars on the video. Would someone please look and see what I'm doing wrong!. I've included the output from ffmpeg below. The -ss and -t are for
just this test video.

Thanks to all who reply



FFmpeg version git-N-28506-g3660b5b, Copyright (c) 2000-2011 the FFmpeg developers  built on Mar 18 2011 08:56:46 with gcc 4.4.5
 configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb
--enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid
--enable-x11grab
  libavutil    50. 40. 0 / 50. 40. 0
  libavcodec   52.114. 0 / 52.114. 0
  libavformat  52.103. 0 / 52.103. 0
  libavdevice  52.  3. 0 / 52.  3. 0
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0


Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (60000/2002)
Input #0, mpeg, from 'VTS_02_1.VOB': Duration: 00:21:04.54, start: 0.026133, bitrate: 33518 kb/s Stream #0.0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x480 [PAR 32:27 DAR 16:9],7500 kb/s, 23.98 fps, 29.97 tbr, 90k tbn, 59.94 tbc     Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
[buffer @ 0x16d7ea0] w:720 h:480 pixfmt:yuv420p
[setdar @ 0x16dba70] a:16/9
[crop @ 0x16db090] w:720 h:480 -> w:720 h:480
[scale @ 0x16db800] w:720 h:480 fmt:yuv420p -> w:720 h:360 fmt:yuv420p flags:0xa0000004
[setdar @ 0x16dba70] w:720 h:360 -> dar:16/9 par:8/9
Output #0, avi, to 'output.avi':

ffmpeg -ss 00:00:01 -t 00:10:00 -i VTS_02_1.VOB -vcodec libxvid -b 1130k -r 23.970 -aspect 16:9 -s 720x480 -vf crop=in_w-0:in_h-2*60,scale=720:360 -sn -an -pass 1 -y output.avi

---

### Post by FakeOutdoorsman on 2011-04-04
[FFmpeg and 'Fist of Fury'](http://www.andrews-corner.org/fist.html) shows an interesting and effective method of cropping.

---

### Post by Dimoutlook on 2011-04-04
Thanks for the tip however that still gives a video where the hight is stretched really would like to use ffmpeg the command line is better than auto-GK

Dimoutlook

---

### Post by FakeOutdoorsman on 2011-04-04
Can you show your FFmpeg command and the complete terminal output?

---

