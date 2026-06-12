---
title: "FFMPEG and Final Cut"
date: 2010-12-12
forum: Multimedia Software
---

### Post by fosheezy on 2010-12-12
I am trying to optimize my workflow between Final Cut on my laptop and FFMPEG on my ubuntu server. Since the server is faster and a back-end machine, I'd rather it do all the importing of my AVCHD footage to .mov files, then drag into Final Cut to edit and export, to go back to ffmpeg to be encoded for different purposes. I'd like FFMPEG to handle all of the heavy work (even though I realize the exporting from Final Cut is one thing I cannot avoid).

The issue I've been having is that when I go to export the final video in final cut the export will take literally 24 hours for a 20 minute segment. I'm using a core i7 2.66GHz macbook pro so I'm not on an old laptop. There's got to be an issue between the codec that FFMPEG encoded and the output format I go to which are both .mov files, aac audio and x264 (ffmpeg) h264 (final cut). 

Is this an issue with the jump from x264 to h264?

Does anyone have a similar workflow to share advice on?

I'm using this command: 
```
ffmpeg -i 00040.MTS -acodec libfaac -ar 44100 -ab 120k -vcodec libx264 -vb 5000k -s hd1080 -vpre medium -threads 0 outtest.mov
```

The input file is 29 seconds long and when I drag it into my sequence it's taking 25 minutes just to render initially so I can edit in the sequence. This never happens when importing the same footage directly from the camera onto my laptop, it's always ready to edit when I put it onto the sequence.

edit: here is what a Final Cut imported video's info looks like.
```


ffmpeg -i after.mov
FFmpeg version SVN-r23386, Copyright (c) 2000-2010 the FFmpeg developers
  built on May 29 2010 18:04:42 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.16. 0 / 50.16. 0
  libavcodec    52.72. 0 / 52.72. 0
  libavformat   52.67. 0 / 52.67. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 2997.00 (2997/1) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'after.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 537199360
    compatible_brands: qt  
  Duration: 00:00:09.77, start: 0.-33375, bitrate: 87204 kb/s
    Stream #0.0(eng): Video: Apple Intermediate Codec, 1920x1080, 85901 kb/s, PAR 1:1 DAR 16:9, 29.97 fps, 29.97 tbr, 2997 tbn, 2997 tbc
    Stream #0.1(eng): Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
    Stream #0.2(eng): Data: tmcd / 0x64636D74, 0 kb/s

```

edit: here's my revised command that brought the same clip from 25 minutes down to 14

```
ffmpeg -i 00040.MTS -acodec pcm_s16le -ar 48000 -ab 1500k -vcodec libx264 -vb 15000k -aspect 16:9 -r 29.97 -s hd1080 -vpre medium -threads 0 outtest.mov
 
```

---

