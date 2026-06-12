---
title: "Which filesystem is best for storing large ISO images on external HDD?"
date: 2008-02-11
forum: Multimedia Production
---

### Post by tr333 on 2008-02-11
Which filesystem is best for storing large DVD ISO images (8GB) on an external HDD?  I would have used FAT32, but that can only handle up to 4GB file size.  Can linux read HFS+ partitions?  I ask that because I might be using this drive with an Apple TV.

---

### Post by logos34 on 2008-02-11
> **tr333 said:**
>  Can linux read HFS+ partitions?.

Yes.  However to write to hfs+ I believe you'll need to disable journaling on it.

NTFS or ext3 will work just fine too.

---

