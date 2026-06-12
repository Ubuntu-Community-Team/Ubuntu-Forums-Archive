---
title: "ffmpeg: how to specify to copy only one audio stream while encoding the others"
date: 2012-06-29
forum: Multimedia Software
---

### Post by tanoloco on 2012-06-29
Hello,

I'm trying to encode a video which has two audio streams. I usually convert audio to 192 kbps. As one of them comes already in this flavour, I would like to copy it as it is, while converting the other audio stream.

Here's the info of my source file:
```

ffmpeg -i "source.mkv" 
ffmpeg version git-2012-03-05-1007a80 Copyright (c) 2000-2012 the FFmpeg developers
  built on Mar  5 2012 09:40:09 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab --enable-libxvid --enable-libvpx
  libavutil      51. 41.100 / 51. 41.100
  libavcodec     54.  8.100 / 54.  8.100
  libavformat    54.  2.100 / 54.  2.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 63.100 /  2. 63.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  7.100 /  0.  7.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, matroska,webm, from 'source.mkv':
  Duration: 02:05:05.82, start: 0.000000, bitrate: 8086 kb/s
    Stream #0:0: Video: h264 (High), yuv420p, 1920x800 [SAR 1:1 DAR 12:5], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Metadata:
      title           : x264   1920x800   Bitrate=7252 kbps   AvrageQuantizer=21.283
    Stream #0:1(eng): Audio: ac3, 48000 Hz, 5.1(side), s16, 448 kb/s (default)
    Metadata:
      title           : English AC3 5.1 chnls 640 kbps
    Stream #0:2(ita): Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Metadata:
      title           : Italian AC3 2.0 chnls 192 kbps

```

I tried to use the following command:
```

nice ffmpeg -i "source.mkv" -map 0:0 -s 640x272 -f ogg -vcodec libtheora -r 23.98 -b:v 1200k -map 0:1 [COLOR="Red"]-acodec:a:0 libvorbis[/COLOR] -ac:a:0 6 -b:a:0 192k -ar:a:0 48000 -map 0:2 [COLOR="red"]-acodec:a:1 copy[/COLOR] -async 1 -pass 2 -passlogfile "pass" "target.ogv"

```

But I get a fatal error:
```

ffmpeg version git-2012-03-05-1007a80 Copyright (c) 2000-2012 the FFmpeg developers
  built on Mar  5 2012 09:40:09 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab --enable-libxvid --enable-libvpx
  libavutil      51. 41.100 / 51. 41.100
  libavcodec     54.  8.100 / 54.  8.100
  libavformat    54.  2.100 / 54.  2.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 63.100 /  2. 63.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  7.100 /  0.  7.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, matroska,webm, from 'source.mkv':
  Duration: 02:05:05.82, start: 0.000000, bitrate: 8086 kb/s
    Stream #0:0: Video: h264 (High), yuv420p, 1920x800 [SAR 1:1 DAR 12:5], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Metadata:
      title           : x264   1920x800   Bitrate=7252 kbps   AvrageQuantizer=21.283
    Stream #0:1(eng): Audio: ac3, 48000 Hz, 5.1(side), s16, 448 kb/s (default)
    Metadata:
      title           : English AC3 5.1 chnls 640 kbps
    Stream #0:2(ita): Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Metadata:
      title           : Italian AC3 2.0 chnls 192 kbps
w:1920 h:800 pixfmt:yuv420p tb:1/1000000 sar:1/1 sws_param:
[scale @ 0x9e24940] w:1920 h:800 fmt:yuv420p -> w:640 h:272 fmt:yuv420p flags:0x4
[COLOR="Red"][ogg @ 0x9cd29c0] Unsupported codec id in stream 1[/COLOR]
Output #0, ogg, to 'target.ogv':
  Metadata:
    title           : title
    comment         : comment
    date            : date
    encoder         : Lavf54.2.100
    Stream #0:0: Video: theora, yuv420p, 640x272 [SAR 51:50 DAR 12:5], q=2-31, pass 2, 1200 kb/s, 23.98 tbn, 23.98 tbc (default)
    Metadata:
      title           : x264   1920x800   Bitrate=7252 kbps   AvrageQuantizer=21.283
    Stream #0:1(eng): Audio: ac3, 48000 Hz, 5.1(side), 448 kb/s (default)
    Metadata:
      title           : English AC3 5.1 chnls 640 kbps
    Stream #0:2(ita): Audio: ac3, 48000 Hz, stereo, 192 kb/s
    Metadata:
      title           : Italian AC3 2.0 chnls 192 kbps
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> libtheora)
  Stream #0:1 -> #0:1 (copy)
  Stream #0:2 -> #0:2 (copy)
[COLOR="Red"]Could not write header for output file #0 (incorrect codec parameters ?)[/COLOR]

```

