---
title: "Trimming video using ffmpeg?"
date: 2016-02-29
forum: Multimedia Software
---

### Post by eezacque on 2016-02-29
I would appreciate some help trimming a video file.
The file plays fine through the Ubuntu Videos software, VLC and ffplay, but trimming through ffmpeg gives me an audio-only file.
I am trimming through
 ffmpeg  -analyzeduration 2148M -probesize 2148M  -i in.mov -pix_fmt yuv420p -ss 00:30:00 -to 00:35:00 -vcodec copy -acodec copy out.mp4
but keep getting the error "Could not find codec parameters for stream 0 (Video: h264 (avc1 / 0x31637661), none, 720x576): unspecified pixel format
Consider increasing the value for the 'analyzeduration' and 'probesize' options" whatever values I choose for said parameters.

Any clue?

---

### Post by FakeOutdoorsman on 2016-02-29
Please show the complete console output from your command (and use the code button to format it nicely).

---

### Post by goofprog on 2016-02-29
I would suggest to omit the pixel format option and not to do a codec copy and just have it render again.  I personally had problems with audio syncing when I tried to copy and clip a movie file.

---

### Post by eezacque on 2016-03-01
> **FakeOutdoorsman said:**
> Please show the complete console output from your command (and use the code button to format it nicely).

```

$ ffmpeg  -analyzeduration 2148M -probesize 2148M -i in.mov -pix_fmt yuv420p -ss 00:30:00 -to 00:35:00  -vcodec copy -acodec copy out.mp4 
ffmpeg version 2.5.10-0ubuntu0.15.04.1 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 4.9.2 (Ubuntu 4.9.2-10ubuntu13)
  configuration: --prefix=/usr --extra-version=0ubuntu0.15.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --shlibdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --enable-shared --disable-stripping --enable-avresample --enable-avisynth --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libshine --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libwavpack --enable-libwebp --enable-libxvid --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzvbi --enable-libzmq --enable-frei0r --enable-libvpx --enable-libx264 --enable-libsoxr --enable-gnutls --enable-openal --enable-libopencv --enable-librtmp --enable-libx265
  libavutil      54. 15.100 / 54. 15.100
  libavcodec     56. 13.100 / 56. 13.100
  libavformat    56. 15.102 / 56. 15.102
  libavdevice    56.  3.100 / 56.  3.100
  libavfilter     5.  2.103 /  5.  2.103
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  1.100 /  1.  1.100
  libpostproc    53.  3.100 / 53.  3.100
[h264 @ 0x1949fe0] A non-intra slice in an IDR NAL unit.
[h264 @ 0x1949fe0] decode_slice_header error
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1946de0] Could not find codec parameters for stream 0 (Video: h264 (avc1 / 0x31637661), none, 720x576): unspecified pixel format
Consider increasing the value for the 'analyzeduration' and 'probesize' options
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'in.mov':
  Metadata:
    major_brand     : isom
    minor_version   : 0
    compatible_brands: mp41avc1
    creation_time   : 2016-02-25 15:54:30
    encoder         : vlc 2.2.1 stream output
    encoder-eng     : vlc 2.2.1 stream output
  Duration: 00:46:36.84, start: 0.000000, bitrate: 3431 kb/s
    Stream #0:0(eng): Video: h264 (avc1 / 0x31637661), none, 720x576, SAR 16:15 DAR 4:3, 1000k tbr, 1000k tbn, 2000k tbc (default)
    Metadata:
      creation_time   : 2016-02-25 15:54:30
      handler_name    : VideoHandler
    Stream #0:1(eng): Audio: mp2 (mp4a / 0x6134706D), 44100 Hz, stereo, s16p, 127 kb/s (default)
    Metadata:
      creation_time   : 2016-02-25 15:54:30
      handler_name    : SoundHandler
    Stream #0:2(eng): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 720x576 [SAR 16:15 DAR 4:3], 3298 kb/s, 25 fps, 25 tbr, 1000k tbn, 50 tbc (default)
    Metadata:
      creation_time   : 2016-02-25 15:54:30
      handler_name    : VideoHandler
Output #0, mp4, to 'out.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 0
    compatible_brands: mp41avc1
    encoder         : Lavf56.15.102
    Stream #0:0(eng): Video: h264 ([33][0][0][0] / 0x0021), none, 720x576 [SAR 16:15 DAR 4:3], q=2-31, 1000k tbn, 1000k tbc (default)
    Metadata:
      creation_time   : 2016-02-25 15:54:30
      handler_name    : VideoHandler
    Stream #0:1(eng): Audio: mp2 (i[0][0][0] / 0x0069), 44100 Hz, stereo, 127 kb/s (default)
    Metadata:
      creation_time   : 2016-02-25 15:54:30
      handler_name    : SoundHandler
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
Press [q] to stop, [?] for help
frame=    0 fps=0.0 q=-1.0 Lsize=    4711kB time=00:05:00.01 bitrate= 128.6kbits/s    
video:0kB audio:4677kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.720447%

```

