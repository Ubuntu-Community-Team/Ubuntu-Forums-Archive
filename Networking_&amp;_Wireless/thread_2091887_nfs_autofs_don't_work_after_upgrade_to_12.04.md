---
title: "nfs autofs don't work after upgrade to 12.04"
date: 2012-12-06
forum: Networking &amp; Wireless
---

### Post by bilkay on 2012-12-06
After upgrading my desktop server from 10.04 to 12.04 (after previously upgrading my laptop), the autofs nfs mounts on my laptop no longer work. They worked with the laptop upgraded and the desktop still at 10.04. The nfs-kernel-server on the desktop appears to be running but all mount attempts fail. 

bilkay@Laptop:~$ mount -t nfs Saturn:/home /mnt
mount.nfs: an incorrect mount option was specified


This is what I get in syslog after restarting nfs-kernel-server:
```

Dec  6 09:45:44 Saturn mountd[17549]: Caught signal 15, un-registering and exiting.
Dec  6 09:45:44 Saturn kernel: [70736.891862] nfsd: last server has exited, flushing export cache
Dec  6 09:45:46 Saturn kernel: [70738.033341] svc: failed to register lockdv1 RPC service (errno 97).
Dec  6 09:45:46 Saturn kernel: [70738.033405] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Dec  6 09:45:46 Saturn kernel: [70738.033445] NFSD: starting 90-second grace period
```

---

### Post by dannyboy79 on 2012-12-06
do you have nfs-common installed, that's what clients use to mount NFS server shares.

---

### Post by bilkay on 2012-12-06
> **dannyboy79 said:**
> do you have nfs-common installed, that's what clients use to mount NFS server shares.
As I described, the client had no problem with nfs mounts prior to the server upgrade, so it was installed. However, I did another install and it was upgraded, and now it works.

Thanks for the tip.

---