I google for a while without finding the right search keywords to get the solution.
Any of you would be so kind to help me in carrying this out correctly?

Thank you in advance!

---

### Post by tanoloco on 2012-06-29
I took a step ahead, using

```

nice ffmpeg -i "source.mkv" -map 0:0 -s 640x272 -f ogg [COLOR="Red"]-c:v libtheora[/COLOR] -r 23.98 -b:v 1200k -map 0:1 [COLOR="red"]-c:a:0 libvorbis[/COLOR] -ac:a:0 6 -b:a:0 192k -ar:a:0 48000 -map 0:2 [COLOR="red"]-c:a:1 copy [/COLOR]-async 1 -pass 2 -passlogfile "pass" "target.ogv"

```

I succeed at selecting one stream to be copied, but I still cannot go on .. it allows me to convert ac3 into libvorbis, but it doesn't allow me to copy ac3 ??? 
What does it means?
Is the container the problem?
```

ffmpeg version git-2012-03-05-1007a80 Copyright (c) 2000-2012 the FFmpeg developers
  built on Mar  5 2012 09:40:09 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab --enable-libxvid --enable-libvpx
  libavutil      51. 41.100 / 51. 41.100
  libavcodec     54.  8.100 / 54.  8.100
  libavformat    54.  2.100 / 54.  2.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 63.100 /  2. 63.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  7.100 /  0.  7.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, matroska,webm, from 'source.mkv':
  Duration: 02:05:05.82, start: 0.000000, bitrate: 8086 kb/s
    Stream #0:0: Video: h264 (High), yuv420p, 1920x800 [SAR 1:1 DAR 12:5], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Metadata:
      title           : x264   1920x800   Bitrate=7252 kbps   AvrageQuantizer=21.283
    Stream #0:1(eng): Audio: ac3, 48000 Hz, 5.1(side), s16, 448 kb/s (default)
    Metadata:
      title           : English AC3 5.1 chnls 640 kbps
    Stream #0:2(ita): Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Metadata:
      title           : Italian AC3 2.0 chnls 192 kbps
w:1920 h:800 pixfmt:yuv420p tb:1/1000000 sar:1/1 sws_param:
[scale @ 0xa81f940] w:1920 h:800 fmt:yuv420p -> w:640 h:272 fmt:yuv420p flags:0x4
[COLOR="red"]Incompatible sample format 's16' for codec 'libvorbis', auto-selecting format 'flt'
[ogg @ 0xa6cd9c0] Unsupported codec id in stream 2[/COLOR]
Output #0, ogg, to 'target.ogv':
  Metadata:
    title           : title
    comment         : comment
    date            : date
    encoder         : Lavf54.2.100
    Stream #0:0: Video: theora, yuv420p, 640x272 [SAR 51:50 DAR 12:5], q=2-31, pass 2, 1200 kb/s, 23.98 tbn, 23.98 tbc (default)
    Metadata:
      title           : x264   1920x800   Bitrate=7252 kbps   AvrageQuantizer=21.283
    Stream #0:1(eng): Audio: vorbis, 48000 Hz, 6 channels, flt, 192 kb/s (default)
    Metadata:
      title           : English AC3 5.1 chnls 640 kbps
    Stream #0:2(ita): Audio: ac3, 48000 Hz, stereo, 192 kb/s
    Metadata:
      title           : Italian AC3 2.0 chnls 192 kbps
[COLOR="Blue"]Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> libtheora)
  Stream #0:1 -> #0:1 (ac3 -> libvorbis)
  Stream #0:2 -> #0:2 (copy)[/COLOR]
[COLOR="red"]Could not write header for output file #0 (incorrect codec parameters ?)[/COLOR]


```

---

### Post by FakeOutdoorsman on 2012-06-29
> **tanoloco said:**
> Is the container the problem?

Yes, AC3 appears to be unsupported by Ogg. See [RFC 5334: Section 4](http://tools.ietf.org/html/rfc5334#section-4) or [Ogg: Specification of MIME types and respective codecs parameter](http://wiki.xiph.org/index.php/MIMETypesCodecs) for officially supported audio formats.

---

