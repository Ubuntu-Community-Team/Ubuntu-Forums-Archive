---
title: "Gutsy drops a hard drive every few weeks"
date: 2008-09-15
forum: Mythbuntu
---

### Post by Maynard on 2008-09-15
I have 2 hard drives, one is 40 GB and the other is a 500 GB (Seagate Barracuda).  I have the OS installed on the 40 GB partition, and the 500 GB is for recordings.  About once a month (or 6 weeks or so), my 500 GB hard drive gets unmounted somehow.  I figure it out because the 40 GB gets filled up with recordings when the 500 GB is dropped.  Then my system crashes, and I have to manually remount the 500 GB hard drive.

I've looked in mythbackend.log and can't see anything that tells me what happened.  Any ideas?

---

### Post by Lester_Burnham on 2008-09-16
I'm curious. Was it formatted XFS?

I had big problems in Hardy with a 500gb Samsung. Ended up using EXT3 in the end.

---

### Post by db260179 on 2008-09-16
Compress some of your log files, /var/log/messages /var/log/syslog
send you /etc/fstab aswell, attach it to this post

Thanks

> **Maynard said:**
> I have 2 hard drives, one is 40 GB and the other is a 500 GB (Seagate Barracuda).  I have the OS installed on the 40 GB partition, and the 500 GB is for recordings.  About once a month (or 6 weeks or so), my 500 GB hard drive gets unmounted somehow.  I figure it out because the 40 GB gets filled up with recordings when the 500 GB is dropped.  Then my system crashes, and I have to manually remount the 500 GB hard drive.

I've looked in mythbackend.log and can't see anything that tells me what happened.  Any ideas?

---

### Post by Maynard on 2008-09-16
I have the 500 GB drive formatted as JFS.

Here are the log files and fstab:

---

### Post by db260179 on 2008-09-17
Thanks!

A few things you can try :-

1. Check the sata lead connection, make sure its not loose, could be disconnecting physically - sata leads are known to fall off!
2. In Your /etc/fstab - you have the drive set with the UUID, in a terminal type, sudo blkid, confirm the UUID is the same as /etc/fstab. If not change the /etc/fstab to match the blkid reading

JFS has no real benefits over EXT3, it's wise to re format the drive to ext3.

> **Maynard said:**
> I have the 500 GB drive formatted as JFS.

Here are the log files and fstab:

---

### Post by insane_alien on 2008-09-17
have you tried upgrading? it is entirely possible that this is a known bug and has already been fixed.

---

### Post by Maynard on 2008-09-17
I've checked the SATA cable and it isn't loose.

I'll try reformatting to ext3 first.  I'm weary of upgrading because of all the manual config I have (wireless card, remote, etc).  But if reformatting to ext3 doesn't work...I'll upgrade.

BTW, once I reformat to ext3, is there any setting I should reconfigure (like selecting the "delete slowly", or whatever, option)?

Thanks for all your help!

---

### Post by db260179 on 2008-09-19
In mythbackend setup, yes select 'delete files slowly' and select 'recurse directorys/sub etc'

> **Maynard said:**
> I've checked the SATA cable and it isn't loose.

I'll try reformatting to ext3 first.  I'm weary of upgrading because of all the manual config I have (wireless card, remote, etc).  But if reformatting to ext3 doesn't work...I'll upgrade.

BTW, once I reformat to ext3, is there any setting I should reconfigure (like selecting the "delete slowly", or whatever, option)?

Thanks for all your help!

---

### Post by DemonBob on 2008-09-19
I had the same issue, turns out the UUID of the disk in fstab was wrong, make sure you double check all the UUID's in the fstab

---

