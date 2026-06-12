---
title: "Can I tansfer the MySQL recording rules from a .21 box to a seperate .22 box?"
date: 2009-12-05
forum: Mythbuntu
---

### Post by epi 1:10,000 on 2009-12-05
Has any one ever done this?  can I back up the DB to CD and transfer it?

---

### Post by t3chn0b0y on 2009-12-06
> **epi 1:10,000 said:**
> Has any one ever done this?  can I back up the DB to CD and transfer it?

I wouldn't suggest copying your .21 db over to .22
the database has changed quit a bit, and it will mess up your
.22 ..

---

### Post by matt06 on 2009-12-06
Why not backup your entire 0.21 system to another drive and then use the backup drive to try the upgrade?  That's what I did.  Just make sure you can boot to both the old 0.21 and the backup copy.  Once you can boot to both, you can safely try the upgrade to 0.22 on one of the drives.

Either way, [backup your database first]("http://www.mythtv.org/wiki/Database_Backup_and_Restore").

---

