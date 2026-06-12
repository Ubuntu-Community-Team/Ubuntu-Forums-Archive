---
title: "Mythtv: Deleted programs not deleting files"
date: 2009-11-09
forum: Multimedia Software
---

### Post by NuttinButNet on 2009-11-09
I have Mythtv .21 and it's been running fine. I'm not sure what I changed, but I thought I'd post here first.

When I delete the recordings in the Mythttv recording screen they delete on the screen but it's not deleting the files and the disk is starting to fill up. I looked in the database and the table "recorded" has a record of every file that has not been deleted but should have and the column of "recgroup" has a "deleted" in it for each of these orphan files. I don't have a "deleted" group in the recording groups on the recording screen.

I must have changed something to stop mythtv from deleting the files when I delete the program. Does anyone know what setting will stop/start mythtv from deleting the files?

I can manually delete all the orphan files, but I'd rather fix the real problem.

Thanks

---

### Post by jtmoney on 2010-01-07
Hey, did you ever figure out what was causing this?  I've been experiencing this, off and on, with 0.22, but never experienced it with 0.21.  /var/log/mythbackend.log provides no clues.

Have you ever run a database-optimizing script for MythTV?

---

### Post by will177 on 2010-04-25
I have this problem now too, on 0.22 on Karmic 64-bit.
Anyone know the solution?
Help!  Disk is almost full.
Thanks in advance.

---

