---
title: "Mythbuntu Mount Fails Regularly"
date: 2009-01-31
forum: Mythbuntu
---

### Post by paulin on 2009-01-31
I've been using Mythbuntu for a couple of months now.  I have a problem where the mounts I have setup, are lost regularly (at least once in a 24 hour period).  I have to reboot to fix it.  

Anybody know why and/or how to fix it.

Any help would be appreciated.

Thanks
steve

---

### Post by ian dobson on 2009-02-01
Hi,

Can you give abit more information:

What mounts have you setup (Local drive,CIFS/NFS share). How are they started (fstab, rc.local script).

Regards
Ian Dobson

---

### Post by paulin on 2009-02-01
The mounts are NFS using the FS Tab

Here is one of them.
xxx.xxx.xxx.xxx:/general  /mnt/general nfs      intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,tcp     0       0


Currently I have to mounts setup
General
Media

The log shows the following when they are no longer working.
[   51.312030] eth0: no IPv6 routers present
[29633.132044] nfs: server xxx.xxx.xxx.xxx not responding, still trying

Any time I do anything near the mount (ls or cd into /mnt/general)  the terminal window (remote or local) locks up.  Can't ctrl+c or anything to get out of it...

Here is the uname info too:

Linux ZombiesMyth 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

Hope that's enough information

Steve

PS I have another ubuntu (desktop addition) that doesn't have this problem.  The mount is to a ReadyNas duo from netgear.

---

