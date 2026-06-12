---
title: "NFS Problem"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by hobit on 2009-12-30
I'm having a permissions problem with NFS.  Server is Ubuntu 6.06 and the client is Ubuntu 9.10.  Everything seems fine on the server end as it serves up the NFS partition and the client can mount it.  My problem is that after a few minutes the client looses all permissions except read, to the NFS share.  When it is first mounted I have full RW access.

Server export file
```
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
/mnt/NFS 192.168.0.0/24(rw,no_root_squash,async)
```

I've followed the guides that can be found on this site but still no luck.  The only issue that I can see is that on the client machine there is no /etc/init.d/nfs-common file; nfs-common and portmap are both installed on the client.

Any help would be greatly appreciated as this is getting rather frustrating.

Thanks.

---

### Post by hobit on 2010-01-04
I have checked the UID's, ownership, permissions, config files etc. and all are fine.

A new NFS mount allows me full access (rw) but after I alter a file or create a folder the permissions regress to read only.

I have to umount and restart the NFS service on the server and client to reset the rw rules but no matter what it always reverts back to read only.

Any thoughts?

Thanks.

---

