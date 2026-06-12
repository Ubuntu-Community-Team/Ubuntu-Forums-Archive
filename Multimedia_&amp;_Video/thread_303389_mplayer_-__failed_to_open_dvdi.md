---
title: "mplayer -  failed to open dvd://i"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by tinker123 on 2006-11-20
Hi.  I just installed mplayer into my Ubuntu 6.10 installation.  When I tried to play a dvd I got this error message;


failed to open dvd://i


I take it that this is not the right path to my dvd?  How can I correct this.  Thanks in advance.

---

### Post by tinker123 on 2006-11-23
mplayer is looking for dvds at /dev/dvd/,  Ubuntu maps it elsewhere.  I took the dvd path in /etc/fstab, opened up mplayers config dialog, and inserted that path.  It works now.

---

