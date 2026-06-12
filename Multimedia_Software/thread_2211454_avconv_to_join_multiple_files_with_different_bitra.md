---
title: "avconv to join multiple files with different bitrates"
date: 2014-03-16
forum: Multimedia Software
---

### Post by Lei_Jiang on 2014-03-16
Hi,

I have several mp4 files with slightly different video/audio bitrates and I would like to join them into one(on 12.04LTS). I know the 'concat:file1|file2|file3' methodology but this seems to only work with files that have same settings for everything, fps, rates, etc. How can I achieve this?

Also any tip to keep quality loss minimum? The file specs are like below.

avconv version 0.8.10-4:0.8.10-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:56:59 with gcc 4.6.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '1.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isomavc1
    creation_time   : 2014-02-23 06:53:23
  Duration: 00:05:00.20, start: 0.000000, bitrate: 1019 kb/s
    Stream #0.0(und): Video: h264 (High), yuv420p, 1280x720, 952 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Metadata:
      creation_time   : 2014-02-23 06:53:23
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 64 kb/s
    Metadata:
      creation_time   : 2014-02-23 06:53:23

Thanks!

---

