---
title: "convert to 3gp (problem with ffmpeg)"
date: 2010-09-02
forum: Multimedia Software
---

### Post by Samic on 2010-09-02
hi
I've searched a lot to find a solution to convert files to 3gp format!
but it doesn't work!!
WinFF doesn't work because ffmpeg doesnt!
here is the output:
```

samic@F29:~/Desktop$ ffmpeg -i Bruce--PingPong.wmv -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -ab 32 -y clip.3gpFFmpeg version 0.6-4:0.6-2ubuntu2~ppa1~lucid1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jul 17 2010 20:55:23 with gcc 4.4.3
  configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version='4:0.6-2ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version='4:0.6-2ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'Bruce--PingPong.wmv':
  Metadata:
    WMFSDKVersion   : 9.00.00.4503
    WMFSDKNeeded    : 0.0.0.0000
    IsVBR           : 0
    title           : lizn&#261;wszy funiaste.net
    author          : 
    copyright       : 
    comment         : 
  Duration: 00:01:12.88, start: 5.000000, bitrate: 548 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, 2 channels, s16, 64 kb/s
    Stream #0.1: Video: wmv3, yuv420p, 320x240, 25 tbr, 1k tbn, 1k tbc
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'mp3'
samic@F29:~/Desktop$ 

```

I installed the last ffmpeg and _[all thing which is in this tutorial]("http://ubuntuforums.org/showthread.php?t=1117283")_!!

---

### Post by andrew.46 on 2010-09-02
Hi Samic,

I can see a couple of problems:

[LIST]
[*]The first is that your FFmpeg appears to be at least in part courtesy of a PPA rather than a result of the FakeOutdoorsman's guide. Have you added a PPA at some stage that has given you some FFmpeg packages?
[*]A 3gp container would not normally hold mp3 sound, usually there would be either amr or aac sound with aac usually the better choice in terms of sound quality.
[*]You have made some errors with your mp3 syntax, it should normally be *-acodec **[COLOR="Red"]libmp3lame[/COLOR]** * and *-ab 32[COLOR="Red"]k[/COLOR]*, but as I have mentioned mp3 is probably not the best choice here.
[/LIST]

Can I ask why the choice of 3gp? I presume that you are trying to encode for use on a mobile phone or similar device.

Andrew

---

### Post by Samic on 2010-09-02
Hi Andrew and thanks for your response

