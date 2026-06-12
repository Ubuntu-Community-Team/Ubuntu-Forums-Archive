---
title: "Videos Players"
date: 2008-10-10
forum: Multimedia Software
---

### Post by mschraier on 2008-10-10
I am running Ibex Beta and can only get VLC to work.  Drgaon player says there is no media in the drive and Kaffeine says I need to install libdvdcss.  It is installed and still not working.  Any idea?????     :guitar::guitar:

---

### Post by TenPlus1 on 2008-10-10
Try enabling the medibuntu repos:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

then going to [www.getdeb.net](www.getdeb.net) and downloading the latest SMPlayer which plays everything perfectly for me...

---

### Post by mschraier on 2008-10-10
I have accessed Medubuntu.  Its just wierd that only VLC works.  I will try SMplayer.  Do I need to install Mplayer first or will getdeb be all I need?

---

### Post by SuperSonic4 on 2008-10-10
MPlayer is a dependency of SMPlayer (the latter is a frontend to the former)

If you use Adept you should be ok

---

### Post by mc4man on 2008-10-10
> Kaffeine says I need to install libdvdcss. It is installed and still not working. Any idea
Kaffeine also needs libxine1-ffmpeg and in it's settings (xine engine parameters -> media) the dvd.device should be changed from the default of /dev/dvd to /dev/scd[COLOR="Red"]x[/COLOR], where x is your drive (typically scd0 or scd1
The libdvdcss error message is somewhat generic.

---

