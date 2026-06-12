---
title: "HDMI, nvidia and video performance"
date: 2010-04-24
forum: Multimedia Software
---

### Post by Tenn lynx on 2010-04-24
Hey

I have noticed that, using nvidia's latest drivers, HDMi output to my 32" LCD (1920x1080) and totem or vlc, the video on my LCD gets a bit "choppy" when the image changes faster.. some bars start appearing on the moving parts of the image.. like the system is having trouble rendering the video. This doesn't happen on my laptop screen even when both displays are running at the same time.

Also, this problem doesn't appear in windows 7, everything works perfectly there with one odd thing... the picture gets "choppy" on the laptop screen when I'm running both at the same time.

It's not that noticeable, but I can tell the difference between windows and ubuntu in quality and it's annoying me :)

Ideas?

Thanks
Tenn

PS
also another issue here: 
[http://ubuntuforums.org/showthread.php?t=1461452]("http://ubuntuforums.org/showthread.php?t=1461452")

---

### Post by cchhrriiss121212 on 2010-04-24
If you are viewing 720p/1080p files you will want to use [vdpau]("http://ubuntuforums.org/showthread.php?t=1037625") which makes use of nvidia hardware acceleration.
If this is occurring with sd video and regular dvds then you should try disabling compiz.

---

### Post by vthiru on 2010-04-24
> **cchhrriiss121212 said:**
> If you are viewing 720p/1080p files you will want to use [vdpau]("http://ubuntuforums.org/showthread.php?t=1037625") which makes use of nvidia hardware acceleration.
If this is occurring with sd video and regular dvds then you should try disabling compiz.
Ok, I shall try that out. Thanks [cchouhrriiss121212]("http://ohioloco.ubuntuforums.org/member.php?u=948514"). Also, what would you do if you had an ATI GPU and the same problem?

---

### Post by cchhrriiss121212 on 2010-04-24
> **vthiru said:**
> Ok, I shall try that out. Thanks [cchouhrriiss121212]("http://ohioloco.ubuntuforums.org/member.php?u=948514"). Also, what would you do if you had an ATI GPU and the same problem?
Swap it for an nvidia one :lolflag:. 
But you could also try using [mplayer-mt]("http://ubuntuforums.org/showthread.php?t=1049449") which allows you to use multiple cores, which should give you a similar performance boost.

---

