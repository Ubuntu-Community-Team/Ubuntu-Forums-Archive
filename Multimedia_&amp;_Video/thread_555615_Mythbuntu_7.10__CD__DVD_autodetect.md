---
title: "Mythbuntu 7.10 : CD / DVD autodetect"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by Sdx1978 on 2007-09-20
Hi all,

another thread for a different subject.
Like said on other thread I installed Mythbuntu 7.10 on a PC as mediacenter.

When inserting a CD or DVD, no autodetect occurs. I can't play neither a CD nor a DVD !!
Quite annoying !

Any idea how to fix this ?

For other task like burning (K3B), or transferring data from CD/DVD, I don't have any problems.

Thanks in advance !

---

### Post by Sdx1978 on 2007-09-25
Hello again,

nobody is using mythbuntu as a CD/DVD player ? If yes, how do u do to automatically play a CD or a DVD ?

Thanks !!

---

### Post by superm1 on 2007-09-26
You need to setup the automatically mounting disks option in mythtv.  It's off by default.  You also need libdvdcss2 installed.

---

### Post by Sdx1978 on 2007-09-26
Hi,

I found out last night what was my problem.
Mythbuntu setup used /dev/cdrom and /dev/dvd, while my drive was on /dev/cdrom1 and /dev/dvd1

It appears not to have auto detection for those parameters in Mythbuntu.


Last problem now:
Even if "automatic play" is activated in Mythbuntu, the only way to play a DVD is to go manually in the DVD menu and use "Play a DVD" ...
So from main menu (first interface), I can't play a DVD.

---

