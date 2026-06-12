---
title: "Exporting CIFS share as NFS"
date: 2012-08-28
forum: Networking &amp; Wireless
---

### Post by medacomix15 on 2012-08-28
I have a NTFS NAS mounted on my Ubuntu PC (11.10) to /mnt/nas2/

I wish to set this up as an network drive so my Windows PC can access it. I've tried directly mounting the NTFS NAS to my windows PC, and I can access the files, but my streaming server software does not work with it.

my **/etc/exports** looks like this:

```
/mnt/nas2/ 10.x.x.x(rw,all_squash,async,insecure_locks,no_acl,no_subtree_check,nohide,insecure)
```

my **/etc/fstab** looks like this:

```
//10.x.x.y/GoFlex\040Home\040Public\Media   /mnt/nas2   cifs   username=username,password=password,iocharset=utf8,file_mode=0777,dir_mode=0777,_netdev   0 0
```

---

