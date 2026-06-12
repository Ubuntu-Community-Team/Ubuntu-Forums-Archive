---
title: "Logictech Media Server 7.9 unable to see /dev/sda"
date: 2020-07-09
forum: Multimedia Software
---

### Post by zz4z7j on 2020-07-09
I'm a newbie to Linux....

I've been able to install, format, and mount the 2nd and 3rd drives into Ubuntu without any issue. I'm at a lost on why when I attempt to map the 2nd or 3rd drive into Logictech Media Server 7.9. The software is unable to see /dev/sda or /dev/sdb? I've added pictures to show the issue.

Thanks

---

### Post by TheFu on 2020-07-09
Don't confuse the entire drive (sda) with the partition that holds a file system (sda1).
MS-Windows has warped too many people's minds on this topic by using the "drive" term when "partition" is the correct term.

Also, using an HBA as a RAiD controller is further confusing things.  Whenever setting up storage for RAiD, the best practice is to create a partition and use that for any RAiD needs for a multitude of reasons, but mainly so when a disk fails then a replacement disk that isn't exactly the same size can be used. Partitions provide a migration path that using the whole disk does not.

Did you mount the file system(s) to an empty directory (each) under ubuntu?

As for Logitech software - that's something you'll need to take up with the customer support from that company.

---

### Post by Yellow Pasque on 2020-07-10
> **TheFu said:**
> Don't confuse the entire drive (sda) with the partition that holes a file system (sda1)

Just an FYI: You can have a disk with one partition that spans the entire disk, and has no partition table (parted calls this a 'loop' partition table). The partition then will be simply named /dev/sda
Might want to look at fdisk to see exactly what is going on.
```
sudo fdisk -l
```

---

### Post by Yellow Pasque on 2020-07-10
> **zz4z7j said:**
> The software is unable to see /dev/sda or /dev/sdb

You need to point it to where those partitions are mounted. From your pic, it looks like one of them is /media/music/<something>

---

