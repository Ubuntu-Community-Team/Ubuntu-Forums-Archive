---
title: "No sound, just static"
date: 2008-11-16
forum: Multimedia Software
---

### Post by kyle99 on 2008-11-16
I'm a complete linux newbie running Ubuntu 8.10. Whenever sound is supposed to come out of my speakers, it's just static. I have tried putting headphones in place of speakers, but still static, and the speakers work in Windows, so... Post if you need more info, I don't really know what more to post...

Thanks a ton in advance!

---

### Post by psyke83 on 2008-11-16
It's because your PCM volume is set to 0% (or muted).

Turn the volume up via alsamixer:
```
$ alsamixer -Dhw
```

Also see the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

---

### Post by kyle99 on 2008-11-17
> **psyke83 said:**
> It's because your PCM volume is set to 0% (or muted).

Turn the volume up via alsamixer:
```
$ alsamixer -Dhw
```

Also see the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

Haha, worked perfectly, thanks a ton :)

---

### Post by MystaMax on 2008-11-18
ha, I had the same problem. I tried alsamixer, but didn't know about the "-Dhw" flags. Should of read the man pages.... Thanks anyway.

---

### Post by Crafty Kisses on 2008-11-18
Can you please mark the thread as solved. :)

---

