---
title: "[SOLVED] How to play a short audio clip from BASH"
date: 2008-07-21
forum: Multimedia Software
---

### Post by minus24 on 2008-07-21
What's the best way to play a short audio clip (e.g., an alarm bell) from a BASH script?  At the moment I'm using totem, but it's overkill to have its GUI start up!  I'd prefer just a simple command for one-off playing of an audio clip.

---

### Post by ron999 on 2008-07-21
Hi
You could use mplayer, like this:-
```
mplayer <filename>
```

---

### Post by minus24 on 2008-07-22
Thanks.  Suppressing stdout and stderr, the following worked just fine:

#!/bin/bash
(sleep ${1:-240}; mplayer /usr/share/sounds/phone.wav >/dev/null 2>&1) &

---

### Post by edtakken on 2012-11-28
> **minus24 said:**
> Thanks.  Suppressing stdout and stderr, the following worked just fine:

#!/bin/bash
(sleep ${1:-240}; mplayer /usr/share/sounds/phone.wav >/dev/null 2>&1) &

In OS X the player command is   afplay
More at  [http://hints.macworld.com/article.php?story=20081002080543392](http://hints.macworld.com/article.php?story=20081002080543392)

---

