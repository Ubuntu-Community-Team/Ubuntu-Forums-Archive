---
title: "Install nfs-common on a PXE thick client"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by SeaKing on 2012-11-18
Hello,

I need to install nfs-common on a thick client but there  are some problems, the  debian client was installed by debootstrap and  nfs-common with chroot. Now if I boot the Client I get the following  error message: 
```

rpc.statd: unable to register (statd, 1, udp)

```After googleing a bit I installed rpcbin but this installation throw out this error:
```

rcpbind: Cannot open '/var/run/rpcbind/rpcbind.xdr' file for reading, error 2 (no such file or directory)

```my fstab
```

proc            /proc         proc    defaults 0 0 
/dev/nfs        /             nfs     defaults 0 0 
none            /tmp          tmpfs   defaults 0 0 
none            /var/tmp      tmpfs   defaults 0 0 
none            /media        tmpfs   defaults 0 0 
none            /var/log      tmpfs   defaults 0 0

```If I would add this to my fstab

```
 none            /var/run      tmpfs   defaults 0 0
```The error would occure as well, the file rcpbing could not be stored, right?

---

