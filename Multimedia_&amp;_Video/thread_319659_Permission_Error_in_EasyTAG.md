---
title: "Permission Error in EasyTAG"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by Forge42 on 2006-12-16
Hello all.  

I'm trying to use easytag to move a bunch of mp3 files into subdirectories based on their tags.  Basic \artist\album\title.mp3 type thing.  Whenever Easytag asks if I want to rename the file, I get a permission error.  I know I have write permissions for where I'm trying to save them.  I even manually duplicated what (I think) I'm asking easy tag to do.  No problems.  Anyone have an idea what might be going on?

FWIW, I'm writing to an NTFS partition on a large slave drive on my primary IDE channel.

---

### Post by jpkotta on 2006-12-16
Are you sure you can write to NTFS partitions?  Say your NTFS partition is mounted at /ntfs.  What happens when you do ```
touch /ntfs/foo ; ls -l /ntfs
```
I'm not sure about edgy, but dapper will not write to NTFS without a patch.

---

### Post by Forge42 on 2006-12-16
Yes.  I'm positive I can write to the location I'm trying to copy to.  Like I said, I manually did what I was asking easyTAG to do.  I know that edgy won't write to NTFS by default, but I applied that hack that allows NTFS write support.

---

### Post by Forge42 on 2006-12-16
bump

---

