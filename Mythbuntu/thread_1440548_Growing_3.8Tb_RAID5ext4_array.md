---
title: "Growing 3.8Tb RAID5/ext4 array"
date: 2010-03-27
forum: Mythbuntu
---

### Post by ian dobson on 2010-03-27
Hi,

Maybe someone can answer a "simple" question that I have.

I have a 3.8Tb RAID5 array (3 2Tb drives) formatted as ext4, I've just picked up several new 2Tb drives and would like to grow the file system to use 4 2Tb drives. I've added a drive to my array and mdadm is currently reshaping the array to use all 4 drives (It'll take about 30hours to complete). My question is, is it safe to grow the filesystem using e2resize? 

I have a good backup of all the data so if things do go wrong it'll only take a day or so to restore everything. So does e2resize in ubuntu 9.10 support growing arrays to larger than 4Tb?

Regards
Ian Dobson

---

### Post by ian dobson on 2010-03-28
Hi,

Anyone?

The array is still reshaping (It's been running for 14Hours and still has about 12hours to go) so I still have time to go before I need to e2resize.

Regards
Ian Dobson

---

### Post by nickrout on 2010-03-28
I assume because you posted here you are using this for myth. Mightn't it be safer to set up a new partition and add it to your storage group?

---

### Post by ian dobson on 2010-03-28
> **nickrout said:**
> I assume because you posted here you are using this for myth. Mightn't it be safer to set up a new partition and add it to your storage group?

Just adding a new storage group/partition isn't really a solution, part of the large array is for mythtv, but not all. I need a redundant storage systm (RAID) so I can only add a drive to my current array or create a new array with several disks which I can't afford at the moment.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-03-28
Hi,

OK the reshape is finished:-

```

Mar 28 18:28:36 alpha2 kernel: [104357.343421] md: md1: reshape done.
Mar 28 18:28:36 alpha2 kernel: [104357.525114] RAID5 conf printout:
Mar 28 18:28:36 alpha2 kernel: [104357.525119]  --- rd:4 wd:4
Mar 28 18:28:36 alpha2 kernel: [104357.525122]  disk 0, o:1, dev:sda2
Mar 28 18:28:36 alpha2 kernel: [104357.525124]  disk 1, o:1, dev:sdb2
Mar 28 18:28:36 alpha2 kernel: [104357.525125]  disk 2, o:1, dev:sdc2
Mar 28 18:28:36 alpha2 kernel: [104357.525127]  disk 3, o:1, dev:sdd2
Mar 28 18:28:36 alpha2 kernel: [104357.525134] md1: detected capacity change from 3960767250432 to 5941150875648
Mar 28 18:28:37 alpha2 kernel: [104358.479632] VFS: busy inodes on changed media or resized disk md1
Mar 28 18:28:37 alpha2 mdadm[1452]: RebuildFinished event detected on md device /dev/md1

```

Maybe I can shutdown the box tomorrow (I have a simulation running at the moment (The main use of the drive space)) and try a fs resize.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-03-30
Hi,

OK,I've posted the same question on in the server forum, maybe I'll get an answer there.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-04-01
Hi,

OK, rebooted the box into single user mode. Did a fsck (that took almost 1 hour), then started a resize2fs -p /dev/md1. 

After several minutes it displayed a message along the lines of "expanding inodes pass 1 (of maximum 1475)" which started to get me abit worried, but about 15 minutes later it finished pass 1 and ended without an error.

I mounted the device and all my files are there :)

Rebooted the box and it started as if nothing had happened (apart from a 6Tb data mount point :D:D:D).

Linux has come along way, since my first tests with an 486 and a sound blaster with CD drive attached.

Regards
Ian Dobson

---

