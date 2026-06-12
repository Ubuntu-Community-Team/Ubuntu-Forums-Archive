---
title: "[SOLUTION] no audio after yesterday's updates"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by jcraveiro on 2007-04-14
```
sudo gpasswd -a username audio
```
(replacing *username* for your username)

and reboot. Worked for me (snd-intel8x0).

Before trying, you might want to compare the output of
```
aplay -l
```
and
```
sudo aplay -l
```

In my case, running as normal user gave me no soundcards, unlike running with sudo.

---

### Post by nagius on 2007-05-10
Many thanks for your advise your solution work perfectly. tried everything but this work fine.

---

