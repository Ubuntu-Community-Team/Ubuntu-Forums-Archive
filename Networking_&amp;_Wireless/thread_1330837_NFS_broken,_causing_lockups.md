---
title: "NFS broken, causing lockups"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by stdPikachu on 2009-11-18
Following a powercut, one of my media slaves is no longer picking up its NFS connection, and any attempt to mount them manually (either via mount -a or mount -t nfs) causes the console to lock up, random commands will fail to execute and I have to button the system. There's no indication what's cauing this error; other NFS clients can mount these directories fine.

On the server exports:```
/storage/movies         banquo(ro,sync,no_subtree_check)
/storage/music          banquo(ro,sync,no_subtree_check)
/storage/tv             banquo(ro,sync,no_subtree_check)
```
From the server logs:```
Nov 18 21:20:03 prospero mountd[1878]: authenticated unmount request from 192.168.1.20:896 for /storage/tv (/storage/tv)
Nov 18 21:20:03 prospero mountd[1878]: authenticated unmount request from 192.168.1.20:897 for /storage/tv (/storage/tv)
Nov 18 21:22:36 prospero mountd[1878]: authenticated mount request from 192.168.1.20:749 for /storage/tv (/storage/tv)
Nov 18 21:22:39 prospero mountd[1878]: authenticated mount request from 192.168.1.20:794 for /storage/music (/storage/music)
Nov 18 21:22:39 prospero mountd[1878]: authenticated mount request from 192.168.1.20:931 for /storage/movies (/storage/movies)
Nov 18 21:27:41 prospero mountd[1878]: authenticated mount request from 192.168.1.20:805 for /storage/movies (/storage/movies)
``````
Nov 18 21:09:00 prospero kernel: [   10.763154] svc: failed to register lockdv1 RPC service (errno 97).
Nov 18 21:09:00 prospero kernel: [   10.763740] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Nov 18 21:09:00 prospero kernel: [   10.763893] NFSD: starting 90-second grace period
``````
rpcinfo -p prospero
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  49668  status
    100024    1   tcp  52391  status
    100021    1   udp  58188  nlockmgr
    100021    3   udp  58188  nlockmgr
    100021    4   udp  58188  nlockmgr
    100021    1   tcp  32848  nlockmgr
    100021    3   tcp  32848  nlockmgr
    100021    4   tcp  32848  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  59662  mountd
    100005    1   tcp  45255  mountd
    100005    2   udp  59662  mountd
    100005    2   tcp  45255  mountd
    100005    3   udp  59662  mountd
    100005    3   tcp  45255  mountd
```
NFS has been restarted more times than I care to mention... anyone have any idea how to fix this?

---

