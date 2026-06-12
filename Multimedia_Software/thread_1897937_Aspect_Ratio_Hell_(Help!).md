---
title: "Aspect Ratio Hell (Help!)"
date: 2011-12-20
forum: Multimedia Software
---

### Post by Jose Catre-Vandis on 2011-12-20
Hi

I have been sent a video in .mov format which I need to post on youtube and on our website.

I can see it is encoded to display in 16:9 aspect but in Windows Media Player (the player I know most people will use) and when uploaded to youtube it plays back in 4:3 format so the video is squeezed, and everything looks tall and thin.

What it should be like:
[ATTACH]209416[/ATTACH]
What it is like:
[ATTACH]209417[/ATTACH]

I have been using ffmpeg to try to re-encode the video to flv with "-s 480x270 -aspect 16:9" flags, but it still plays back squished. ffmpeg -i doesn't give back any PAR/DAR/SAR information.

How to encode to flv (or any format to upload to youtube) so that it will play back at the correct aspect ratio?

Output of ffmpeg -i:
```


ffmpeg.exe -i web.mov

FFmpeg version SVN-r18709, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-memalign-hack --prefix=/mingw --cross-prefix=i686-mingw32- --cc=ccache-i686-mingw32-gcc --target-os=mingw32 --arch=i686 --cpu=i686 --e
nable-avisynth --enable-gpl --enable-zlib --enable-bzlib --enable-libgsm --enable-libfaac --enable-libfaad --enable-pthreads --enable-libvorbis --enable-libtheo
ra --enable-libspeex --enable-libmp3lame --enable-libopenjpeg --enable-libxvid --enable-libschroedinger --enable-libx264
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.27. 0 / 52.27. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Apr 28 2009 04:04:42, gcc: 4.2.4

Seems stream 1 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'TLS-web.mov':
  Duration: 00:02:59.28, start: 0.000000, bitrate: 5221 kb/s
    Stream #0.0(eng): Audio: adpcm_ima_qt, 48000 Hz, stereo, s16
    Stream #0.1(eng): Video: h264, yuv420p, 480x360, 25 tbr, 25 tbn, 50 tbc
At least one output file must be specified
```

ffmpeg code line:
```
-vcodec flv -f flv -r 25 -s 480x270 -aspect 16:9 -b 900kb -g 160 -cmp dct -subcmp dct -mbd 2 -flags +aic+cbp+mv0+mv4 -trellis 1 -ac 2 -ar 44100 -ab 128kb
```

Thanks

---

