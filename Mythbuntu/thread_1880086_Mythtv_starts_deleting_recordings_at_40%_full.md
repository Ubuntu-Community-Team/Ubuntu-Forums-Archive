---
title: "Mythtv starts deleting recordings at 40% full"
date: 2011-11-12
forum: Mythbuntu
---

### Post by mathog on 2011-11-12
The problem is this, whenever storage exceeds 40%, or about 400GB on disk, it starts deleting recordings.

WHY?????

Details:

0.21 mythbuntu
Two disks: sdb at 160GB and sda at 1TB.  
Two storage directories:

/dev/sdb7  143486704 121715036  21771668  85% /home/mythdbstorage
/dev/sda7  935020576 288072392 646948184  31% /home/mythdbstorage2

Yet whenever storage exceeds 40%, or about 400GB on disk, MythTV starts deleting recordings (oldest first).

Why?????

"extra disk space" is set at 1 GB.  Both of these storage areas have been added to both of the Default and LiveTV storage groups.  For some reason Mythtv seems to think that the total storage area is 400GB, when it is actually over 1 TB.  There are not 400GB partitions, nor have there ever been.  For the life of me I can't figure out where it is getting the 400GB limit from.

Tried running  

  mysql_tables.sh --repair

but it made no difference.

Any suggestions?

Thank you.

---

### Post by nickrout on 2011-11-13
Dunno, but 0.21 is very old, try using a supported version :)

---

### Post by mathog on 2011-11-13
> **nickrout said:**
> Dunno, but 0.21 is very old, try using a supported version :)

Ideally, sure.  However, given the relatively high chance of that upgrade not going smoothly, and the several days it might easily take to get back to a working system, and the better half's constant use of the DVR, it would be best for now to just fix this one problem.

---

### Post by nickrout on 2011-11-14
Well you are likely on your own, 0.21 is not supported.

---

### Post by mathog on 2011-12-21
I figured out what is happening here.  It is normal, but annoying.  The situation is this:

1.  small 160 GB original disk, used until mostly full
2.  added a larger disk.
3.  list both disks as storage areas.

The default storage algorithm splits IO when it can.  So whenever both tuners are running it writes one file to the first disk, and the other file to the second disk.  This happens a lot.  The situation is that the first disk is nearly full, while the second one has gobs of space.  This is where it gets interesting.  When the system sees there isn't enough room on the smaller disk for the next recording it deletes the oldest recording **on that disk**, even though there are gobs of unused memory on the other disk.  This old version apparently lacks the capability of rebalancing the storage.

The workaround was to copy from the command line all of the recordings from the smaller disk to the larger disk.  Now neither disk is anywhere close to filling up so no old recordings are deleted even though we are well past 42% now.  Somewhere near another 300 GB of accumulated recordings the small disk will fill up again, and at that point the symptom will recur - unless I manually move files around before then.

---