I used a code from here:
_[http://forum.ubuntu.ir/index.php/topic,347.0.html](http://forum.ubuntu.ir/index.php/topic,347.0.html)_
It's in my language (Farsi) but you know the commands! (or with a bad translation you can _[see this!]("http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=fa&tl=en&u=http%3A%2F%2Fforum.ubuntu.ir%2Findex.php%2Ftopic%2C347.0.html")_)

also I used the things you suggested (I don't know if I used them correctly):
```

samic@F29:~/Desktop$ ffmpeg -i Bruce--PingPong.wmv -s qcif -vcodec h263 -acodec libmp3lam -ac 1 -ar 8000 -ab 32k -y clip.3gp

FFmpeg version 0.6-4:0.6-2ubuntu2~ppa1~lucid1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jul 17 2010 20:55:23 with gcc 4.4.3
  configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version='4:0.6-2ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version='4:0.6-2ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'Bruce--PingPong.wmv':
  Metadata:
    WMFSDKVersion   : 9.00.00.4503
    WMFSDKNeeded    : 0.0.0.0000
    IsVBR           : 0
    title           : lizn&#261;wszy funiaste.net
    author          : 
    copyright       : 
    comment         : 
  Duration: 00:01:12.88, start: 5.000000, bitrate: 548 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, 2 channels, s16, 64 kb/s
    Stream #0.1: Video: wmv3, yuv420p, 320x240, 25 tbr, 1k tbn, 1k tbc
Unknown encoder 'libmp3lam'




samic@F29:~/Desktop$ ffmpeg -i Bruce--PingPong.wmv -s qcif -vcodec h263 -acodec amr -ac 1 -ar 8000 -ab 32k -y clip.3gp

FFmpeg version 0.6-4:0.6-2ubuntu2~ppa1~lucid1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jul 17 2010 20:55:23 with gcc 4.4.3
  configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version='4:0.6-2ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version='4:0.6-2ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'Bruce--PingPong.wmv':
  Metadata:
    WMFSDKVersion   : 9.00.00.4503
    WMFSDKNeeded    : 0.0.0.0000
    IsVBR           : 0
    title           : lizn&#261;wszy funiaste.net
    author          : 
    copyright       : 
    comment         : 
  Duration: 00:01:12.88, start: 5.000000, bitrate: 548 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, 2 channels, s16, 64 kb/s
    Stream #0.1: Video: wmv3, yuv420p, 320x240, 25 tbr, 1k tbn, 1k tbc
Unknown encoder 'amr'




samic@F29:~/Desktop$ ffmpeg -i Bruce--PingPong.wmv -s qcif -vcodec h263 -acodec aac -ac 1 -ar 8000 -ab 32k -y clip.3gp

FFmpeg version 0.6-4:0.6-2ubuntu2~ppa1~lucid1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jul 17 2010 20:55:23 with gcc 4.4.3
  configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version='4:0.6-2ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version='4:0.6-2ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'Bruce--PingPong.wmv':
  Metadata:
    WMFSDKVersion   : 9.00.00.4503
    WMFSDKNeeded    : 0.0.0.0000
    IsVBR           : 0
    title           : lizn&#261;wszy funiaste.net
    author          : 
    copyright       : 
    comment         : 
  Duration: 00:01:12.88, start: 5.000000, bitrate: 548 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, 2 channels, s16, 64 kb/s
    Stream #0.1: Video: wmv3, yuv420p, 320x240, 25 tbr, 1k tbn, 1k tbc
encoder 'aac' is experimental and might produce bad results.
Add '-strict experimental' if you want to use it.

samic@F29:~/Desktop$ 

```Also I attached my sources.list in case it helps!
thank you for your time and consideration
oh sorry I forgot! yes I want it for my mobile phone!

---

### Post by andrew.46 on 2010-09-02
Hi Samic,

I am always more than a little jealous of people who can speak more than one language :).

You would be best to sort out FFmpeg itself first. Concerning you sources.list it all looks reasonable although I suspect this has no place there:

```
deb http://wine.budgetdedicated.com/apt edgy main
```

and I would definitely comment that one out. There must be another PPA involved and perhaps you could look in */etc/apt/sources.list.d* and the culprit will be there.

It is then up to you, to transcode to mp3, aac, h263 the Ubuntu repository FFmpeg + the additions suggested by FakeOutdoorsman will suffice:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

but I suspect you will need to see the contents of */etc/apt/sources.list.d* first, and then decide which way to head...

When this is sorted out if your phone will take h263 video + aac in a 3gp container, and a lot of phones can do better than this now, something like the following will be what you are after:

```

ffmpeg -i Bruce--PingPong.wmv \
        -s qcif -vcodec h263 -b 200k \
        -acodec libfaac -ab 64k \
        -y clip.3gp

```

All the best,

Andrew

**PS** You left the 'e' off libmp3lame :).

---

### Post by Samic on 2010-09-02
Thank you very much but believe me! it doesn't work in any way!! it's making me crazy!! ](*,)
There must be a way! I'm not a bad person! I just want to have a clip in my mobile! that shouldn't be so hard!!

> 
samic@F29:~/Desktop$ sudo apt-get install ffmpeg libavcodec-extra-52Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffmpeg is already the newest version.
libavcodec-extra-52 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.




samic@F29:~/Desktop$ ffmpeg -i Bruce--PingPong.wmv -s qcif -vcodec h263 -acodec libmp3lame -ac 1 -ar 8000 -ab 32k -y clip.3gp
FFmpeg version 0.6-4:0.6-2ubuntu2~ppa1~lucid1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jul 17 2010 20:55:23 with gcc 4.4.3
  configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version='4:0.6-2ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version='4:0.6-2ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'Bruce--PingPong.wmv':
  Metadata:
    WMFSDKVersion   : 9.00.00.4503
    WMFSDKNeeded    : 0.0.0.0000
    IsVBR           : 0
    title           : lizn&#261;wszy funiaste.net
    author          : 
    copyright       : 
    comment         : 
  Duration: 00:01:12.88, start: 5.000000, bitrate: 548 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, 2 channels, s16, 64 kb/s
    Stream #0.1: Video: wmv3, yuv420p, 320x240, 25 tbr, 1k tbn, 1k tbc
[3gp @ 0x86a27e0]track 1: could not find tag, codec not currently supported in container
Output #0, 3gp, to 'clip.3gp':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0: Video: h263, yuv420p, 176x144, q=2-31, 200 kb/s, 25 tbn, 25 tbc
    Stream #0.1: Audio: libmp3lame, 8000 Hz, 1 channels, s16, 32 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Could not write header for output file #0 (incorrect codec parameters ?)





