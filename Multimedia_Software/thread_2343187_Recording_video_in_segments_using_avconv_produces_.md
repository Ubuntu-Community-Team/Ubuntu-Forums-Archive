---
title: "Recording video in segments using avconv produces weird files"
date: 2016-11-14
forum: Multimedia Software
---

### Post by hatross1 on 2016-11-14
Hello gurus!

I'm trying to record a video from my webcam (no audio needed), splitting the record into fragments. I'm using the latest build of avconv for this:

```

avconv -version

avconv version v13_dev0-397-g31756ab, Copyright (c) 2000-2016 the Libav developers
  built on Nov 14 2016 10:30:33 with gcc 4.9.2 (Debian 4.9.2-10)
avconv v13_dev0-397-g31756ab
libavutil     55. 29. 0 / 55. 29. 0
libavcodec    57. 28. 4 / 57. 28. 4
libavformat   57.  9. 0 / 57.  9. 0
libavdevice   56.  1. 0 / 56.  1. 0
libavfilter    6.  8. 0 /  6.  8. 0
libavresample  3.  0. 0 /  3.  0. 0
libswscale     4.  0. 0 /  4.  0. 0
```

Assume I have to make 75-sec record, splitting it into 15-sec (approx) fragments. For this I'm issuing a command:

```

avconv -f video4linux2 -i /dev/video0 -r 15 -s 640x360 -vcodec mpeg4 -b: 300k -map 0 -f segment -segment_time 15 -t 75 test_%02d.mkv
```

Well, I'm getting five files (test_00 - test_04) as supposed,

first file in sequence is totally ok, but **all files except first show(have) wrong duration info**.

for second file (test_01) - players (totem and vlc) show 30 sec length, but playback stops where it should, ~ after 15 sec of playing
same duration is shown by avconv:
```
avconv -i test_01.mkv 
avconv version v13_dev0-397-g31756ab, Copyright (c) 2000-2016 the Libav developers
  built on Nov 14 2016 10:30:33 with gcc 4.9.2 (Debian 4.9.2-10)
Input #0, matroska,webm, from 'test_01.mkv':
  Metadata:
    ENCODER         : Lavf57.9.0
  Duration: 00:00:30.33, start: 0.000000, bitrate: N/A
    Stream #0:0: Video: mpeg4 (Simple Profile)
      yuv420p, 640x360 [PAR 1:1 DAR 16:9], PAR 1:1 DAR 16:9
      15 fps, 1k tbn
At least one output file must be specified
```

for third - 45 sec length is shown,  but playback stops where it should, ~ after 15 sec
fourth - 60 sec, fifth - 1m15s ..and so on

actually this makes later reviewing and navigating videos very uncomfortable.
Can anyone pls advice what could be done to fix this?

Thanks in advance!

Dmitry

---

### Post by hatross1 on 2016-11-16
Well, thanks anyone for your silence :)

Solution is:
- switch to ffmpeg
- use following command:

```

ffmpeg -f video4linux2 -i /dev/video0 -r 15 -s 960x720 -vcodec mpeg4 -b: 400k -map 0 -f segment -segment_time 15 -reset_timestamps 1 -t 75 test_%02d.mkv
```

I'm closing the thread...

---