---

### Post by eezacque on 2016-03-01
> **goofprog said:**
> I would suggest to omit the pixel format option and not to do a codec copy and just have it render again.  I personally had problems with audio syncing when I tried to copy and clip a movie file.

I spent some time playing with the various parameters, and omitting the pixel format option gives even more error messages:
```

[buffer @ 0xa32860] Unable to parse option value "-1" as pixel format
    Last message repeated 1 times
[buffer @ 0xa32860] Error setting option pix_fmt to value -1.
[graph 0 input from stream 0:0 @ 0xa35180] Error applying options to the filter.
Error opening filters!

```

---

### Post by QDR06VV9 on 2016-03-02
I try to use this:
```
ffmpeg -analyzeduration 2147483647 -probesize 2147483647 -i /path/to/video.mp4. 2147483647 is max_int
```
Hope this helps..

---

### Post by eezacque on 2016-03-03
> **runrickus said:**
> I try to use this:
```
ffmpeg -analyzeduration 2147483647 -probesize 2147483647 -i /path/to/video.mp4. 2147483647 is max_int
```
Hope this helps..

Nope, but thanks for trying...

---

### Post by FakeOutdoorsman on 2016-03-04
How was the file created? I'm guessing the file may be damaged or corrupted. It appears to have two video streams, and the second one may be undamaged. You can try stream copying that one.

Additionally, 2.5.10 is considered old since FFmpeg development is so active. I recommend [downloading a recent build](http://johnvansickle.com/ffmpeg/). Then try:

```
ffmpeg -i input -map 0:v:1 -map 0:a -c copy -ss 00:30:00 -to 00:35:00 output.mp4
```

Due to the condition of the file you may or may not need to add -analyzeduration and -probesize.
MP2 audio is not the most common audio format used in MP4 container, so your player/device/decoder may not like it.

---

### Post by eezacque on 2016-03-04
> **FakeOutdoorsman said:**
> How was the file created? I'm guessing the file may be damaged or corrupted. It appears to have two video streams, and the second one may be undamaged. You can try stream copying that one.

Additionally, 2.5.10 is considered old since FFmpeg development is so active. I recommend [downloading a recent build]("http://johnvansickle.com/ffmpeg/"). Then try:

```
ffmpeg -i input -map 0:v:1 -map 0:a -c copy -ss 00:30:00 -to 00:35:00 output.mp4
```

Due to the condition of the file you may or may not need to add -analyzeduration and -probesize.
MP2 audio is not the most common audio format used in MP4 container, so your player/device/decoder may not like it.

The file was ripped from a dvd using vlc; note that it plays through a variety of software.
I'll upgrade ffmpeg and see if that helps.

One more thing: how can I copy a specific video stream?

---

### Post by QDR06VV9 on 2016-03-04
> **eezacque said:**
> 
One more thing: how can I copy a specific video stream?
See if this helps: [https://ffmpeg.org/ffmpeg.html](https://ffmpeg.org/ffmpeg.html)

---

