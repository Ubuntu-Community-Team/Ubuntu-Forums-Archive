---
title: "no sound all of a sudden"
date: 2012-07-26
forum: Multimedia Software
---

### Post by bobipod on 2012-07-26
i'm running a dell inspiron 1520 with ubuntu 12.04.

I'm trying to watch youtube and have discovered i have no sound.  I tried music through vlc and still no sound.

Any ideas? 

I've been through sound settings and everything is active.

---

### Post by ajgreeny on 2012-07-26
Run ```
alsamixer
``` in terminal and check that the levels of outputs are not set too low or muted.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
In capture page use spacebar to enable the different input devices (mic, line, CD, video).
Esc will save and exit.

---

### Post by bobipod on 2012-07-27
thanks for the help

---

### Post by bobipod on 2012-07-27
any ideas why it keeps re setting to zero volume?

---

### Post by bobipod on 2012-08-03
bump for some help.

---

### Post by bobipod on 2012-08-11
back up again for any solutions?

---

