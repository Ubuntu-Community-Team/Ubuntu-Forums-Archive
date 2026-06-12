---
title: "Can't mount Samba share"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by mwolfgang on 2009-11-15
I added the following line to my /etc/fstab, but the share fails to mount automatically:

```
//ubuntudesktop/media /media/media smbfs username=matt,password=*password* 0   0
```In addition, when I attempt to mount the share manually from the command line, using the following command, it asks for my password, then just hangs and never mounts the share:

```
sudo mount -t  smbfs -o username=matt //ubuntudesktop/media/ /media/media/
```Any ideas?

Thanks,
Matt

---

### Post by Fir3chi3f on 2009-11-15
Does the drive normally mount ok? without the fstab modified and just by clicking the drive in the Places menu?

---

### Post by mwolfgang on 2009-11-15
> **Fir3chi3f said:**
> Does the drive normally mount ok? without the fstab modified and just by clicking the drive in the Places menu?


Yes, I can access it that way, but it doesn't mount as part of the file system, so it's basically inaccessible in a lot of applications.  i.e. it doesn't appear as a sub-direcctory in /media or /mnt.

---

### Post by michaelgilch on 2010-01-20
any luck on this? I am having the same issue.  Thanks

---

### Post by mwolfgang on 2010-01-20
I was able to mount by using the IP address instead of the computer name.  I eventually added entries for the other machines in my house to my /etc/hosts file and that completely resolved the problem.

Matt

---

