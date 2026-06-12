---
title: "How do I set volume keys to not control PCM?"
date: 2011-03-22
forum: Multimedia Software
---

### Post by Vostrocity on 2011-03-22
Right now, it controls both Master and PCM, resulting in weird volume increments. I want PCM to stay at 50 and only change Master with my volume keys. Thanks for the help.

---

### Post by lidex on 2011-03-24
Does this help:
[http://ubuntuforums.org/showthread.php?t=1305889](http://ubuntuforums.org/showthread.php?t=1305889)

---

### Post by Vostrocity on 2011-03-24
Yes, that is exactly what I needed! However, I now get the crackling sound mentioned in that thread, and the line I'm supposed to comment out to eliminate it has since been removed from alsa-base.conf. It seems like I'm supposed to disable a power-save feature?

---

### Post by Vostrocity on 2011-03-24
You know, actually I managed to fix that by just choosing the other Output option in Sound Prefs. :)

---

