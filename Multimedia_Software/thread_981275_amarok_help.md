---
title: "amarok help"
date: 2008-11-13
forum: Multimedia Software
---

### Post by Quicksilver21 on 2008-11-13
i have about 35gb of music on my NTSF partition but i cant find it in amarok, is there a way to have amarok recognize the music from my other partition?

---

### Post by teh2 on 2008-11-13
I haven't yet done this with an NTFS partition, but what I did with my ext3 partition was, I mounted it inside of /home/tom/Music so that it looks like /home/tom/Music/MusicLibrary and then made sure that Amarok was set to scan /home/tom/Music, and it picked it up automatically.

---

### Post by KevNice on 2009-01-31
I had a similar problem and used a similar solution. It wasn't scanning music into either Amarok or Exaile. At first I had it as a /media/storage partition, but then I switched it to /home/storage and it scanned correctly.

---

