---
title: "SMplayer outputs no video with some files"
date: 2011-01-05
forum: Multimedia Software
---

### Post by sjvega on 2011-01-05
I'm having this problem with SMplayer where it just outputs sound, no video whatsoever , I tried running Mplayer directly and I've seen the logs of SMplayer and the only thing it says is : 

[20:23:56:697] MplayerProcess:: parseLine: '[h264 @ 0x89a61c0]no frame!'
[20:23:56:697] MplayerProcess:: parseLine: 'Error while decoding frame!'
[20:23:56:698] MplayerProcess:: parseLine: '[h264 @ 0x89a61c0]AVC: nal
over and over again.
The video itself its fine, I can watch it in VLC, but since it some time stutters and the images garbles, it get on my nerves... besides this video isn't the first one to give this problem.
 I've tried changing the video output driver, but I've had no success.
Does anybody has an idea for solving this problem? , I've looked around but couldn't find anything.
Sorry for the bad english, and thanks in advance!

---

### Post by mc4man on 2011-01-05
It may or may not be related to the default demuxer (I don't use smplayer here

Possibly take a glance thru this thread (gets to the point around post 7
[http://ubuntuforums.org/showthread.php?t=1653240](http://ubuntuforums.org/showthread.php?t=1653240)

---

### Post by sjvega on 2011-01-05
Thanks for the reply. 
Apparently as someone on that thread said there is a bug on the default demuxer for certain codecs on older versions of mplayer, I've just updated it and it works as a charm.
Thanks!

---

