---
title: "ffmpeg pixel aspect errors"
date: 2014-03-10
forum: Multimedia Software
---

### Post by Langstracht on 2014-03-10
I am trying to convert a video from .m4v to a reduced size .avi and ffmpeg is not co-operating.

I really wanted 400x240 (the screen size of the device) but "I think" 400x226 is the correct aspect ratio.

So, in response to:

```
ffmpeg -i movie1.m4v -s 400x226 movie1.avi
```

after screens full of data I get:

```
[buffer @ 0x9ea9d00] w:720 h:480 pixfmt:yuv420p
[scale @ 0x9e9eb80] w:720 h:480 fmt:yuv420p -> w:400 h:226 fmt:yuv420p flags:0x4
[mpeg4 @ 0x9e9f300] Invalid pixel aspect ratio 96389/96000, limit is 255/255
Output #0, avi, to 'sum.avi':
    Stream #0.0(und): Video: mpeg4, yuv420p, 400x226 [PAR 96389:96000 DAR 853:480], q=2-31, 200 kb/s, 90k tbn, 90k tbc
    Metadata:
      creation_time   : 2014-01-29 23:40:24
    Stream #0.1(eng): Audio: mp2, 48000 Hz, mono, s16, 64 kb/s
    Metadata:
      creation_time   : 2014-01-29 23:40:24
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

And then ffmpeg abends.

Does anyone know what is, or I am doing, wrong here.  Appreciate any help.

TIA

---

### Post by FakeOutdoorsman on 2014-03-10
Please include the complete ffmpeg console output (or at least the first ~50 lines and the last ~50 lines) and not just a selection.

---

### Post by Langstracht on 2014-03-11
```

ffmpeg version 0.7.6-4:0.7.6-0ubuntu0.11.10.3, Copyright (c) 2000-2011 the Libav developers
  built on Jan 24 2013 19:25:26 with gcc 4.6.1
  configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.3' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.3' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avcodec     configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.3' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avformat    configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.3' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avdevice    configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.3' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avfilter    configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.3' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  swscale     configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.3' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  postproc    configuration: --extra-version='4:0.7.6-0ubuntu0.11.10.3' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x83d62a0] max_analyze_duration reached

