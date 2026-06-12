---
title: "mounting a raid-0 stripe"
date: 2012-09-23
forum: Mythbuntu
---

### Post by cjohnson19791979 on 2012-09-23
i've googled myself silly and i can't really find an answer that fits my situation. i've got four disks (2x 2tb and 2x 1tb) that previously showed as a single 6tb volume in windows 7. this drive previously (and hopefully still does) held all my recordings from sagetv. i'd like to use this array for myth the same way. they are all showing as GPT.

---

### Post by nickrout on 2012-09-23
> **cjohnson19791979 said:**
> i've googled myself silly and i can't really find an answer that fits my situation. i've got four disks (2x 2tb and 2x 1tb) that previously showed as a single 6tb volume in windows 7. this drive previously (and hopefully still does) held all my recordings from sagetv. i'd like to use this array for myth the same way. they are all showing as GPT.

Does this cover it?

[http://ubuntuforums.org/showthread.php?t=833653](http://ubuntuforums.org/showthread.php?t=833653)

(Frankly I would be s*** scared of wrecking the raid array and would go for the "safe" way of buying two fresh 3TB drives, copying the data from windows to a linux machine over a (fast) network and then start playing with the raid array in linux.)

---

### Post by cjohnson19791979 on 2012-09-24
> 
Does this cover it?


almost.

i've read some things about there needing to be a kernel option enabled for this to work. maybe that might be correct maybe not. either way, that link you sent me to isn't really specific enough to my setup. i can't be sure if i'm doing something wrong or if i'm missing another piece to this puzzle.

here's the drive layout...

> 
$ sudo parted -l
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  99.6MB  98.6MB  fat32                 boot
 2      99.6MB  492GB   492GB   ext4
 3      492GB   500GB   8281MB  linux-swap(v1)


Model: ATA WDC WD1002FBYS-0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  1066kB  1049kB               LDM metadata partition
 2      1066kB  134MB   133MB                Microsoft reserved partition  msftres
 3      134MB   1000GB  1000GB               LDM data partition


Model: ATA WDC WD1002FBYS-0 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  1066kB  1049kB               LDM metadata partition
 2      1066kB  134MB   133MB                Microsoft reserved partition  msftres
 3      134MB   1000GB  1000GB               LDM data partition


Model: ATA WDC WD20EARS-00S (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  1066kB  1049kB               LDM metadata partition
 2      1066kB  134MB   133MB                Microsoft reserved partition  msftres
 3      134MB   2000GB  2000GB               LDM data partition


Model: ATA WDC WD20EARS-00S (scsi)
Disk /dev/sde: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  1066kB  1049kB               LDM metadata partition
 2      1066kB  134MB   133MB                Microsoft reserved partition  msftres
 3      134MB   2000GB  2000GB               LDM data partition




the thing is that i'm not sure which partition to point the mdadm --build line to. my guess would be #3 but i dunno for certain.

---

### Post by nickrout on 2012-09-24
I don't know for sure but the other article seemed to be saying that if you point mdadm to the wrong partition it will give an error, but won't destroy anything. So trial and error may be needed.

PS not sure why you want raid0 in this circumstance. A drive containing media does not have to be particularly fast.

---

### Post by cjohnson19791979 on 2012-09-24
> not sure why you want raid0 in this circumstance.it might need to be linear for all i know? that's what i mean about not being sure if what i'm doing is correct or not as it pertains to my setup. windows actually calls it a spanned dynamic volume, so it may very well not be raid-0.

---

