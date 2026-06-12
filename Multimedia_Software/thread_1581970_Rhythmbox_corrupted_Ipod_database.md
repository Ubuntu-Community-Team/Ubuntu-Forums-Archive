---
title: "Rhythmbox corrupted Ipod database"
date: 2010-09-25
forum: Multimedia Software
---

### Post by itlarson on 2010-09-25
I was trying to sync my Ipod with Rhythmbox.  After deleting an album, I disconnected the Ipod, and found it was displaying no music.  Evidently this is a matter of the Ipod's internal database being corrupt, since you can still browse it with nautilus, and play the music that way.  But the file name's aren't human readable, and it's impossible to play the music through the Ipod itself.

On the internet I found out the database could be restored with:
gnupod_addsong --restore -m /media/IPOD
But this gives the error:
Could not write to /media/IPOD, iPod mounted read-only? (Read-only file system)

Any Ideas?

---

### Post by lkjoel on 2010-09-25
> **itlarson said:**
> I was trying to sync my Ipod with Rhythmbox.  After deleting an album, I disconnected the Ipod, and found it was displaying no music.  Evidently this is a matter of the Ipod's internal database being corrupt, since you can still browse it with nautilus, and play the music that way.  But the file name's aren't human readable, and it's impossible to play the music through the Ipod itself.

On the internet I found out the database could be restored with:
gnupod_addsong --restore -m /media/IPOD
But this gives the error:
Could not write to /media/IPOD, iPod mounted read-only? (Read-only file system)

Any Ideas?
Is it Jail-Broken?

---

### Post by itlarson on 2010-09-26
I didn't think that was needed for an Ipod classic.  It was syncing in Linux previously.  It's literally never been hooked up to Itunes.

---

### Post by itlarson on 2010-09-26
I can't do any file operations on the Ipod except reading it.  I would like to reformat it with gparted, but it doesn't show up.  The folowing seems to imply the device should be readable:

$ mount -l
/dev/sdd1 on /media/IPOD type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1002,gid=1002,shortname=mixed,dmask=0077,utf8=1,flush) [IPOD]

---

### Post by PabloTempe on 2010-09-26
I would try synching it with another Linux machine. This way you can isolate that it isn't your computer causing the problem.

---

### Post by primaerfunktion on 2010-10-13
ive exactly the same problem with my shuffle 3rd gen since ive updated to 10.10. on 10.04 everything worked perfect. i also tried banshee and gtkpod and they destroyed the firmware too. so i had to reset it with itunes on a windows machine... for me it seems like it is much more some kind of ubuntu related promblem. i cant imagine why this happens all the time... i hope some of you guys can.

---