samic@F29:~/Desktop$ ffmpeg -i Bruce--PingPong.wmv \
>         -s qcif -vcodec h263 -b 200k \
>         -acodec libfaac -ab 64k \
>         -y clip.3gp
FFmpeg version 0.6-4:0.6-2ubuntu2~ppa1~lucid1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jul 17 2010 20:55:23 with gcc 4.4.3
  configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version='4:0.6-2ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version='4:0.6-2ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'Bruce--PingPong.wmv':
  Metadata:
    WMFSDKVersion   : 9.00.00.4503
    WMFSDKNeeded    : 0.0.0.0000
    IsVBR           : 0
    title           : lizn&#261;wszy funiaste.net
    author          : 
    copyright       : 
    comment         : 
  Duration: 00:01:12.88, start: 5.000000, bitrate: 548 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, 2 channels, s16, 64 kb/s
    Stream #0.1: Video: wmv3, yuv420p, 320x240, 25 tbr, 1k tbn, 1k tbc
Unknown encoder 'libfaac'

samic@F29:~/Desktop$ 

I don't know what to do about */etc/apt/sources.list.d*! there are many file! So I just zipped them all and attached! sorry!

BTW: you are so lucky that English is your first language! It's not important how much I study English I'll never be able to speak naturally and good and others should tolerate my speaking! sad! but true!

---

