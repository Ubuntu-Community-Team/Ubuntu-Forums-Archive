---
title: "colors don't display correctly when playing movie"
date: 2008-05-10
forum: Multimedia Software
---

### Post by spyder0080 on 2008-05-10
Hello all,

I did a clean install of Hardy a few weeks ago and I noticed that when I play movies (either off of files, dvd's, or streaming video) the colors are off. Everything else, the colors are fine. If someone could help me, I would really appreciate it!

Thanks!

---

### Post by mc4man on 2008-05-10
ck. here
[http://ubuntuforums.org/showthread.php?t=769209](http://ubuntuforums.org/showthread.php?t=769209)

---

### Post by spyder0080 on 2008-05-10
thanks a lot! the colors display correctly now!

---

### Post by mc4man on 2008-05-10
You may find it better to install totem-xine (leave totem-gstreamer installed). Totem-xine is a better player overall and shouldn't cause this issue. If you do so after installing run in the terminal ```
sudo update-alternatives --config totem
``` then at the prompt choose 2 and totem-xine will replace totem-gstreamer as your active totem player.

---

