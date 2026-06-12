---
title: "MythTV recording playback on VLC &quot;clock gap&quot; erorrs"
date: 2009-11-30
forum: Multimedia Software
---

### Post by mrdek11 on 2009-11-30
Hi there!

I've been trying to transcode and stream some of my mythtv recordings through VLC using the following command: ```
vlc -I dummy -v 2038_20091117103000.mpg --sout '#transcode{width=320,height=240,vcodec=h264,vb=768,acodec=mp4a,ab=128,channels=2}:standard{access=http,mux=ts,url=:8080}'
```

This works great, but after about 20 seconds of streaming, it begins spitting out:
```
[00000413] main input warning: feeding synchro with a new reference point trying to recover from clock gap
[00000413] main input warning: clock gap, unexpected stream discontinuity

```
over and over, and both audio and video stutter for the rest of the stream.

I tested the stream without transcoding to see if the problem is coming from there:
```
vlc -I dummy -v 2038_20091117103000.mpg --sout '#standard{access=http,mux=ts,url=:8080}'
```
This stream appears and sounds smooth, but it is still constantly getting "clock gap" errors.

I don't get any of these errors when running either command with a file not recorded with MythTV.

Does anybody have any experience with this? I'd appreciate any help I can get.

Thanks,
Derek

[edit]Does MythTV make a "flag" for the commercials in the actual video file? I just realized that these "clock gap" errors begin at the first "black screen" (either cutting to or from commercials)[/edit]

---

### Post by mrdek11 on 2010-01-14
Alas, I'm still looking for an answer to this question.

Does anybody know why these clock gap errors are occurring or how to fix them?
I would greatly appreciate any tips or suggestions you might have to give.

Thanks,
Derek

---

