---
title: "Recording mount in root/var/lib = oops"
date: 2009-01-27
forum: Mythbuntu
---

### Post by rodercot on 2009-01-27
Hey All,

 I setup my machine a couple days ago with 8.10. I figured I would do something dumb. 

 Anyhow my drive is like so. 

 / = 20Gb ext3 sda1 primary
swap = 2gb sda5 logical
/var/lib = 280Gb xfs sda6 logical

 I setup myth to use /var/lib/mythtv/recrodings as default selected but it is using my os root /var/lib directory and is filling up the root partiton quickly. 

 /dev/sda6 is mounted as /var/lib in /etc/fstab by the looks of it. 

 I would assume by looking at df -h that nothing has been put on the actual dev/sda6 as it saying only 1% is used and it is still reporting the full size as partitioned in the setup. 
 
 What are the steps to fix my screw up here please. 

 Can I just boot gparted live and change the swap and xfs partitions to primary from logical or is there another route to follow I have been searching most of the day with no luck yet. 
 
 There's all that dos fdisk use coming back to a haunt me.

 Thanks,
 
 Dave

---

### Post by rodercot on 2009-01-28
I tried a couple things and no luck so I just reinstalled myth and xbmc. Set the partitions the same as before but as primary and now all is fine. 

 Dave

---