### Post by mc4man on 2010-09-02
What a total pita it is reading the output from a recent shared debian packaged ffmpeg. (wish that could be cleaned up.

The configure for your ffmpeg appears to be this
> configuration: --extra-version='4:0.6-2ubuntu2~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
Don't see any --enable-libfaac or --enable-libmp3lame either
(not to sure you can put mp3 in a 3gp container anyway
*Appears *to be either a rather crappy build.. or you need to install *the actual extra versions of the ffmpeg libs from it - check in synaptic*

why not just build a static, standalone ffmpeg and use that for encoding
[FakeOutdoorsman's guide]("http://ubuntuforums.org/showthread.php?t=786095") in Tips and Tutorials should serve you well

For comparison here's the configure for a basic new shared debian packaged ffmpeg I built for maverick  from a current svn source

> configuration: --extra-version='4:0.6-2ubuntu4' --prefix=/usr --enable-avfilter --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvpx --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --enable-libmp3lame  --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libxvid --enable-libx264 --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-shared --disable-static

---

### Post by Samic on 2010-09-02
thanks mc4man,
_[I did as you said]("http://ubuntuforums.org/showthread.php?t=786095")_. (It was like a screen-saver running for ever!)

after that I tried again and I got this:

> samic@F29:~/Desktop$ ffmpeg -i Bruce--PingPong.wmv -s qcif -vcodec h263 -acodec libmp3lame -ac 1 -ar 8000 -ab 32k -y clip.3gp
FFmpeg version SVN-r25025, Copyright (c) 2000-2010 the FFmpeg developers
  built on Sep  2 2010 21:11:12 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.24. 0 / 50.24. 0
  libavcore      0. 6. 0 /  0. 6. 0
  libavcodec    52.87. 0 / 52.87. 0
  libavformat   52.78. 3 / 52.78. 3
  libavdevice   52. 2. 1 / 52. 2. 1
  libavfilter    1.38. 1 /  1.38. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'Bruce--PingPong.wmv':
  Metadata:
    WMFSDKVersion   : 9.00.00.4503
    WMFSDKNeeded    : 0.0.0.0000
    IsVBR           : 0
    title           : lizn&#261;wszy funiaste.net
    author          : 
    copyright       : 
    comment         : 
  Duration: 00:01:12.88, start: 5.000000, bitrate: 548 kb/s
    Stream #0.0(pol): Audio: wmav2, 44100 Hz, 2 channels, s16, 64 kb/s
    Stream #0.1(pol): Video: wmv3, yuv420p, 320x240, 524 kb/s, 25 tbr, 1k tbn, 1k tbc
[buffer @ 0x98f8df0] w:320 h:240 pixfmt:yuv420p
[scale @ 0x98f5770] w:320 h:240 fmt:yuv420p -> w:176 h:144 fmt:yuv420p flags:0xa0000004
[3gp @ 0x98d0200] track 1: could not find tag, codec not currently supported in container
Output #0, 3gp, to 'clip.3gp':
  Metadata:
    encoder         : Lavf52.78.3
    Stream #0.0(pol): Video: h263, yuv420p, 176x144, q=2-31, 200 kb/s, 25 tbn, 25 tbc
    Stream #0.1(pol): Audio: libmp3lame, 8000 Hz, 1 channels, s16, 32 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Could not write header for output file #0 (incorrect codec parameters ?)
samic@F29:~/Desktop$ 

Seriously what's wrong with this program??!!

(also I wish if a guy wants to cleanup packages that you said, he makes a friendly, reasonable program for converting files first! something like Xilisoft vedio converter! ahhh!)

---

### Post by mc4man on 2010-09-02
> Seriously what's wrong with this program??!
Nothing, maybe stop trying to use mp3 audio
(don't have a cell phone nor use 3gp but see no indication that you can use mp3

in your last output - plain as day 
> [3gp @ 0x98d0200] track 1: could not find tag, codec not currently supported in container

---

### Post by FakeOutdoorsman on 2010-09-02
> **Samic said:**
> Seriously what's wrong with this program??!!
.3gp doesn't accept mp3 audio.  Try andrew.46's command from [post 4](http://ubuntuforums.org/showpost.php?p=9796427&postcount=4).

[QUOTE=Samic]BTW: you are so lucky that English is your first language![/QUOTE]
Your English is fine.

---

### Post by Samic on 2010-09-02
WOW! FINALLY! :D

Thank you guys very much!! andrew.46 , mc4man and FakeOutdoorsman
you are all really kind to help

to sum up for anyone who may have this problem later:
building a static, standalone ffmpeg from this link
_[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)_
and then using this coomand helps to converting to 3gp
```
ffmpeg -i Bruce--PingPong.wmv \
        -s qcif -vcodec h263 -b 200k \
        -acodec libfaac -ab 64k \
        -y clip.3gp

```Thanks again ):P
Btw: If you are curious about "Bruce--PingPong.wmv" it was this: (of course I didn't want it for just this file!)
[http://www.youtube.com/watch?v=9QHslHpK4-Q](http://www.youtube.com/watch?v=9QHslHpK4-Q)

---

### Post by mc4man on 2010-09-02
Glad you got it sorted - one small thing
If you need to post any terminal outputs in the future as the above ones then put them in a quote box instead of a code box.
The code box sometimes makes reading the terminal output a bit difficult on many screens.

*use a code box when showing an actual command to be run or one you did run (just the command.

---

### Post by Samic on 2010-09-02
I wish you had said that before! but I'll do it from now on. thanks

---

### Post by mc4man on 2010-09-02
> I wish you had said that before!
I was having a bit of a 'brain lock', didn't notice at first you were using code boxes.
If you're curious about the diff. you can go and edit one of the posts
(you just remove the [....] and [/....] and then quote it
where .... is CODE

---

### Post by andrew.46 on 2010-09-02
Hi Samic,

> **Samic said:**
> WOW! FINALLY! :D

Thank you guys very much!! andrew.46 , mc4man and FakeOutdoorsman
you are all really kind to help

The joys of the Northern / Southern timezone differences, I was hoping the whole thing would be sorted out while I slept :).

My only suggestions are that you should really have a long hard look at all of those PPAs and see if they are really all necessary for your system. The possibility for conflicting packages is quite high... Also I am not much of a phone buff but many newer phones will take h264 video and aac sound in an mp4 container and this will be a lot nicer than h263 + aac in a 3gp container. Perhaps have a look at the documentation with your phone?

All the very best,

Andrew

---

### Post by Samic on 2010-09-03
> **mc4man said:**
> I was having a bit of a 'brain lock', didn't notice at first you were using code boxes.
If you're curious about the diff. you can go and edit one of the posts
(you just remove the [....] and [/....] and then quote it
where .... is CODE

ooo! I did as you said and now I think quote in much worse!!
when you use code, your post will not be longer than a specific amount! but with quote, it will be long as the text! this causes a very long threads that your finger will hurt when you scroll them with your mouse wheel!!;)

---

### Post by andrew.46 on 2010-09-08
Hi Samic,

Which reminds me, if you ever wanted to see what amr sound is like your copy of FFmpeg will now do the following:

```

ffmpeg -i Bruce--PingPong.wmv \
       -s qcif -vcodec h263 -r 25 -b 200k \
       -acodec libopencore_amrnb -ac 1 -ar 8000 -ab 12200 \
        Bruce--PingPong.3gp

```

I used to use something similar for my wife's old mobile phone and just testing this syntax today I can see that the sound produced by FFmpeg and libopencore amr has improved greatly over the last little while...

Andrew

---

### Post by Samic on 2010-09-08
Thanks Andrew
I'll try it
):P

---

