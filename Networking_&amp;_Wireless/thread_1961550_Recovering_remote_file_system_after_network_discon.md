---
title: "Recovering remote file system after network disconnect"
date: 2012-04-19
forum: Networking &amp; Wireless
---

### Post by Only1KW on 2012-04-19
Does anyone know of any way with any remote file system protocol to recover after the network connection between a laptop running Ubuntu and the remote server is dropped?  

So far, I've tried AFS, NFS, and SSHFS with no luck.  With all of them, after the network connection is lost with active files opened, all applications using those remote files lock up to the point that kill -9 has no effect on them.  I've tried unmounting and remounting the mount point after network connectivity is restored and, during the times the unmount doesn't hang, the application state doesn't change at all.  My only options are to either reboot or ignore the zombie processes/windows and never attempt to sleep or hibernate the computer again.  Anyone have any other recommendations?

---

### Post by Only1KW on 2012-04-21
Seriously?  There is no way to configure any Linux client for any remote file system to get it to work well with laptops?

---

