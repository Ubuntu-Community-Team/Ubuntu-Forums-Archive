---
title: "Moving files around storage groups"
date: 2010-05-16
forum: Mythbuntu
---

### Post by dualboot on 2010-05-16
Hi All,
I am looking at backing up my 9.10 system before clicking on the 'upgrade' button in update manager.  I have a second 1TB disk, and have added /mnt/sdb1/recordings into the default storage group.  I still have /var/lib/mythtv/recordings in there, and that has about 60GB of media files.

If I could move these files to the second disk my clonezilla backup would be only a few gigs.

Is it just a simple as using mv ?  Will mythtv look in both places, or do I have to tell it about the moves somehow ?

---

### Post by ian dobson on 2010-05-16
Hi,

Move the recordings over to the second drive making sure that they land in a directory pointed to my a storage group. Then edit the programs table for the filesyou moved, changing the storage group field.

Regards
Ian Dobson

---

### Post by dualboot on 2010-05-22
Thanks Ian.

Do I need to use phpmyadmin ?  I did use it years ago, but can't remember how to get access to it.  Is there a good howto anyone can point me to ?

---

### Post by ian dobson on 2010-05-23
Hi,

Google is your friend :- [https://help.ubuntu.com/10.04/serverguide/C/phpmyadmin.html](https://help.ubuntu.com/10.04/serverguide/C/phpmyadmin.html)

Regards
Ian Dobson

---

