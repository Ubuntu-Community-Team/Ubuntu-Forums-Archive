---
title: "Hoe to watch mythtv files (i.e. 2091_20090929200000.mpg) not in database?"
date: 2010-09-23
forum: Mythbuntu
---

### Post by yonkiman on 2010-09-23
So mythbuntu system disk crashed and when I'm all done rebuilding everything I know I will have some orphaned TV files, some of which I'd like to watch.

Byt when I try to watch any of the files in VLC or even inside Myth (watching them using "Watch Videos"), they place for maybe a second and then hang up.  I don't understand how/why MythTV is happy to play them if it knows they are a recorded TV program and they're synced in the database, but has no idea what to do with the files if I try to play them on their own.  This has always puzzled me, and now I'd really like to understand so I can watch some of my orphaned shows.

Cheers,
Fred

---

### Post by Hobgoblin on 2010-09-24
It's been a while since I had MythTV up and running but the files used to play fine for me in any media player.

---

### Post by andree_b on 2010-09-24
It should just play in VLC or via "Watch Videos".
It rather seems your file got corrupted during the disk crash...

---

### Post by LowSky on 2010-09-24
if the video doens't play using vlc it is most likely corrupted.

if the video is just stuttering, try changing the deinterlace option in VLC I find it helps with recordings that are done in 1080i

---

### Post by nickrout on 2010-09-25
what does the log file say?

---

### Post by yonkiman on 2010-09-25
> **nickrout said:**
> what does the log file say?

Which log file and where?

---

### Post by nickrout on 2010-09-25
/var/log/mythtv/mythfrontend.log

---

