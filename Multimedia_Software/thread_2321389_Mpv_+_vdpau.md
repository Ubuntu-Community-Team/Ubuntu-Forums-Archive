---
title: "Mpv + vdpau"
date: 2016-04-22
forum: Multimedia Software
---

### Post by cesdo2 on 2016-04-22
Hello. MPV plays youtube videos, which quality is better then 720p, using software decoding.

> $ mpv [https://www.youtube.com/watch?v=4u-U0bOgs94](https://www.youtube.com/watch?v=4u-U0bOgs94)
Warning: option --subcp was replaced with --sub-codepage and might be removed in the future.
Playing: [https://www.youtube.com/watch?v=4u-U0bOgs94](https://www.youtube.com/watch?v=4u-U0bOgs94)
 (+) Video --vid=1 (*) (h264)
 (+)  Audio --aid=1 --alang=und (*)  'videoplayback?pl=20&mn=sn-pivhx-n8vs&ip=193.151.224.40&mm=31&id=o-AOZN1yg-J767ed6XN575aG8ZsXbSIC9XH9f1iWjEafV7&fexp=9406003%2C9416126%2C9416891%2C9417580%2C9419452%2C9419546%2C9420452%2C9421544%2C9422596%2C9423038%2C9423194%2C9426927%2C9428398%2C9429261%2C9431012%2C9431865%2C9432604%2C9432683%2C9433097&sparams=clen%2Cdur%2Cgir%2Cid%2Cinitcwndbps%2Cip%2Cipbits%2Citag%2Ckeepalive%2Clmt%2Cmime%2Cmm%2Cmn%2Cms%2Cmv%2Cpl%2Crequiressl%2Csource%2Cupn%2Cexpire&itag=258&ms=au&initcwndbps=1805000&mv=m&dur=218.623&mt=1461147525&ipbits=0&sver=3&key=yt6&signature=5B6F646E9E11BE0B8E8245B1FF1A741DD23E69CA.AABE4F3C44DA598210C958ED7D4B8C4021DD6E43&clen=10527872&upn=SG6loQNrT2o&source=youtube&gir=yes&mime=audio%2Fmp4&requiressl=yes&keepalive=yes&expire=1461169191&lmt=1459392988216236&ratebypass=yes'  (aac) (external)
AO: [pulse] 48000Hz stereo 2ch float
**Using software decoding.**
**VO: [opengl] 3840x2160 yuv420p**
(Paused) AV: 00:01:36 / 00:03:38 (44%) A-V:  0.000 Dropped: 26 Cache: 10s+44MB
Saving state.

mpv.conf:

> $ cat ~/.config/mpv/mpv.conf
**--ytdl-format=bestvideo+bestaudio**
save-position-on-quit=yes
fullscreen=yes
**hwdec=vdpau**
subcp=enca:ru:utf8

How can I play them with hardware decoding using vdpau? 

Ubuntu 14.04 LTS 32-bit, Nvidia GeForce GT 440 512 Mb GDDR5, Nvidia binary driver 352.63 from nvidia-352-updates.

---

### Post by SeijiSensei on 2016-04-22
Add "vo=vdpau" to mpv.conf.

---

### Post by mc4man on 2016-04-22
Just to mention - 
here on https/http streams I like mpv to open right away rather than wait on stream buffering. (even though it's just an empty window.
That can be done via a protocol section(s) in mpv.conf -
 
```
[protocol.http]
force-window=immediate

[protocol.https]
force-window=immediate
```

---

