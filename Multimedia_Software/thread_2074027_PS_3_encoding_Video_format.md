---
title: "PS 3 encoding Video format"
date: 2012-10-20
forum: Multimedia Software
---

### Post by petersk on 2012-10-20
The first format plays on my PS3 through mediatomb.  The second doesn't.  Does anyone have an idea why?  I'll re-mencoder the second to match, if I knew what the difference was.

Thanks in advanced.
Kurt
```

=========== FIRST ============
$ ffmpeg -i CuriousGeorge_Season1/Curious.George.S01E01.FliesAKite_FromScratch.DivX.avi 2>&1 /dev/null
ffmpeg version 0.7.6-4:0.7.6-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers
  built on Jun 12 2012 16:44:09 with gcc 4.6.1
  configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[mpeg4 @ 0xfaa360] Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 29.97 (30000/1001)
Input #0, avi, from 'CuriousGeorge_Season1/Curious.George.S01E01.FliesAKite_FromScratch.DivX.avi':
  Duration: 00:25:45.87, start: 0.000000, bitrate: 959 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 624x480 [PAR 1:1 DAR 13:10], 29.97 fps, 29.97 tbr, 29.97 tbn, 30k tbc
    Metadata:
      title           : Main
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
    Metadata:
      title           : Audio
Unable to find a suitable output format for '/dev/null'

=========== SECOND ===========

$ ffmpeg -i CuriousGeorge_Season5/Curious.George.S05E01.MarcoSoundItOut_MonkeysDuckling.xvid.avi 2>&1 /dev/null
ffmpeg version 0.7.6-4:0.7.6-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers
  built on Jun 12 2012 16:44:09 with gcc 4.6.1
  configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
Input #0, avi, from 'CuriousGeorge_Season5/Curious.George.S05E01.MarcoSoundItOut_MonkeysDuckling.xvid.avi':
  Metadata:
    encoder         : MEncoder SVN-r1.0~rc3+svn20090426-4.4.3
  Duration: 00:25:25.25, start: 0.000000, bitrate: 2187 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 1904x1072 [PAR 1:1 DAR 119:67], PAR 137216:137207 DAR 2048:1153, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 209 kb/s
Unable to find a suitable output format for '/dev/null'

```
This might not be the right forum to ask, so if you want to point out the right one, that's cool too.

---

### Post by petersk on 2012-10-20
here's a little more infor from mencoder:
Seem like one difference is the bpp.  Could that really be the cause of not playing?  Any suggestions on how to get the two to match?
```

$ mplayer CuriousGeorge_Season1/Curious.George.S01E01.FliesAKite_FromScratch.DivX.avi -vo null -ao null -frames 0 2>&1 /dev/null | egrep "(VIDEO|AUDIO)"
VIDEO:  [DX50]  624x480  24bpp  29.970 fps  819.4 kbps (100.0 kbyte/s)
AUDIO: 48000 Hz, 2 ch, floatle, 128.0 kbit/4.17% (ratio: 16000->384000)
$ mplayer CuriousGeorge_Season5/Curious.George.S05E01.MarcoSoundItOut_MonkeysDuckling.xvid.avi -vo null -ao null -frames 0 2>&1 /dev/null | egrep "(VIDEO|AUDIO)"
VIDEO:  [XVID]  1904x1072  12bpp  29.970 fps  1964.3 kbps (239.8 kbyte/s)
AUDIO: 48000 Hz, 2 ch, floatle, 209.6 kbit/6.82% (ratio: 26205->384000)

```

---

