---
title: "Avconv Errors on Foscam Camera RTSP Stream (works in ffmpeg)"
date: 2014-11-03
forum: Multimedia Software
---

### Post by will55 on 2014-11-03
Hi All,
Thank you in advance for looking. I'm running an updated version of Trusty
```
No LSB modules are available.Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```

I'm trying to set up a process to pull screenshots from a Foscam FI9805 E. I know it should be doable in avconv and, after doing a bit of research I came up with the following avconv command:
```
avconv -i rtsp://<user>:<pass>@<local_ip>:88/videoMain -vframes 1 -r 1 -s 640x360 foscam1.jpg
```
This command generates a jpeg as expected, however the image is all grey. Avconv spits out a few errors (shown below) but it's tough sometimes to tell which is the relevant error in avconv.
```

avconv version 9.16-6:9.16-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Aug 10 2014 18:16:02 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
**Non-reference picture received and no reference available**
**[h264 @ 0x2077040] decode_slice_header error**
[rtsp @ 0x2072de0] Estimating duration from bitrate, this may be inaccurate
Guessed Channel Layout for  Input Stream #0.1 : mono
Input #0, rtsp, from 'rtsp://<redacted>:88/videoMain':
  Metadata:
    title           : IP Camera Video
    comment         : videoMain
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264 (Baseline), yuv420p, 1280x720, 30 fps, 90k tbn
    Stream #0.1: Audio: pcm_mulaw, 8000 Hz, mono, s16, 64 kb/s
Output #0, image2, to 'foscam1.jpg':
  Metadata:
    title           : IP Camera Video
    comment         : videoMain
    encoder         : Lavf54.20.4
    Stream #0.0: Video: mjpeg, yuvj420p, 640x360, q=2-31, 200 kb/s, 90k tbn, 1 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> mjpeg)
Press ctrl-c to stop encoding
**Non-reference picture received and no reference available**
**[h264 @ 0x20ef620] decode_slice_header error**
frame=    1 fps=  0 q=1.6 Lsize=       0kB time=1.00 bitrate=   0.0kbits/s    
video:4kB audio:0kB global headers:0kB muxing overhead -100.000000%

```

I was curious so tried to run the command in ffmpeg in Centos7
```


LSB Version:    :core-4.1-amd64:core-4.1-noarch:cxx-4.1-amd64:cxx-4.1-noarch:desktop-4.1-amd64:desktop-4.1-noarch:languages-4.1-amd64:languages-4.1-noarch:printing-4.1-amd64:printing-4.1-noarch
Distributor ID:    CentOS
Description:    CentOS Linux release 7.0.1406 (Core) 
Release:    7.0.1406
Codename:    Core

```
Here's the ffmpeg command (all I did was replace avconv with ffmpeg):
```
ffmpeg -i rtsp://<user>:<password>@<local_ip>:88/videoMain -vframes 1 -r 1 -s 640x360 foscam1.jpg
```
It worked! The "Decode Slice Header Error" and "Non-reference picture recieved and no reference available" errors did not appear in ffmpeg and the picture came out clearly w/o any artifacting even.
```


ffmpeg version 2.3.2 Copyright (c) 2000-2014 the FFmpeg developers
  built on Aug 25 2014 17:23:07 with gcc 4.8.2 (GCC) 20140120 (Red Hat 4.8.2-16)
  configuration: --prefix=/usr --bindir=/usr/bin --datadir=/usr/share/ffmpeg --incdir=/usr/include/ffmpeg --libdir=/usr/lib64 --mandir=/usr/share/man --arch=x86_64 --optflags='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector-strong --param=ssp-buffer-size=4 -grecord-gcc-switches -m64 -mtune=generic' --enable-bzlib --disable-crystalhd --enable-gnutls --enable-libass --enable-libcdio --enable-libdc1394 --disable-indev=jack --enable-libfreetype --enable-libgsm --enable-libmp3lame --enable-openal --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libsoxr --enable-libspeex --enable-libtheora --enable-libvorbis --enable-libv4l2 --enable-libx264 --enable-libxvid --enable-x11grab --enable-avfilter --enable-avresample --enable-postproc --enable-pthreads --disable-static --enable-shared --enable-gpl --disable-debug --disable-stripping --shlibdir=/usr/lib64 --enable-runtime-cpudetect
  libavutil      52. 92.100 / 52. 92.100
  libavcodec     55. 69.100 / 55. 69.100
  libavformat    55. 48.100 / 55. 48.100
  libavdevice    55. 13.102 / 55. 13.102
  libavfilter     4. 11.100 /  4. 11.100
  libavresample   1.  3.  0 /  1.  3.  0
  libswscale      2.  6.100 /  2.  6.100
  libswresample   0. 19.100 /  0. 19.100
  libpostproc    52.  3.100 / 52.  3.100
Guessed Channel Layout for  Input Stream #0.1 : mono
Input #0, rtsp, from 'rtsp://<redacted>@192.168.1.200:88/videoMain':
  Metadata:
    title           : IP Camera Video
    comment         : videoMain
  Duration: N/A, start: 0.000000, bitrate: 64 kb/s
    Stream #0:0: Video: h264 (Baseline), yuv420p, 1280x720, 90k tbr, 90k tbn, 180k tbc
    Stream #0:1: Audio: pcm_mulaw, 8000 Hz, 1 channels, s16, 64 kb/s
[swscaler @ 0x2425540] deprecated pixel format used, make sure you did set range correctly
Output #0, image2, to 'foscam1.jpg':
  Metadata:
    title           : IP Camera Video
    comment         : videoMain
    encoder         : Lavf55.48.100
    Stream #0:0: Video: mjpeg, yuvj420p, 640x360, q=2-31, 200 kb/s, 1 fps, 1 tbn, 1 tbc
    Metadata:
      encoder         : Lavc55.69.100 mjpeg
Stream mapping:
  Stream #0:0 -> #0:0 (h264 (native) -> mjpeg (native))
Press [q] to stop, [?] for help
frame=    1 fps=0.0 q=4.6 Lsize=N/A time=00:00:01.00 bitrate=N/A    
video:16kB audio:0kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: unknown

```

I've done my best to try and upgrade the h264 codecs available on my Ubuntu box it to no avail it seems. Based on the timing of the error (in the output) I'm thinking that avconv is having trouble with decoing the h264 stream rather than encoding to jpg. The only thing I see different in the printouts (between avconv and ffmpeg) is that avconv lists an fps of 30 while ffmpeg doesn't list an fps at all. If it is an output issue I can see that avconv uses Lavf54.20.4 while ffmpeg uses Lavf55.40.100. Additionally ffmpeg lists Lavc55.69.100 as it's jpeg encoder while avconv does not have a similar line. I have tried to make sure that avconv was fairly updated using "apt-get" but I could have easily missed a package.

Anyways, I'm hoping someone might be able to suggest a path for me. Appreciate any help you can give.

---

### Post by andrew.46 on 2014-11-03
Perhaps stick with FFmpeg:

Compile FFmpeg on Ubuntu, Debian, or Mint
[https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)

The tide seems to be slowly turning against libav / avconv anyway.....

---

### Post by will55 on 2014-11-03
That did it! FFmpeg on Ubuntu behaved as it did on Centos. Appreciate the suggestion. 
I did it via the method you linked (compile from source) but, for any future searchers [this thread]("http://ubuntuforums.org/showthread.php?t=2219550") lists a repo that includes ffmpeg.

---

### Post by andrew.46 on 2014-11-03
> **will55 said:**
> That did it! FFmpeg on Ubuntu behaved as it did on Centos. Appreciate the suggestion. 

Good to hear it all worked out :)

---

