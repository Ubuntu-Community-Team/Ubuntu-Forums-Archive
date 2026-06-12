---
title: "is possible compress these flv file more?"
date: 2013-10-25
forum: Multimedia Software
---

### Post by davidtuti2 on 2013-10-25
Hi,

How is possible that these flv file to can compress more. What command would be use?

Many thanks and sorry for my english!

```
ffmpeg -i interffmpeg version N-57417-g2e7a1fd Copyright (c) 2000-2013 the FFmpeg developers
  built on Oct 25 2013 23:13:30 with gcc 4.6 (Debian 4.6.3-14+rpi1)
  configuration: --enable-gpl --enable-libx264 --enable-libmp3lame --enable-nonfree --enable-libaacplus
  libavutil      52. 47.101 / 52. 47.101
  libavcodec     55. 38.101 / 55. 38.101
  libavformat    55. 19.104 / 55. 19.104
  libavdevice    55.  5.100 / 55.  5.100
  libavfilter     3. 89.100 /  3. 89.100
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Input #0, flv, from 'inter':
  Duration: 00:01:25.59, start: 0.000000, bitrate: 33 kb/s
    Stream #0:0: Audio: aac, 44100 Hz, stereo, fltp


ls -lh inter
-rw-r--r-- 1 pi pi 353K Oct 26 00:29 inter




```

---

### Post by davidtuti2 on 2013-10-26
Nobody knows?

---

### Post by FakeOutdoorsman on 2013-10-26
You did not provide much information. Did you create these files? If yes, then show your ffmpeg command and the complete console output. What format(s) do you require?

---

### Post by davidtuti2 on 2013-10-26
These file is a flv file that I have when I make a rstdump.  The output file is what I would like to compress

---

### Post by FakeOutdoorsman on 2013-10-27
It seems to only contain AAC audio. The bitrate is already fairly low (33k/s). How low do you need it to be?

---

