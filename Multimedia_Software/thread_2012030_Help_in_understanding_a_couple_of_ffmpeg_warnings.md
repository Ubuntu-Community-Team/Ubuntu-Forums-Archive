---
title: "Help in understanding a couple of ffmpeg warnings"
date: 2012-06-28
forum: Multimedia Software
---

### Post by tanoloco on 2012-06-28
Hello,

Can anyone help me to understand why I'm getting the following warnings, please? What am I supposed to change in the command I fire?

```

nice ffmpeg -i "source.mkv" -map 0:0 -s 640x272 -f ogg -vcodec libtheora -r 23.98 -b:v 1200k -acodec libvorbis -ac 6 -ar 48000 -b:a 192k -vol 300 -map 0:1 -async 1 -pass 2 -passlogfile "pass" "target.ogv"

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
  Metadata:
    title           : title [HDTV,H.264,AC3] - THOR
  Duration: 01:55:05.35, start: 0.000000, bitrate: 5428 kb/s
    Stream #0:0(eng): Video: h264 (High), yuv420p, 1280x544, SAR 1:1 DAR 40:17, 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Metadata:
      title           : title
    Stream #0:1(eng): Audio: ac3, 48000 Hz, stereo, s16, 384 kb/s (default)
    Metadata:
      title           : AC3 2.0
    Stream #0:2(eng): Subtitle: ssa (default)
    Metadata:
      title           : English ***
    Stream #0:3: Attachment: ttf
    Metadata:
      filename        : TCCEB.TTF
      mimetype        : application/x-truetype-font
    Stream #0:4: Attachment: ttf
    Metadata:
      filename        : TCCEB.TTF
      mimetype        : application/x-truetype-font
[buffer @ 0xaaee280] w:1280 h:544 pixfmt:yuv420p tb:1/1000000 sar:1/1 sws_param:
[scale @ 0xaae4880] w:1280 h:544 fmt:yuv420p -> w:640 h:272 fmt:yuv420p flags:0x4
[COLOR="Red"]Incompatible sample format 's16' for codec 'libvorbis', auto-selecting format 'flt'[/COLOR]
[COLOR="Red"][libvorbis @ 0xaae84c0] No channel layout specified. The encoder will use Vorbis channel layout for 6 channels.[/COLOR]
Output #0, ogg, to 'target.ogv':
  Metadata:
    title           : title
    comment         : comment
    date            : date
    encoder         : Lavf54.2.100
    Stream #0:0(eng): Video: theora, yuv420p, 640x272 [SAR 1:1 DAR 40:17], q=2-31, pass 2, 1200 kb/s, 23.98 tbn, 23.98 tbc (default)
    Metadata:
      title           : title
    Stream #0:1(eng): Audio: vorbis, 48000 Hz, 6 channels, flt, 192 kb/s (default)
    Metadata:
      title           : AC3 2.0
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> libtheora)
  Stream #0:1 -> #0:1 (ac3 -> libvorbis)


```

Thank you in advance!

---

### Post by andrew.46 on 2012-06-28
Do you really want 6 channel sound for your output file?

---

### Post by tanoloco on 2012-06-28
Thank you, setting -ac 2 will remove the second warning.
Still remains the first one:

Incompatible sample format 's16' for codec 'libvorbis', auto-selecting format 'flt'

---

### Post by FakeOutdoorsman on 2012-06-28
You can ignore that. It's just telling you that it's converting to a different audio sample format.

---

### Post by andrew.46 on 2012-06-28
Indeed you could safely ignore both warnings (and even manually map the 6 channels if you were really keen). If the sample format warning really bothers you you could bypass FFmpeg's auto selection and add something like the following to use floating point in your commandline:

```

-sample_fmt flt 

```

but this is not really necessary. Most of the details here:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -h 2>/dev/null | grep sample_fmt[/COLOR]**
-sample_fmts        show available audio sample formats
-sample_fmt format  set sample format
-request_sample_fmt <int>   .D.A. sample format audio decoders should prefer
-in_sample_fmt     <int>   ...A. Input Sample Format
-out_sample_fmt    <int>   ...A. Output Sample Format
-internal_sample_fmt <int>   ...A. Internal Sample Format

```

Lots of room for small adjustments in FFmpeg :).

---

### Post by tanoloco on 2012-06-29
Thank you all guys for your nice and kind explanation.

---

