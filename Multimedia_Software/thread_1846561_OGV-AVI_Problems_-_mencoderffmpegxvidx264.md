---
title: "OGV-AVI Problems - mencoder/ffmpeg/xvid/x264"
date: 2011-09-19
forum: Multimedia Software
---

### Post by dodle on 2011-09-19
I am having all kinds of trouble converting a video that I created with recordmydesktop. I first tried encoding the OGV to AVI with mencoder:

```
mencoder apt_segfault.ogv -ovc xvid -xvidencopts pass=1:bitrate=1400 -oac mp3lame -lameopts cbr:br=128 -o apt_segfault.avi
```

But only a small portion of the video is encoded and is off sync with the audio. I tried with the x264 codec as well and got the same result. 

I then decided to try ffmpeg:

```
ffmpeg -i apt_segfault.ogv -vcodec libxvid -b 1400k -acodec libmp3lame -ab 128k apt_segfault.avi
```

The whole video encodes and works fine. My only complaint is that I can't improve the video quality. Setting the video bitrate (-b 1400k) didn't seem to make a difference. The video has turned out at 201Kbps. The same thing happens with mencoder, passing 'bitrate=1400' to xvidencopts doesn't affect anything.

Also, when trying to use x264 with ffmpeg I get the following errors:

```
ffmpeg -i apt_segfault.ogv -vcodec libx264 -acodec libmp3lame -ab 128k apt_segfault.avi

...
...
...
[ogg @ 0x8e88bc0]max_analyze_duration reached
Input #0, ogg, from 'apt_segfault.ogv':
  Duration: 00:04:22.93, start: 0.000000, bitrate: 382 kb/s
    Stream #0.0: Data: skeleton
    Stream #0.1: Video: theora, yuv420p, 1024x768 [PAR 1:1 DAR 4:3], 15 fps, 15 tbr, 15 tbn, 15 tbc
    Stream #0.2: Audio: vorbis, 44100 Hz, mono, s16, 239 kb/s
File 'apt_segfault.avi' already exists. Overwrite ? [y/N] y
[libx264 @ 0x8e8c290]broken ffmpeg default settings detected
[libx264 @ 0x8e8c290]use an encoding preset (vpre)
Output #0, avi, to 'apt_segfault.avi':
    Stream #0.0: Video: libx264, yuv420p, 1024x768 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: libmp3lame, 44100 Hz, mono, s16, 128 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.2 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

So if anybody has any ideas why mencoder fails to encode the entire video or can tell me how to increase the video bitrate in ffmpeg, please let me know.

---

### Post by dodle on 2011-09-20
I figured out what was wrong with libx264 and ffmpeg. Apparently the default settings for libx264 are broken and a video preset needs to be declared with the '-vpre' flag:

```
ffmpeg -i apt_segfault.ogv -vcodec libx264 -vpre lossless_ultrafast ...
```

---

