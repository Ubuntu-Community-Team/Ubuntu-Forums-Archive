---
title: "sound disappearing in smplayer"
date: 2010-06-05
forum: Multimedia Software
---

### Post by pickarooney on 2010-06-05
I recently upgraded mplayer and smplayer to fix a bug with subtitle rendering in the repos version. From the PPA/SVN I have 
```
This is SMPlayer v. 0.6.9 (SVN r3447) 
```

However, sound keeps disappearing in smplayer and won't come back until I reboot. Sound is still present in all other players including mplayer.

Running smplayer from the command line gives no output so I don't know what night be wrong. Volume is at max and not muted.

---

### Post by pickarooney on 2010-06-05
Never mind - the audio driver had somehow set itself to OSS. Hard to imagine why this keeps happening.

---

