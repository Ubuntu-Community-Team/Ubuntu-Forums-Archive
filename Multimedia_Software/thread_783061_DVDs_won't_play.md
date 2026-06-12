---
title: "DVDs won't play"
date: 2008-05-05
forum: Multimedia Software
---

### Post by TorchlightJay on 2008-05-05
Hello,
  I have an HP tx2000z running Ubuntu 8.04 LTS. I have libdvdcss1.2.9 installed but I can't open dvds. I always get some weird message.

The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (/media/scd0)

Now I have changed /media/scd0 to a variety of things (it started out as /dev/dvd). I just don't know whay i can't play dvds. Any ideas?

---

### Post by Zorael on 2008-05-05
If you open up /media/scd0 in a file manager, is there content?

edit: I also heard some rumor that you had to run **sudo /usr/share/doc/libdvdread3/install-css.sh** in a terminal to get it working.

---

