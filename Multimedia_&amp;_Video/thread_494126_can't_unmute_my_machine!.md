---
title: "can't unmute my machine!"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by orengolan on 2007-07-06
ubuntu 7.04 refuses to unmute. i try ctrl+t....but it's still on mute.

anyone?

---

### Post by ugm6hr on 2007-07-06
Try
```
alsamixer
```
Then use "M" to unmute each channel (left / right arrows to select).

---

### Post by scholzilla on 2007-07-06
Alternatively, this could relate to a known bug in the kernel upgrades. For me to avoid this muting, I had to reinstall 7.04, then use apt-get upgrade to do my upgrades. This withholds all updates to the kernel while upgrading everything else.

---

