---
title: "What's Wrong With This?  fstab question."
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by umechanism on 2009-03-15
I have an HPmediaVault which is a NAS.  I have setup folders on this NAS which I want to mount in ubuntu.  I can not make this mount.  Is there anything wrong with my syntax?

```
hpmediavault:/shares/Volume1/FileShare /mnt/hpmediavault/Volume1/FileShare nfs
```

I can ping the NAS by typing "ping hpmediavault".  That works just fine.  I can also mount the folders manually but I can't do it from the fstab file.

Any help would be appreciated.

tks

---

### Post by warchief_ryan on 2009-03-16
Is there no access controls on the NAS? such as username or password, those might have to be added.

have you tried using its IP instead of the hostname? If you don't have a dns server or added the NAS hostname to the hosts file then I wouldn't think that would work.

---

### Post by umechanism on 2009-03-16
Not for folder access.  I can set a username and password for each folder but, at the present time, none of my folders are password restricted.

---

### Post by umechanism on 2009-03-17
I finally got it to work.  See below:
```
//192.168.2.102/FileShare /mnt/hpmediavault/Volume1/FileShare cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0
```
Everything works perfectly now.

M

---

### Post by stanz on 2009-03-17
> **umechanism said:**
> I finally got it to work.  See below:
```
//192.168.2.102/FileShare /mnt/hpmediavault/Volume1/FileShare cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0
```Everything works perfectly now.
M
...

---

