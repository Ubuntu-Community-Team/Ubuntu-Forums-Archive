---
title: "Restore Amarok MySQL backup on a new system?"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by khughitt on 2008-01-24
Heya,

I'm trying to restore an Amarok database backup in Gusty, but am having luck getting the restore to synchronize with my new system: that is, the statistics are all saved in the database backup, but they do not (apparently) point to the same place on my new system.

The *directory structure* is the same (e.g. /media/Music on both the old and new system), however, the overall partition setup for my old system is different than it is now, and I think this may be where the problem lies.

After browsing around the Amarok database schema, I noticed that the device id in the devices table does not match the device id for most of my statistics.

For example, the music folder is listed as id **13**:

```

+----+--------------------+
| id | lastmountpoint     |
+----+--------------------+
|  1 | /media/winXP       | 
|  2 | /                  | 
|  3 | /media/sdb1        | 
|  4 | /media/sdc1        | 
|  5 | /media/LEXAR       | 
|  6 | /media/IPOD        | 
|  7 | /media/disk        | 
|  8 | /media/disk        | 
|  9 | /media/Fedora      | 
| 10 | /media/Debian      | 
| 11 | /                  | 
| 12 | /boot              | 
| 13 | /media/Music       | 
| 14 | /media/Windows     | 
| 15 | /media/EXTERNAL_HD | 
| 16 | /                  | 
| 17 | /boot              | 
+----+--------------------+
17 rows in set (0.00 sec)

```

Whereas in the statistics table, most of the songs are associated with device id 6.

To fix the issue should I simply change the id for /media/Music from 13 to 6?
Anyone have any ideas on how I could go about further diagnosing or fixing the problem?

Any help would be greatly appreciated.

Thanks!

---

