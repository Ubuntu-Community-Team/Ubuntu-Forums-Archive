---
title: "Cowon D2 read only state"
date: 2011-05-29
forum: Multimedia Software
---

### Post by homerwookey on 2011-05-29
Hi all, hoping you might be able to help once more, 
My cowon D2+ has become read only and I would like to know how to change this so i can transfer tracks to it from my music library.
Ive had a good look on the site and havent been able to find anything relevant so far.
running ubuntu 10.04
Thanks in advance

---

### Post by creontu on 2011-05-29
Hi [homerwookey]("http://ubuntuforums.org/member.php?u=634569"),
I also have D2 - no problems with it so far. Any time I had a problem(happened once or twice) I just reseted it with the small button located between the mini-usb and charger port. Is it the extension card of the unit memory you cannot write to? If this is the card, then chances are the unit is not the one to blame. Worked with 10.04 now worx with 11.04.

---

### Post by homerwookey on 2011-05-29
Thanks, I have also had to use this on a few occasions, the problem is that it is recognised as a read only file system, so I need to be able to change this to read/write so I can transfer files. It is the internal drive.

---

### Post by creontu on 2011-05-29
Some googling [suggests this]("http://iaudiophile.net/forums/showthread.php?t=23549"), otherwise there's always warranty and service from Cowon... wish you luck. I'll keep an eye on this thread, as mine could be also in danger :)

---

### Post by homerwookey on 2011-05-30
I found that link as well, I've just been trying to get hold of a windows machine to check, which is why in the meantime I thought I'd post this thread out there to see if the problem was something else...
Anyway I got hold of a windows machine this morning, and would you believe it, after performing the checkdisk and safely remove hardware, now I can read/write again! very bizarre as I dont use windows, but I'm not complaining! Thanks

---

### Post by Chronon on 2011-05-30
Damaged file systems are usually mounted as read-only to prevent causing further damage.  If this happens again you can run the appropriate fsck from Ubuntu to try to fix it.

---

