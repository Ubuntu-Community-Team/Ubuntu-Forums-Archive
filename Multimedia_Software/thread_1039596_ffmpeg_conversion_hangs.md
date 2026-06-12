---
title: "ffmpeg conversion hangs"
date: 2009-01-14
forum: Multimedia Software
---

### Post by romeyde on 2009-01-14
just about got my m2t to mp4 ffmpeg conversion script hashed out for making ps3 compatible videos.   it runs nightly at 3am and converts any shows recorded by tuner that day.   today, I came home from work and found ffmpeg hung for 12+ hours with cpu pegged at 100% the entire time.   manually tried running ffmpeg on the same file and it happened again.   see anything here that i can adjust to keep this from happening with ffmpeg?  

command that is hung.

/usr/local/bin/ffmpeg -i /data/media/recordings/foo.m2t -y -vcodec libx264 -acodec libfaac -f mp4 -mbd rd -flags 4mv+aic+qprd+mv0 -cmp 2 -subcmp 2 -level 41 -bf 3 -ac 2 -b 1050kb -ab 192kb -s hd720 -copyts -threads 0 /data/media/recordings/bar.mp4

---

### Post by FakeOutdoorsman on 2009-01-14
What release of ffmpeg are you using: from the repository or self-compiled?

---

### Post by romeyde on 2009-01-14
> **FakeOutdoorsman said:**
> What release of ffmpeg are you using: from the repository or self-compiled?

self compiled per your earlier suggestion.  :)

FFmpeg version SVN-r16536, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52.10. 0 / 52.10. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 11 2009 11:10:52, gcc: 4.3.2


Tried the same file again and it seems to get stuck on this frame, just repeats over and over.  I get that perhaps it's a bad file or something, but seems like ffmpeg could/should detect that and bypass the frame?

frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   [mpeg2video @ 0x96c8840]invalid mb type in I Frame at 115 31
[mpeg2video @ 0x96c8840]concealing 174 DC, 174 AC, 174 MV errors
frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s   frame=67526 fps= 29 q=31.0 size=  346561kB time=1126.41 bitrate=2520.4kbits/s

---

### Post by FakeOutdoorsman on 2009-01-14
Looks like a problem with that particular input file, but I've never seen this error before.  You could ask the [ffmpeg-user](http://ffmpeg.org/mailinglists.html) mailing list what they think is wrong.  Make sure you give them your exact ffmpeg command and the full output (you can exclude repetitious output).  Or go to the #ffmpeg IRC channel and ask.  Use a [pastebin](http://ffmpeg.pastebin.com/) service for your input and output if you use IRC.

---

