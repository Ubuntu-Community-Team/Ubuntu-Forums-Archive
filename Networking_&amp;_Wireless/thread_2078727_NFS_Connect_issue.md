---
title: "NFS Connect issue"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by blackdiamondute on 2012-10-31
I am tying to get my NFS server working by mounting a local drive:
 
```
sudo mount -t nfs localhost:/home/michael/iMX6/LTIB/ltib/rootfs /tmp/test_rootfs
mount.nfs: access denied by server while mounting localhost:/home/michael/iMX6/LTIB/ltib/rootfs
```my exports file has the following:

```
/home/michael/iMX6/LTIB/ltib/rootfs *(rw,async,no_root_squash,no_subtree_check,insecure)
```Any help would be great

---

### Post by blackdiamondute on 2012-10-31
It appears that this was a permissions problem from one of the parent directories of the directory I was trying to mount.  Gave the group and others read access and then the problem went away.

---

