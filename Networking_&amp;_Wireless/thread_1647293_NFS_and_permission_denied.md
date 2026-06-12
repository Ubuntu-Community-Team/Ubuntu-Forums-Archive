---
title: "NFS and permission denied"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by f8a on 2010-12-17
Hello,

My nfs setup started acting up today. I cannot find the error in my config. Heres the details:

192.168.1.40 - nfs server
192.168.1.9 - client machine

On the server:

/etc/exports:
```
/backup                 192.168.1.9/255.255.255.255(ro,sync,no_subtree_check,no_root_squash)
```On the client:

/etc/fstab:
```
192.168.1.40:/backup  /nas/backup     nfs     ro,noauto,noexec,nosuid 0 0
```Now this *seems* to work. On the client:

```
% mount 
...
192.168.1.40:/backup on /nas/backup type nfs (ro,noexec,nosuid)
...
```Up to this point everything is as expected. /nas/backup is mounted properly. Problem is with permissions. For example:
```

client% id
uid=/*snip*/ gid=/*snip*/ groups=4(adm),20(dialout),24(cdrom),46(plugdev),105(lpadmin),115(admin),116(sambashare),1000(/*snip*/),1021(spbak)
client% ls -ld /nas/backup/tmp
drwxr-x--- 2 1021 spbak 4096 2010-07-22 08:51 /nas/backup/tmp
client% ls -l /nas/backup/tmp 
ls: cannot open directory /nas/backup/tmp: Permission denied

```So as shown above my user is in the spbak group but still I cannot access directory tmp which I think I should be able to access according to permissions.

Any pointers would be greatly appreciated ;)

---

