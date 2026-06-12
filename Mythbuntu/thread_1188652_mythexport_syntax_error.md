---
title: "mythexport syntax error"
date: 2009-06-15
forum: Mythbuntu
---

### Post by bcg30506 on 2009-06-15
I am running mythbuntu 9.04 with mythexport 2.0-0ubuntu1 and can no longer export recordings without getting a syntax error in the log file.  The error in mythexport.log is:

June 15 22:38:32 mythbox /usr/bin/mythexport-daemon[6410]: Exporting /monolith/tmp/mythexport/FNC-Glenn_Beck--20090615165900.mp4
sh: Syntax error: "(" unexpected
June 15 22:38:32 mythbox /usr/bin/mythexport-daemon[6410]: ERROR: nice -n19 ffmpeg -i /monolith/tv/1046_20090615165900.mpg -y -an -v 1 -vcodec h264 -b 1700000 -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 400x300 -aspect 4:3 -f mp4 -pass 1 /dev/null FAILED/ at line 540 in /usr/bin/mythexport-daemon

It used to work and I changed nothing on purpose.  Maybe a weekly update broke something?  How can I get around this for it to start working again?  My ffmpeg version is 3:0.svn20090303-1ubuntu6.

---

### Post by rhpot1991 on 2009-06-22
> **bcg30506 said:**
> I am running mythbuntu 9.04 with mythexport 2.0-0ubuntu1 and can no longer export recordings without getting a syntax error in the log file.  The error in mythexport.log is:

June 15 22:38:32 mythbox /usr/bin/mythexport-daemon[6410]: Exporting /monolith/tmp/mythexport/FNC-Glenn_Beck--20090615165900.mp4
sh: Syntax error: "(" unexpected
June 15 22:38:32 mythbox /usr/bin/mythexport-daemon[6410]: ERROR: nice -n19 ffmpeg -i /monolith/tv/1046_20090615165900.mpg -y -an -v 1 -vcodec h264 -b 1700000 -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 400x300 -aspect 4:3 -f mp4 -pass 1 /dev/null FAILED/ at line 540 in /usr/bin/mythexport-daemon

It used to work and I changed nothing on purpose.  Maybe a weekly update broke something?  How can I get around this for it to start working again?  My ffmpeg version is 3:0.svn20090303-1ubuntu6.

Lets start off by running this by hand and seeing what happens:
```
/usr/bin/mythexport-daemon[6410]: ERROR: nice -n19 ffmpeg -i /monolith/tv/1046_20090615165900.mpg -y -an -v 1 -vcodec h264 -b 1700000 -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 400x300 -aspect 4:3 -f mp4 -pass 1 /dev/null 
```

I think the ( error is a false positive, but I'll double check on it as well.

---

### Post by bcg30506 on 2009-06-22
Here it is by hand:

```

$ nice -n19 ffmpeg -i /monolith/tv/1046_20090615165900.mpg -y -an -v 1 -vcodec h264 -b 1700000 -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^(1-qComp) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 400x300 -aspect 4:3 -f mp4 -pass 1 /dev/null
-bash: syntax error near unexpected token `('

```

and here it is if I escape the parens:

```

$ nice -n19 ffmpeg -i /monolith/tv/1046_20090615165900.mpg -y -an -v 1 -vcodec h264 -b 1700000 -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq blurCplx^\(1-qComp\) -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 400x300 -aspect 4:3 -f mp4 -pass 1 /dev/null
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

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mpeg, from '/monolith/tv/1046_20090615165900.mpg':
  Duration: 00:20:30.72, start: 0.312400, bitrate: 4961 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 6000 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 384 kb/s
Invalid value '1' for option 'loop'

```

---

