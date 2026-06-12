---
title: "[SOLVED] Need advice moving from KnoppMyth to Mythbuntu"
date: 2007-11-28
forum: Mythbuntu
---

### Post by ahood on 2007-11-28
Hi All,

I am planning on moving from KnoppMyth to Mythbuntu. I have setup two drivers with LVM and I am concerned about how to restore the LVM so that Mythbuntu can see it.

Below are commands I think I need to run in order to restore the LVM partition (called vg). 

It would be much appreciated if someone confirmed that the commands below are correct or if they need revising?

All commands below will be done as root.

First is to confirm volume groups and backup fstab
> 
vgscan

pvdisplay

mv /etc/fstab /etc/fstab.orig

nano /etc/fstab


Add the following lines to fstab
> 
File System
/myth auto defaults.auto 0 2

Processes
/dev/vg/myth /myth auto defaults.auto 0 2



Lastly, mount the LVM partition
> 
mount /dev/vg/myth /myth

update-rc.d lvm start 26 S . stop 82 1



When do I execute the above commands?

Is there anything else I should know before doing this?

If successful, I would then restore the mysql table of programming data by executing the following command.

> 
mysql -u mythtv -p mythconverg < recorded.sql


Again, any help would be greatly appreciated.

Al

---

### Post by ubnewbie2 on 2007-11-28
I just migrated from Knoppmyth to mythbuntu.  I must say, I think it is a big step forward.  

Firstly, did you notice the sticky at the top of this forum on lv's.

I took a different approach. I too had and lvm setup under knoppmyth, so I purchased another hard disk, the same size as the lv (hard disks just keep getting cheaper :-) and copied the files across that I wanted to keep.

Now I have twice the storage, which I could lvm together, but I think I'll reuse the older drives for the video, photo and music storage, keeping the new drive for recordings.  Then, when the new version of mythtv comes out, with storages groups, I will add all the drives into the storage group - and so not need an lv at all.

---

### Post by ahood on 2007-11-28
Thanks so much!!!

I like your approach. I will do something similar.

Al

---

