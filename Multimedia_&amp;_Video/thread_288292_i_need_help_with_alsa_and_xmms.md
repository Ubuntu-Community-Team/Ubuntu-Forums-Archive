---
title: "i need help with alsa and xmms"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by sundaymars on 2006-10-29
Every time I try to open an audio file in XXMS Music Player, I get a warning that says "failed to open audio output: ALSA 1.2.10 output plugin" Does anyone know anything I can do to alleviate this? Thank you in advanced.

---

### Post by pacer on 2006-11-01
I had the same problem. 
I found what ESD is also runnig. 
see if esd process exists. if yes then kill it and remove from start-up 
killall esd

---

