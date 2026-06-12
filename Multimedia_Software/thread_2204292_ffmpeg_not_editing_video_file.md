---
title: "ffmpeg not editing video file"
date: 2014-02-07
forum: Multimedia Software
---

### Post by Geoff_Lane on 2014-02-07
I have an mpeg ts file giving playback problems.

Recorded from a set top box VLC freezes after around 90 seconds as does a hardware video player I have.

However my Sony Bravia built in media player views it fine.

I have tried to get ffmpeg to cut out the starting 2 minutes of a video file  but it freezes after a short while.

The following is the output from ffmpeg, same with avconv;

> geoff@mercury:~/.gvfs/SFTP for root on pi/media/iomegaExt4/video/TV Series/MrS$ avconv -i MrS-01.mpg 
avconv version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:12:07 with gcc 4.6.3
[mpeg2video @ 0x82415a0] mpeg_decode_postinit() failure
    Last message repeated 10 times
[mpegts @ 0x823c240] max_analyze_duration reached
[mpegts @ 0x823c240] PES packet size mismatch
    Last message repeated 1 times
Input #0, mpegts, from 'MrS-01.mpg':
  Duration: N/A, start: 63770.130756, bitrate: N/A
  Program 4164 
    Metadata:
      service_name    : BBC ONE Lon
      service_provider: 
    Stream #0.0[0x65]: Video: mpeg2video (Main), yuv420p, 720x576 [PAR 64:45 DAR 16:9], 15000 kb/s, 26.94 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x66](eng): Audio: mp2, 48000 Hz, stereo, s16, 256 kb/s
    Stream #0.2[0x6a](eng): Audio: mp2, 48000 Hz, mono, s16, 64 kb/s (visual impaired)
    Stream #0.3[0x69](eng): Subtitle: dvbsub
  Program 8261 
    Metadata:
      service_name    : ITV
      service_provider: 
    Stream #0.4[0x6a5]: Video: mpeg2video, 90k tbn
    Stream #0.6[0x6a6](eng): Audio: mp3, 0 channels
    Stream #0.5[0x6a7](eng): Audio: mp3, 0 channels (visual impaired)
    Stream #0.7[0x6c3](eng): Subtitle: dvbsub
At least one output file must be specified

Any advice as to how I could edit out the first 2 mins as I am sure it will play fine after that.

Geffers

---

### Post by FakeOutdoorsman on 2014-02-07
Please download a [recent build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) (the real one, not the fake junk in the repo) and see if the issue still occurs:

```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz
```

Then run it (notice the **./** before ffmpeg):
```
./ffmpeg -ss 120 -i MrS-01.mpg -codec copy -map 0 output.mpg
```

---

