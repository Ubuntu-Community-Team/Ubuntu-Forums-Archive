---
title: "[SOLVED] Find out what region a dvd is?"
date: 2008-08-09
forum: Multimedia Software
---

### Post by kamitsukai on 2008-08-09
Is there a way to find out what region a dvd is from ubuntu? as i dont have any non multi region dvd players to test a couple of discs...:lolflag:

PS: i know region codes don't matter on ubuntu!

---

### Post by mc4man on 2008-08-09
Many of the players will report the region of the disk, particularly when opened from a terminal. Try vlc.
ex.
> oug@doug-desktop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: LIVEFREE_OR_DIEHARD_BRANCH
libdvdnav: DVD Serial Number: 37418D50
libdvdnav: DVD Title (Alternative): LIVEFREE_OR_DIEHARD_BRANCH
libdvdnav: Unable to find map file '/home/doug/.dvdnav/LIVEFREE_OR_DIEHARD_BRANCH.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1


---

### Post by kamitsukai on 2008-08-10
thanks very much :)

---

### Post by lisati on 2008-08-10
Presumably the cover is misplaced, or the region code missing or obscured....

---

### Post by kamitsukai on 2008-08-10
> **lisati said:**
> Presumably the cover is misplaced, or the region code missing or obscured....

Nope they genuinely don't say:) not all dvd's do, turns out they were multi region anyway:lolflag:

---

