---
title: "nfs mount problem on boot"
date: 2008-01-07
forum: Mythbuntu
---

### Post by jpdrawneek on 2008-01-07
k - trying to get my client box to mount files of my nas box.

on boot it does not work
i try to remount it and it tells me thats its busy
> mount.nfs: /var/lib/mythtv/videos is already mounted or busy
So i have to umount, mount to get it to mount the file system

fstab
> 
home:/pool/mythtv/videos        /var/lib/mythtv/videos  nfs     defaults       0    0


that look right?  I mainly use SuSE and that has yast for this.

Only box thats having a problem.

Any ideas

---

### Post by barney_1 on 2008-01-12
Hmm... two ideas here.

First, have you tried using your ip address instead of "home:"?

Second, I have had some problems with mounting NFS if the internet connection for my box containing the files drops momentarily.  With Feisty Fawn that box wouldn't reconnect with the router unless I manually used ifdown/ifup.  Could it be that your NFS daemon needs to start after your box acquires it's ip address?

---

