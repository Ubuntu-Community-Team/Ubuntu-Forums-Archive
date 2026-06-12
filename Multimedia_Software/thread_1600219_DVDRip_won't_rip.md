---
title: "DVDRip won't rip"
date: 2010-10-18
forum: Multimedia Software
---

### Post by 98cwitr on 2010-10-18
I've never used this sofware before so bear with me. I installed it via Software Center, put DVD in, created a new project, went to the RIP Title tab, selected all the titles, clicked RIP Selected Titles, Duration went to 00:06 seconds and stopped. Nothing to indicate an error in the logs. What's wrong here?

---

### Post by 98cwitr on 2010-10-18
Update: Disk is encrypted...mplayer wont play it, vlc wont play it...PS3 will.

Solved for the ripping at least :)

```

sudo apt-get install libdvdread4 debhelper fakeroot
sudo /usr/share/doc/libdvdread4/install-css.sh

```

---

### Post by cascade9 on 2010-10-18
Install libdvdcss2 if you havent already ;)

---

### Post by 98cwitr on 2010-10-19
> **cascade9 said:**
> Install libdvdcss2 if you havent already ;)

already got it ;)

---

