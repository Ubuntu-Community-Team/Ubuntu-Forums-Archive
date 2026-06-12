---
title: "So I need to change multimedia defaults on multiple Ubuntu boxes..."
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by The Keeper on 2008-01-17
I'd like to set VLC as the default video and audio player on multiple user accounts and multiple computers. Is there a good terminal command I could run on each computer to set the defaults? This really should take effect on every association Totem or Rhythmbox has taken by default.

Is there an easy solution at all?

Thanks for advice.

---

### Post by The Keeper on 2008-01-26
I guess no then? :( Setting default media player on multiple computers and multiple user accounts is too much a pain in the **** to do per-file type.

---

### Post by tgalati4 on 2008-01-26
gnome-volume-properties --help

Although there do not appear to be any switches to make the desired changes such that you could write a script to do it automatically.  Because the changes are written to the gconf registry, I don't see how you could do otherwise than on a per-user basis.

Linux Mint 4 comes with a more popular selection of applications that open by default so less configuration is needed.

---

