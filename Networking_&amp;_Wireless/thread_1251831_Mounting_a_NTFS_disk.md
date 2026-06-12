---
title: "Mounting a NTFS disk"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by asai on 2009-08-28
Hi,
I have mounted a NTFS disk on a dual boot system.
Entered this into /etc/fstab:
```
/dev/sda1 /media/windows ntfs-fuse auto 0 0
```
When I reboot into Windows, the system needs to run chkdsk.
This happens at every reboot.
Any suggestions on why this happens, and is there a workaround for this?

---

### Post by asai on 2009-09-02
Anyone?

---

### Post by asai on 2009-09-02
Solved it!
I changed the entry in /etc/fstab like this:
```
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
```
Works like a charm. :D

---

