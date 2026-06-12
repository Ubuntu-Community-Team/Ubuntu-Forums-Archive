---
title: "MEncoder DVDRIP"
date: 2012-07-26
forum: Multimedia Software
---

### Post by JamesZhang on 2012-07-26
When ripping a DVD with MEncoder, the progress goes over 100%, why is this happening and how can I get an accurate progress. 

i.e: MEncoder -dvd-device "e:" "dvdnav://17" -of lavf -lavfopts format=mp4 -ofps 25 -ovc x264 -x264encopts threads=1:keyint=300:bitrate=1024 -oac lavc -lavcopts acodec=aac:abitrate=128 -srate 44100 -channels 2  -o "x264.mp4"

---

### Post by TheFu on 2012-07-26
> **JamesZhang said:**
> When ripping a DVD with MEncoder, the progress goes over 100%, why is this happening and how can I get an accurate progress. 

i.e: MEncoder -dvd-device "e:" "dvdnav://17" -of lavf -lavfopts format=mp4 -ofps 25 -ovc x264 -x264encopts threads=1:keyint=300:bitrate=1024 -oac lavc -lavcopts acodec=aac:abitrate=128 -srate 44100 -channels 2  -o "x264.mp4"

I strongly suspect that "e:" is not the DVD device under Ubuntu.  That looks like a Windows drive letter. More likely, it is "/dev/dvd", but the mencoder man page says it is optional.

A simplier command is
```
$ mencoder dvdnav://17  -ovc x264 -x264encopts threads=1:keyint=300:bitrate=1024 -oac  lavc -lavcopts -oac copy  -o  "x264.mp4"
```

Then if that works, I'd try adding more complex parts back in as needed.
OTOH, I've never attempted to rip a DVD using mencoder. I always use vobcopy first.

---