Seems stream 0 codec frame rate differs from container frame rate: 180000.00 (180000/1) -> 90000.00 (180000/2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'movie1.m4v':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isomavc1
    creation_time   : 2014-01-29 23:40:24
    encoder         : HandBrake rev0 2013051899
  Duration: 02:10:08.61, start: 0.000000, bitrate: 1354 kb/s
    Chapter #0.0: start -0.083411, end 103.002900
    Metadata:
      title           : Chapter 1
    Chapter #0.1: start 103.002900, end 368.267900
    Metadata:
      title           : Chapter 2
    Chapter #0.2: start 368.267900, end 685.968622
    Metadata:
      title           : Chapter 3
    Chapter #0.3: start 685.968622, end 990.222567
    Metadata:
      title           : Chapter 4
    Chapter #0.4: start 990.222567, end 1171.403567
    Metadata:
      title           : Chapter 5
    Chapter #0.5: start 1171.403567, end 1382.364322
    Metadata:
      title           : Chapter 6
    Chapter #0.6: start 1382.364322, end 1515.130289
    Metadata:
      title           : Chapter 7
    Chapter #0.7: start 1515.130289, end 1826.274456
    Metadata:
      title           : Chapter 8
    Chapter #0.8: start 1826.274456, end 2253.651400
    Metadata:
      title           : Chapter 9
    Chapter #0.9: start 2253.651400, end 2450.848400
    Metadata:
      title           : Chapter 10
    Chapter #0.10: start 2450.848400, end 2692.589900
    Metadata:
      title           : Chapter 11
    Chapter #0.11: start 2692.589900, end 2922.703122
    Metadata:
      title           : Chapter 12
    Chapter #0.12: start 2922.703122, end 3176.156322
    Metadata:
      title           : Chapter 13
    Chapter #0.13: start 3176.156322, end 3357.971289
    Metadata:
      title           : Chapter 14
    Chapter #0.14: start 3357.971289, end 3579.027467
    Metadata:
      title           : Chapter 15
    Chapter #0.15: start 3579.027467, end 3825.156689
    Metadata:
      title           : Chapter 16
    Chapter #0.16: start 3825.156689, end 4159.941133
    Metadata:
      title           : Chapter 17
    Chapter #0.17: start 4159.941133, end 4512.009522
    Metadata:
      title           : Chapter 18
    Chapter #0.18: start 4512.009522, end 4791.121689
    Metadata:
      title           : Chapter 19
    Chapter #0.19: start 4791.121689, end 5042.205856
    Metadata:
      title           : Chapter 20
    Chapter #0.20: start 5042.205856, end 5377.407389
    Metadata:
      title           : Chapter 21
    Chapter #0.21: start 5377.407389, end 5817.146689
    Metadata:
      title           : Chapter 22
    Chapter #0.22: start 5817.146689, end 5957.620356
    Metadata:
      title           : Chapter 23
    Chapter #0.23: start 5957.620356, end 6178.040556
    Metadata:
      title           : Chapter 24
    Chapter #0.24: start 6178.040556, end 6452.948522
    Metadata:
      title           : Chapter 25
    Chapter #0.25: start 6452.948522, end 6703.648967
    Metadata:
      title           : Chapter 26
    Chapter #0.26: start 6703.648967, end 6868.313467
    Metadata:
      title           : Chapter 27
    Chapter #0.27: start 6868.313467, end 7094.539467
    Metadata:
      title           : Chapter 28
    Chapter #0.28: start 7094.539467, end 7449.777689
    Metadata:
      title           : Chapter 29
    Chapter #0.29: start 7449.777689, end 7661.822856
    Metadata:
      title           : Chapter 30
    Chapter #0.30: start 7661.822856, end 7808.594467
    Metadata:
      title           : Chapter 31
    Stream #0.0(und): Video: h264 (Main), yuv420p, 720x480 [PAR 853:720 DAR 853:480], 1202 kb/s, 23.98 fps, 90k tbr, 90k tbn, 180k tbc
    Metadata:
      creation_time   : 2014-01-29 23:40:24
    Stream #0.1(eng): Audio: aac, 48000 Hz, mono, s16, 146 kb/s
    Metadata:
      creation_time   : 2014-01-29 23:40:24
    Stream #0.2(und): Subtitle: text / 0x74786574
    Metadata:
      creation_time   : 2014-01-29 23:40:24
[buffer @ 0x83e6d00] w:720 h:480 pixfmt:yuv420p
[scale @ 0x83dbb80] w:720 h:480 fmt:yuv420p -> w:400 h:226 fmt:yuv420p flags:0x4
[mpeg4 @ 0x83dc300] Invalid pixel aspect ratio 96389/96000, limit is 255/255
Output #0, avi, to 'movie1.avi':
    Stream #0.0(und): Video: mpeg4, yuv420p, 400x226 [PAR 96389:96000 DAR 853:480], q=2-31, 200 kb/s, 90k tbn, 90k tbc
    Metadata:
      creation_time   : 2014-01-29 23:40:24
    Stream #0.1(eng): Audio: mp2, 48000 Hz, mono, s16, 64 kb/s
    Metadata:
      creation_time   : 2014-01-29 23:40:24
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

---

### Post by FakeOutdoorsman on 2014-03-11
You're using a buggy, fake so-called "ffmpeg" from a fork. Try a recent build of the real ffmpeg from FFmpeg. You can download it via the [FFmpeg Download](http://ffmpeg.org/download.html#LinuxBuilds) page.

Or just do this:
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
tar xzvf ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
```

Then run it (notice the **./** before the ffmpeg):
```
./ffmpeg -i movie1.m4v -s 400x226 movie1.avi
```
[list]
[*]Why 400x226?
[*]Why AVI? It's a dated container, and others are usually better choices.
[*]You can use the scale filter to resize the output. It has the advantage of calculating the width or height for you while preserving the aspect, so you only need to give it one dimension (this will result in 400x267): ```
./ffmpeg -i movie1.m4v -vf scale=400:-1 movie1.avi
```
[/list]

---

### Post by Langstracht on 2014-03-12
> You're using a buggy, fake so-called "ffmpeg" from a fork. Try a recent build of the real ffmpeg from FFmpeg. You can download it via the FFmpeg Download page.

Hmmm.  Been using it without a problem until "now" ...

> Or just do this:

```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
tar xzvf ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
```

Did.   And worked fine.

> Then run it (notice the ./ before the ffmpeg):

```
./ffmpeg -i movie1.m4v -s 400x226 movie1.avi
```

Also did this ... and it also worked fine.  Except, there IS a problem with the audio.  Which is stuttering.  Could be a player problem I suppose.

> Why 400x226?

The, increasingly aging, device has a screen size of 400x240.  I thought I read that 400x226 was a "standard" size.

> Why AVI? It's a dated container, and others are usually better choices.

But, to date .avi, has played just fine on this increasingly aging device.  It would be a bit of a pain to do a conversion and then find that the device doesn't support it.

> You can use the scale filter to resize the output. It has the advantage of calculating the width or height for you while preserving the aspect, so you only need to give it one dimension (this will result in 400x267):

```
./ffmpeg -i movie1.m4v -vf scale=400:-1 movie1.avi
```

Tried to do this using height rather than width and couldn't get it to work.

All of that said thanks for taking this on.  I'll need to monkey around some with the audio situation but otherwise we're good to go.

---

### Post by FakeOutdoorsman on 2014-03-12
> **Langstracht said:**
> Except, there IS a problem with the audio.  Which is stuttering.  Could be a player problem I suppose.
What device is this?

> **Langstracht said:**
> Tried to do this using height rather than width and couldn't get it to work.
What do you mean? Did ffmpeg give an error, or did the output just not work on the device? If it is an ffmpeg problem then you should include your ffmpeg command and the complete ffmpeg console output.

Do you have a video that does play on the device normally? If you do then please show the complete output of:
```

./ffmpeg -i video_that_does_work.avi

```

---

### Post by Langstracht on 2014-03-13
The device is an Archos 3 Vision.

> What do you mean? Did ffmpeg give an error, or did the output just not work on the device? If it is an ffmpeg problem then you should include your ffmpeg command and the complete ffmpeg console output.

I mean I was unable to deduce the correct syntax for ffmpeg to output anything (other than errors) when I specified the height rather than the width.

However, unless there is some reason not to, I would just as well specify the screen size (and accept any distortion that might result) as 400x240.  Your advice is sought and appreciated.

> Do you have a video that does play on the device normally?

I do.

```
ffmpeg version N-61271-ge161c1b Copyright (c) 2000-2014 the FFmpeg developers
  built on Mar 11 2014 05:12:35 with gcc 4.6 (Debian 4.6.3-1)
  configuration: --prefix=/root/ffmpeg-static/32bit --arch=x86_32 --extra-cflags='-m32 -I/root/ffmpeg-static/32bit/include -static' --extra-ldflags='-m32 -L/root/ffmpeg-static/32bit/lib -static' --extra-libs='-lxml2 -lexpat -lfreetype' --enable-static --disable-shared --disable-ffserver --disable-doc --enable-bzlib --enable-zlib --enable-postproc --enable-runtime-cpudetect --enable-libx264 --enable-gpl --enable-libtheora --enable-libvorbis --enable-libmp3lame --enable-gray --enable-libass --enable-libfreetype --enable-libopenjpeg --enable-libspeex --enable-libvo-aacenc --enable-libvo-amrwbenc --enable-version3 --enable-libvpx
  libavutil      52. 66.101 / 52. 66.101
  libavcodec     55. 52.102 / 55. 52.102
  libavformat    55. 34.100 / 55. 34.100
  libavdevice    55. 11.100 / 55. 11.100
  libavfilter     4.  3.100 /  4.  3.100
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 18.100 /  0. 18.100
  libpostproc    52.  3.100 / 52.  3.100
Input #0, avi, from 'Movie2.avi':
  Duration: 02:10:08.56, start: 0.000000, bitrate: 507 kb/s
    Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 400x266 [SAR 1:1 DAR 200:133], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 48000 Hz, stereo, s16p, 128 kb/s
At least one output file must be specified
```

The list line:

> At least one output file must be specified

shows up in red - i.e. as an error.

---

### Post by FakeOutdoorsman on 2014-03-13
> **Langstracht said:**
> I mean I was unable to deduce the correct syntax for ffmpeg to output anything (other than errors) when I specified the height rather than the width.
You should always include your ffmpeg command and the complete ffmpeg console output.

> However, unless there is some reason not to, I would just as well specify the screen size (and accept any distortion that might result) as 400x240.  Your advice is sought and appreciated.
Using the scale filter will prevent distortion, but if that doesn't bother you then you can force the size.

> ```
Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 48000 Hz, stereo, s16p, 128 kb/s
At least one output file must be specified
```
I guess it likes MP3 audio:
```
./ffmpeg -i movie1.m4v -vf scale=400:-1 -codec:v mpeg4 -q:v 4 -codec:a libmp3lame -q:a 5 movie1.avi
```

> "At least one output file must be specified " shows up in red - i.e. as an error.
You can ignore that. In that instance you are simply using ffmpeg to find info about the input and not for also making an output file (which ffmpeg is telling that what it is expecting).

---

### Post by Langstracht on 2014-03-14
> I guess it likes MP3 audio:

```
./ffmpeg -i movie1.m4v -vf scale=400:-1 -codec:v mpeg4 -q:v 4 -codec:a libmp3lame -q:a 5 movie1.avi
```

I guess it does.  Your command works perfectly.  Thank you SO much.

---

