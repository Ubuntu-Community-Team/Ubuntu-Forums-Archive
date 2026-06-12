---
title: "How to mount samba shares"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by plexi50 on 2006-06-24
I installed smbfs and I need to know how to mount a samba folder  to my desktop. Does not need to mount on boot, I can just  type it in each time, as it will change.

---

### Post by slider on 2006-06-24
Places -> Connect to Server
File -> Connect to Server in Nautilus

---

### Post by puelly on 2006-06-24
[QUOTE=plexi50]I installed smbfs and I need to know how to mount a samba folder  to my desktop. Does not need to mount on boot, I can just  type it in each time, as it will change.[/QUOTE]

Try the information on this site:
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by lapsey on 2006-06-24
i prefer 

```
smbmount //server/share ~/Desktop/share -o username=username,password=password,fmask=755,dmask=755,rw
```

or similar.

---

