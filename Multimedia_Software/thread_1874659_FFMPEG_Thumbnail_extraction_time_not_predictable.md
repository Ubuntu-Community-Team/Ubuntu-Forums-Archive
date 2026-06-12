---
title: "FFMPEG Thumbnail extraction time not predictable"
date: 2011-11-03
forum: Multimedia Software
---

### Post by buri on 2011-11-03
Hi,

I use ffmpeg to extract thumbnails from a video. Here's the command I use:
/usr/bin/ffmpeg -i gource.mp4 -vframes 1 -an -s 140x140 -ss 295 pic1.png

The problem I have: The time it takes to extract a frame 500s into the video is about double the time it takes to extract a frame at 295s.

Here's the time as reported by the 'time' command (see below):
295s -> 0m17.643s
500s -> 0m28.595s

Why can't ffmpeg just seek to the given point and extract the frame. I was expecting that command would take the same time, no matter where the frame is extracted.

What can I do about it? I transcoded the video using the zencoder-cloud-service with default options. I could switch to an other format, but I don't know what option I should specify to get a "seekable" video...

Anybody familiar with that?

Thanks!
Erich


Ubuntu: Maverick
```

ffmpeg -version
FFmpeg version 0.6-4:0.6-2ubuntu6.2, Copyright (c) 2000-2010 the FFmpeg developers

```


Example:
```

time /usr/bin/ffmpeg -i /tmp/gource.mp4 -vframes 1 -an -s 140x140 -ss 295 /tmp/pic1.png
FFmpeg version 0.6-4:0.6-2ubuntu6.2, Copyright (c) 2000-2010 the FFmpeg developers
  built on Sep 16 2011 17:11:24 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 120.00 (120/1) -> 59.94 (60000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/tmp/gource.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
  Duration: 00:09:57.56, start: 0.000000, bitrate: 804 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 854x480 [PAR 1:1 DAR 427:240], 802 kb/s, 60 fps, 59.94 tbr, 60 tbn, 120 tbc
Output #0, image2, to '/tmp/pic1.png':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0(und): Video: png, rgb24, 140x140 [PAR 137:77 DAR 137:77], q=2-31, 200 kb/s, 90k tbn, 59.94 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=    1 fps=  0 q=0.0 Lsize=      -0kB time=0.02 bitrate= -10.5kbits/s    its/s    
video:10kB audio:0kB global headers:0kB muxing overhead -100.217091%

real	0m17.643s
user	0m17.245s
sys	0m0.080s

```

```

time /usr/bin/ffmpeg -i /tmp/gource.mp4 -vframes 1 -an -s 140x140 -ss 500 /tmp/pic1.png
FFmpeg version 0.6-4:0.6-2ubuntu6.2, Copyright (c) 2000-2010 the FFmpeg developers
  built on Sep 16 2011 17:11:24 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 120.00 (120/1) -> 59.94 (60000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/tmp/gource.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
  Duration: 00:09:57.56, start: 0.000000, bitrate: 804 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 854x480 [PAR 1:1 DAR 427:240], 802 kb/s, 60 fps, 59.94 tbr, 60 tbn, 120 tbc
Output #0, image2, to '/tmp/pic1.png':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0(und): Video: png, rgb24, 140x140 [PAR 137:77 DAR 137:77], q=2-31, 200 kb/s, 90k tbn, 59.94 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=    1 fps=  0 q=0.0 Lsize=      -0kB time=0.02 bitrate= -10.5kbits/s    its/s    
video:8kB audio:0kB global headers:0kB muxing overhead -100.269509%

real	0m28.595s
user	0m27.646s
sys	0m0.132s

```

---

### Post by FakeOutdoorsman on 2011-11-04
> **buri said:**
> The problem I have: The time it takes to extract a frame 500s into the video is about double the time it takes to extract a frame at 295s.

Why can't ffmpeg just seek to the given point and extract the frame. I was expecting that command would take the same time, no matter where the frame is extracted.

The placement of the *-ss* option is important as the behavior changes depending if you apply it as an input option (before *-i input*) or as an output option (after *-i input*). A more [detailed explanation of -ss placement](http://ubuntuforums.org/showthread.php?p=10113019#post10113019).

> **buri said:**
> What can I do about it?
You can try moving *-ss* as an input option. It will be much faster, but may not give satisfactory results with your H.264 inputs. You could also try adding *-threads* as an input option to speed up decoding. An appropriate value for this option depends on your CPU.

A less optimal solution could be to use an input format that is more friendly to the "ss as an input option" method, but H.264 is hard to beat for all the other reasons. However, I've never heard of zencoder-cloud-service and not all encoders are equal.

---

### Post by buri on 2011-11-04
> 
The placement of the -ss option is important as the behavior changes depending if you apply it as an input option (before -i input) or as an output option (after -i input). A more detailed explanation of -ss placement.


I was not aware on that. The effect is stunning:

```

time /usr/bin/ffmpeg -i /tmp/gource.mp4 -vframes 1 -an -s 140x140 -ss 295 /tmp/pic1.png
real	0m18.252s
user	0m17.441s
sys	0m0.064s

```

```

time /usr/bin/ffmpeg -ss 295 -i /tmp/gource.mp4 -vframes 1 -an -s 140x140 /tmp/pic1.png
...
real	0m0.099s
user	0m0.084s
sys	0m0.012s

```

Awesome! That's more like what I was expecting! 

Thank you so much, it saved my day! :D

---

