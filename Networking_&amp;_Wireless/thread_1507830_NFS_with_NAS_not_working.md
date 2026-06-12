---
title: "NFS with NAS not working"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by gibbylinks on 2010-06-12
Hi All

I can't get my NAS drive to mount using NFS in etc/fstab

can anyone see anything wrong ?

192.168.1.111:/mnt/IDE1/music    /mnt/musicbox          nfs      intr          0       0

this gives me "[COLOR=Red]mount.nfs: an incorrect mount option was specified[/COLOR]" error message

I can connect at the command prompt, but only if I** don't** use the "-t nfs" option !! this gives me the same error.

I have all the necessary pacakages installed and as I say I can connect at the command pompt using ```
sudo mount -v 192.168.1.111:/mnt/IDE1/music /mnt/musicbox -w
```Thanks

---

### Post by paradoxni on 2010-06-12
try  
```

192.168.1.111:/mnt/IDE1/music /mnt/musicbox  nfs  user,rw,auto
```

---

### Post by gibbylinks on 2010-06-12
same error :confused:

---

