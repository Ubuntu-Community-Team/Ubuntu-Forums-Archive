---
title: "exporting to alac with Audacity"
date: 2020-05-17
forum: Multimedia Software
---

### Post by shantiq on 2020-05-17
Any of you know how to do this ...
Tried a few tricks but no good thus far
Thanx
shan

---

### Post by Holger_Gehrke on 2020-05-17
You can use "File"->"Export Audio"->"Export" and then select "(external program)" as format. As the command you should enter
```
ffmpeg -i - -acodec alac "%f"
```
[source]("https://wiki.audacityteam.org/wiki/FFmpeg_integration#Apple_Lossless_.28ALAC.29")

Holger

---

### Post by shantiq on 2020-05-17
Thank u very much Holger was trying to do that through "Custom FFmpeg Export" and was getting nowhere fast

---

### Post by shantiq on 2020-05-17
really wanted a 24-bit file so after much horsing around this does it >>


```
f*fmpeg -i -  -c:a alac -sample_fmt s32p "%f"*
```


**LOG:**


```
ffmpeg -i -  -c:a alac -sample_fmt s32p "/home/shan/Desktop/NAMEOFFILE.m4a"

ffmpeg version N-91586-g90dc584 Copyright (c) 2000-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/home/shan/ffmpeg_build --pkg-config-flags=--static --extra-cflags=-I/home/shan/ffmpeg_build/include --extra-ldflags=-L/home/shan/ffmpeg_build/lib --extra-libs='-lpthread -lm' --bindir=/home/shan/bin --enable-gpl --enable-libaom --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-openssl --enable-libopus --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-nonfree
  libavutil      56. 18.102 / 56. 18.102
  libavcodec     58. 22.101 / 58. 22.101
  libavformat    58. 17.101 / 58. 17.101
  libavdevice    58.  4.101 / 58.  4.101
  libavfilter     7. 26.100 /  7. 26.100
  libswscale      5.  2.100 /  5.  2.100
  libswresample   3.  2.100 /  3.  2.100
  libpostproc    55.  2.100 / 55.  2.100
Guessed Channel Layout for Input Stream #0.0 : stereo
Input #0, wav, from 'pipe:':
  Duration: N/A, bitrate: 1536 kb/s
    Stream #0:0: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 48000 Hz, stereo, s16, 1536 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (pcm_s16le (native) -> alac (native))
[alac @ 0x55ab92dc1e00] encoding as 24 bits-per-sample
Output #0, ipod, to '/home/shan/Desktop/NAMEOFFILE.m4a':
  Metadata:
    encoder         : Lavf58.17.101
    Stream #0:0: Audio: alac (alac / 0x63616C61), 48000 Hz, stereo, s32p (24 bit), 128 kb/s
    Metadata:
      encoder         : Lavc58.22.101 alac
```

---

### Post by Yellow Pasque on 2020-05-18
> Stream #0:0: Audio: alac (alac / 0x63616C61), 48000 Hz, stereo, s32p (24 bit), 128 kb/s

128k? That seems strange for a lossless codec. But I'm not too familiar with ALAC, so maybe I'm misunderstanding something.

---

### Post by shantiq on 2020-06-03
> **Yellow Pasque said:**
> 128k? That seems strange for a lossless codec. But I'm not too familiar with ALAC, so maybe I'm misunderstanding something.


yes since the truth is more in the 1400/1800k range but this is what ffmpeg displays when high conversions take place; it is as if it thinks it is so high we will just say the default for an mp3 conversion 128k
I can assure you the result is what it should be; the reading is just odd :]

---

