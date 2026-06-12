---
title: "[SOLVED] Ripped DVDs stored on frontend?"
date: 2009-01-04
forum: Mythbuntu
---

### Post by novice_geek on 2009-01-04
Hey everyone,

I've been playing with my new (and still broken... [http://ubuntuforums.org/showthread.php?t=1024280](http://ubuntuforums.org/showthread.php?t=1024280)) MythTV install and I have my laptop setup as a remote frontend.  I tried ripping a few of my DVDs on my laptop, and then took a look on the backend and saw that they do show up, but disk usage on the backend is 4.8MB (yes, MB).  After some digging around, I found that they are stored in /var/lib/mythtv/videos on my laptop, and are not on the backend (yet the backend sees them and has the cover art that I specified from using the lookup feature).

Does anyone know how to prevent this from happening?  I REALLY don't want to use just the backend to rip DVDs.

And if anyone gets board, see if you can help me with the previous thread.  The Schedules Direct thing and trying to set a channel for S-Video (?) is driving me nuts.

Thanks!

---

### Post by rhpot1991 on 2009-01-05
> **novice_geek said:**
> Hey everyone,

I've been playing with my new (and still broken... [http://ubuntuforums.org/showthread.php?t=1024280](http://ubuntuforums.org/showthread.php?t=1024280)) MythTV install and I have my laptop setup as a remote frontend.  I tried ripping a few of my DVDs on my laptop, and then took a look on the backend and saw that they do show up, but disk usage on the backend is 4.8MB (yes, MB).  After some digging around, I found that they are stored in /var/lib/mythtv/videos on my laptop, and are not on the backend (yet the backend sees them and has the cover art that I specified from using the lookup feature).

Does anyone know how to prevent this from happening?  I REALLY don't want to use just the backend to rip DVDs.

And if anyone gets board, see if you can help me with the previous thread.  The Schedules Direct thing and trying to set a channel for S-Video (?) is driving me nuts.

Thanks!

This is because the backend stores the info in the database, and the frontend stores the file.  You want to use some sort of a network share, attach the frontened to it and then you can rip to the backend.

I'd recommend NFS: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by novice_geek on 2009-01-05
> **rhpot1991 said:**
> This is because the backend stores the info in the database, and the frontend stores the file.  You want to use some sort of a network share, attach the frontened to it and then you can rip to the backend.

I'd recommend NFS: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)


I just tried NFS, and it's working great now.  Thanks!

---

