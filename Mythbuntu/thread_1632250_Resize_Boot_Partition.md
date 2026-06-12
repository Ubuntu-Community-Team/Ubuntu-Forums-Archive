---
title: "Resize Boot Partition"
date: 2010-11-27
forum: Mythbuntu
---

### Post by Senkoboy on 2010-11-27
I am running Mythbuntu Lucid, I had a 40 gig hard drive with the Mythbuntu and have a 1 TB drive for recordings.   My primary drive was pretty full, only 8 gib left.  I cloned my 40 gig to a 80 gig drive for more space.  Now my 80 gig boots and works fine, it just has unallocated space of 37 gig.  I want to resize my Sda1 partition to fill the extra space.
With a G-Parted live CD, 7.0, it shows, Left to Right:  Sda1,ext4, Boot, 35.7 Gig; Sda2 extended 1.57 Gig; Sda5 swap 1.57 Gig. 

How do I resize my Sda1 partition to fill up the unallocated space?  G-Parted won't let me increase the partition.  I know you have to be careful with the boot partition.  Do I also need to increase the size of my swap partition? 

Thanks,

---

### Post by wilee-nilee on 2010-11-27
How about a actual picture of this on gparted an screen shot.

---

### Post by Senkoboy on 2010-11-28
Attached is a screenshot, I hope.

---

### Post by ian dobson on 2010-11-28
Hi,

YOu can't grow sda1 as your swap partition is right behind it. Remove the swap partition expand sda1 and add your swap to the end of the drive.

Regards
Ian Dobson

---

### Post by oldfred on 2010-11-28
ian dobson's suggestion is the quickest way, but creating a new swap will have a new UUID and you will have to edit fstab with the new UUID.

The only other alternative takes many steps with gparted and it may still change the UUID, (it should not, but...). You expand extended partition all the way to the end of the drive. You then move the swap to the end of the extended. The you can move the left end of the extended to the right. Then expand the root partition.

A third alternative is just to expand the extended partition and create a new partition. You could move /home into it or create it as a data partition.

Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by David Grigor on 2010-11-30
I recommend the third option oldfred mentions. 

It is nice to have home on a seperate partition so when time to upgrade you don't have to worry about personal files getting over written.

---

### Post by Senkoboy on 2010-11-30
I think I will go with option #3.  Just need the time to do it.

Thanks everyone..:D

---

