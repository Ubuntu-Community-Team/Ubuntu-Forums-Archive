---
title: "line-in and audio"
date: 2008-04-11
forum: Multimedia &amp; Video
---

### Post by drascus on 2008-04-11
I have been trying to recored from my line-in input like crazy and can't figure it out. Someone in another post suggest enabling analog form alsamixer but I can't figure out how to do that I tried alsamixer -D analog but got back this error: 

ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL analog
alsamixer: function snd_ctl_open failed for analog: No such file or directory

any ideas how to record from line in?? I know my line in works because I can hear audio through it.

---

### Post by deadgobby on 2008-04-11
what programs are you using? Have you  tried Audacity? If you are hearing sound there the speakers. It should record.

---

### Post by drascus on 2008-04-11
yes I have tried audacity and sound recorder and it didn't seem to work for either.

---

### Post by deadgobby on 2008-04-11
Try OSS instead of ALSA and see what come up. 
Gobby

---

