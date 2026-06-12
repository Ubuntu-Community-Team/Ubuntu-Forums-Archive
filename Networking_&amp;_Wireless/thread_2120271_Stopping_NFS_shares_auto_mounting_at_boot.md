---
title: "Stopping NFS shares auto mounting at boot"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by DBRD on 2013-02-26
I have moved a server from network A to network B, when I try to boot the server it stalls partway through booting whilst it tries to mount nfs shares that were available on network A.  These shares are no longer available and the server just sits on a console screen saying it is waiting for the shares to become available.  

I have gone into single user mode and edited the fstab file to remove the mounts yet the server is still trying to mount the shares on boot.  I have disabled the programs that were using the shares from auto starting also but again the server will not boot.

Any ideas what I have missed?

---

### Post by schragge on 2013-02-26
/etc/auto.master? Are you using autofs?

---

### Post by DBRD on 2013-02-26
Hi,
No, the server is not running autofs.

---

### Post by prodigy_ on 2013-02-26
If there's nothing in the system log, just **grep -r** through **/etc** to find out where else the shares are mentioned. And if this yields nothing, repeat for **/**.

---

### Post by Armann on 2013-02-26
Check /etc/rc.local maybe something is there.

---

