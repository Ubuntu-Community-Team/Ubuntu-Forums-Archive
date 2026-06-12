---
title: "MythTV - recording to multiple partitions?"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by gurgle on 2007-01-04
I would like MythTV to be able to use 2 of my hard drives. Is it possible to set multiple folders/partitions/network shares to record to?

---

### Post by majoridiot on 2007-01-04
mythtv provides for only one record/livetv directory.  off the top of my head, i would say this
*might* be possible if you swapped the record partition in and out yourself, whilst mythtv
*might* be unaware of it and happily record to/play from whatever happened to be mounted.
the only thing is that they would have to be partitions and not directories.

try, e.g...

create a mount point of /mnt/recswap, owned by mythtv
set the recording directory in mythbackend to /mnt/recswap

at that point, you could mount whatever content-holding partition you want @  /mnt/recswap
(assuming mythbackend isn't using it for transcoding, livetv, etc.) and record/play from it.

this will possibly cause problems with livetv expires if the program to be expired is not on
the partition that is currently mounted @ /mnt/recswap.  the program info may or may not
be deleted from the database and the stored recording would likely need to be deleted
manually when you mount that partition again.

it's unknown how the media library would function... i don't know how or when it builds the 
library, so it might delete the info on recordings stored on an unmounted partition.  if it
checks the list against the actual files and rebuilds the library each time you look, then
everything could be cool.

if this works, you could attach scripts to different remote keys to mount/unmount different
partitions.

certainly worth playing with... but backup your mythconverg database first!  there are way
too many unknowns with this.

```
$ mysqldump -u mythtv -your.myth.mysql.password mythconverg -c > mythcvgbak.sql
```

if you need to restore:

```
$ mysql -u root (add -p if you have a root password set for mysql)
mysql>create database mythconverg; 
mysql>exit
$ mysql -u mythtv -your.myth.mysql.password mythconverg < mythcvgbak.sql 

```

please keep us all updated if you dig into this! :D

---

### Post by superm1 on 2007-01-05
> **gurgle said:**
> I would like MythTV to be able to use 2 of my hard drives. Is it possible to set multiple folders/partitions/network shares to record to?
Yes this can be achieved for multiple partitions/drives on one machine. 
What you are looking to setup is LVM.  You mark the partitions as type LVM (0x8e in fdisk), and then you create a logical volume that spans across all the drives/partitions you want.  You add the drives you want to the logical volume group.  Once you have all the space you want, you create a virtual partition on this.  You format this partition with a normal file system, xfs, reiserfs, jfs, etx3 etc.  For myth usage, go xfs.  

Spanning across network shares isn't going to work from a single backend.  If you have several backends however, you can have them recording to different areas.  Say you have one backend with a 500 gig drive, you can use all that space on that backend.  Another backend with two 80 gigs, and a 300 can set up a LVM and span the space across all those drives on its own machine.

Do you follow?

---

### Post by majoridiot on 2007-01-05
i totally overlooked LVM for this...  what mario describes should work. :D

---

### Post by gurgle on 2007-01-05
that sounds pretty involved - thanks for the info tho fellas. Considering I am a MythTV newb, I just want to get it all up and running before I really delve into it. Thanks again.

---

### Post by superm1 on 2007-01-05
> **gurgle said:**
> that sounds pretty involved - thanks for the info tho fellas. Considering I am a MythTV newb, I just want to get it all up and running before I really delve into it. Thanks again.
There is a pretty good description in the general howto on mythtv.org explaining exactly how to set up LVM.  I've used that as a reference in the past, and it does make for an easy expansion to more drives and such.  A slight grain of salt to take with this: if you setup LVM and a drive goes bad, there goes all the data on all the drives.  It doesn't mount the logical volume without all the drives from the group.

---

