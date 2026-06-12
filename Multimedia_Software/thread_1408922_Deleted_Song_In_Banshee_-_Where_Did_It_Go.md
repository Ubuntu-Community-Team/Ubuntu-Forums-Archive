---
title: "Deleted Song In Banshee - Where Did It Go?"
date: 2010-02-17
forum: Multimedia Software
---

### Post by biggsjm on 2010-02-17
I'm cleaning up my music library and deleting duplicates and during that process I accidentally deleted the wrong song. Is there some way to undo this process? Banshee gave me no warning, and the trash is empty. I'm assuming there's a command I can use to recover the file, but as I'm a complete noob, I need some assistance. 

Thanks!

---

### Post by x33a on 2010-02-17
Are you sure the song got deleted from your hard drive. Maybe it just got removed from the library.

---

### Post by biggsjm on 2010-02-17
Yeah, that was the first thing I checked. Not sure where it went, but its not in the artist folder.

---

### Post by x33a on 2010-02-17
Give this a try to recover the song.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I think it is available in the repos.

---

### Post by biggsjm on 2010-02-17
I got it back. I didn't try your tool (but appreciate the assistance). I actually found a backup that had a copy of the song.

I'll raise a bug with Banshee . . . unrecoverable deletes are never a good thing!

Thanks for your help!

---

### Post by kidux on 2010-02-17
It's not a bug, it's part of how Banshee manages your music. You interact directly with the file system as opposed to a program like Amarok that uses symlinks. Delete it out of your library in Banshee, and it deletes it from your HDD.

---

