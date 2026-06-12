---
title: "autofs error cifs 22"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by Thibaud74 on 2012-02-18
Hi,

I'm trying to use autofs to avoid deconnexions with my NAS and samba. I successed on my netbook, not with my laptop ? Here is my config :
```
auto.master
/net/smb_ro /etc/auto.smb  --ghost,--timeout=30,--fstype=cifs,username=hulin,uid=1000,gid=1000

```
I can see my NAS and the root folder, but not read files in the root folder :
```
$ ls /net/smb_ro/NAS/
ADMIN$  archives
$ ls /net/smb_ro/NAS/archives/
ls: impossible to access to /net/smb_ro/NAS/archives/: No file or folder of this type
$ dmesg | tail
[ 5216.055161] CIFS VFS: cifs_mount failed w/return code = -22

```

Thanks for your help,
Thibaud.

---

