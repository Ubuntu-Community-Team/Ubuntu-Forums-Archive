---
title: "NFS strange behaviour in Ubuntu 8.10"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by ClementMenier on 2009-07-07
Dear All,

   We are having issue with our NFS installation since we moved to ubuntu 8.10.

   We have one master serving home files for 8 other PCs. NFS is mounted correctly no problem. After a while some clients seems to lose the connection with the master. For example if we try to ssh them, it cannot read the .ssh directory and therefore cannot find the authorized_keys file.
   This problem is rather haphazard. Sometimes we have once every hour, sometimes we have it ten times in 5 minutes.
   To get back the file system, we just have to connect to the master and
do "ls". This seems to refresh the memory of all nfs clients connected to the master.

Options on the server are (rw,no_root_squash,no_subtree_check).
Options on the client are defaults.
(nfs version = 1.1.2-4ubuntu1.1)

Has anyone any idea what can be the issue and how we can fix this?

Thank you very much,
Clement.

---

### Post by sedawk on 2009-07-07
If this "ls" trick works try to run it once per minute by adding
a cronjob on the master. This will not impact the general performance
of your master. 

This is a wild guess, but is it possible the disk spins down
and NFS traffic fails to wake it up again ...
The solution would then be to not let it spin down.

Because "ls" might read from cached pages, "ls" might
not be enough.
You can try some dummy write operations on the master with cron.
E.g. write some dummy files (touch them or write the date
into the files) and then flush the write buffer cache with "sync".

(if this solves the problem have a detailed look at the power
 management of your disk(s) (hdparm) or your acpi configuration).

---

