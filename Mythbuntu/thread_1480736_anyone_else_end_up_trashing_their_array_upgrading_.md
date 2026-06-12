---
title: "anyone else end up trashing their array upgrading to 10.4?"
date: 2010-05-11
forum: Mythbuntu
---

### Post by jimp180 on 2010-05-11
I don't for the life of me understand why the upgrade would even look at md0 but it did and trashed it also so now that I have tried to fix it to no avail I guess I start all over from square 1.

---

### Post by byStanderone on 2010-05-11
...for one, will not advise an upgrade to lucid without the necessary prerequisites and that is hard to find i guess...most of the upgrades i've heard did not work. just my opinion, though.

---

### Post by jimp180 on 2010-05-11
well I finally fixed it. I had to select s to skip trying to mount the array on boot up, then I was able to delete the /etc/mdadm/mdadm.conf file. once I did that I was able to reboot and then re assembly the array

---

### Post by ian dobson on 2010-05-12
Hi,

I had no problems with mdadm upgrading to 10.04. My backend boots from a 20Gb mirrored partition and data lands on a 6Tb RAID5 array.

The first boot after the upgrade took alot longer than normal (3-4minutes) but now it's back to the normal 30-45seconds.

Regards
Ian Dobson

---

### Post by dibuntux on 2010-05-12
Hello Ian, 
I did not yet upgraded to 10.04 (even if I'm impatient to do so to see if some of my tuning problems on DVB-T disappear), and one of the reason is mdadm.
In fact, even if my Myth Box is on just one disk (ext4 for boot - very fast - and xfs for media on Storage Groups), my main PC has a RAID 1 with mdadm, and everytime I upgrade to a new version of Ubuntu is risky business. Once I had the unpleasent surprise of finding myself in a busybox at the next boot because of a mdadm bug in Ubuntu 8.10...
Also, if I just upgrade my Myth box, I won't be able to connect to it from the main PC fore the versions are different (.23 &.22).

So my questions:
1) Did you do an Upgrade with Upgrade manager dist upgrade and all went well? Any reccomandations for the upgrade?
2) Did you leave Grub 1.5 or changed to Grub 2?
3) What kind of filesystem you use on RAID1 & RAID5?
4) How many disk you have and how are they splitted on the two RAID system?

Thank in advance Ian,
Dave

---

### Post by ian dobson on 2010-05-12
> **dibuntux said:**
> Hello Ian, 

So my questions:
1) Did you do an Upgrade with Upgrade manager dist upgrade and all went well? Any reccomandations for the upgrade?
2) Did you leave Grub 1.5 or changed to Grub 2?
3) What kind of filesystem you use on RAID1 & RAID5?
4) How many disk you have and how are they splitted on the two RAID system?

Thank in advance Ian,
Dave

1) I upgraded using do-release-upgrade from a terminal prompt over a ssh connction from my portable.
2) I'm staying with grub1 (version 0.97)
3) Root is ext3,data is ext4 (ext3 converted to ext4), backup is ext4 formatted from day 1.
4) OK I have 6 2TB wd sata drives. On four of the drives I have 2 partitions, the first is about 20Gb in size and the second is the rest. The first partition on each drive is in a RAID1 array and used for root. The second partition is in a RAID5 array nd mounts as /data where I have all user data (mythtv,mysql,apache).

The remaing 2 drives are 4Kb 2Tb wd drives. I've partitioned them starting at sector 64, then created a RAID0 device over both of them, this is used as backup and only mounted when required.

All drives are mounted in a hot swap cases.

so:-

/       RAID1 20Gb (sda1,sdb1,sdc1,sdd1)
/data   RAID5 6Tb  (sda2,sdb2,sdc2,sdd2)
/backup RAID0 4Tb  (sde1,sdf1)

Hope this helps
Regards
Ian Dobson

---

### Post by dibuntux on 2010-05-12
Mmmmh, sound like a helluva system! Great job, Ian.

1) I will wait until I get another 1.5 TB WD sata drive: I like the Caviar Green ones, a 500MB equip the Myth box and 2 400 MB the RAID1 of my PC. I intend to copy the partions on the new drive first, then upgrade from there. If everything is fine, I will use it as the main drive for Myth, and the 500MB will become the second, all recordings on Storage Group, so it will do load balancing. Eventually I will get a bigger drive and keep the 500MB as a spare for the RAID1 on the PC.
2) I guess so - I will keep Grub 1 myself.
3) Guess I will keep the filesystem as they are; I'm afraid of converting ext3 to ext4 on RAID1 - for myth data I prefer xfs.
4) "/ RAID1 20Gb (sda1,sdb1,sdc1,sdd1)" you are only using 2 of the mentioned partitions, right?

Thanks for the story! Have a nice MythTV watching my friend!

---

