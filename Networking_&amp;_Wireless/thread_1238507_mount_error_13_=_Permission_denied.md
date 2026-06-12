---
title: "mount error 13 = Permission denied"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by malarie on 2009-08-12
Good day,

I cant mount a Windows share in my fstab when the share is on Vista SP1.

Example in my fstab:
#Windows 2003 Server WORKS
//nilgiri/transfer /mnt/windows/Nilgiri/transfer cifs exec,credentials=/etc/cifspw 0 0

#My laptop Running on Vista SP1 Does NOT works.
//penang/transfer /mnt/windows/Penang/transfer  cifs exec,credentials=/etc/cifspw3 0 0

Another Windows XP Machine that WORKS.
//192.168.XXX.XXX/BackupTest  /mnt/windows/BackupTest/backups cifs exec,credentials=/etc/cifspw2 0 0

My Firewall on Vista is disabled. I know DNS is not an issue here.

When i go #mount -a, i have this: 
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

TFM does not say shiz about error 13.
Thanks.

PS: I use the local admin credentials to log on.

---

### Post by malarie on 2009-08-12
Hey noob, why dont you try the domain admin credentials?

---

### Post by malarie on 2009-08-12
Wow!! malarie, you're genius! You  must have a super hot GF!!!

---

### Post by malarie on 2009-08-12
Indeed!

---

