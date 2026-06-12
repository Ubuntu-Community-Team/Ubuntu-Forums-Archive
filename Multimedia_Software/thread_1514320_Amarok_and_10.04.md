---
title: "Amarok and 10.04"
date: 2010-06-20
forum: Multimedia Software
---

### Post by mlacomb on 2010-06-20
I'm having a weird issue.  After installing packages to get the various audio players to "play" mp3s  (vlc and Amarok both play .mp3 files just fine now) I ran into a weird issue with Amarok.

I have an nfs share that is mapped on the culprit machine (/share/mp3) and as above, can be played from with either vlc or Amarok.  The issue is that I have Amarok set to scan this folder as part of it's collection; when I "update collection" it spins for 5-10 minutes (giving a moving progress bar) but when I go to "Local collection" on the main page, it says 0 albums.

I can browse and play using the folders option just fine, but why do I not see anything in the Local collection?  Or am I doing it wrong?

---

### Post by phildopus on 2010-06-25
I'm having the same problem.  I thought that maybe it had something to do with my collection being symlinked from another partition, but I pointed the collection straight at the directory without the symlink and it still didn't work.

---

### Post by Beelzebud on 2010-06-25
I've never been able to get Amarok to save my library under 10.04.   I've built the database a couple of times, and it never saved.   I finally gave up and started using Rythmbox.

---

### Post by Jeffa on 2010-07-12
I'm having the exact same issue. Anyone find a resolution? 

Thanks!

---

### Post by Jeffa on 2010-07-13
See [this thread]("http://ubuntuforums.org/showthread.php?t=1529591") for a solution. 

Hope it helps everyone.

---

