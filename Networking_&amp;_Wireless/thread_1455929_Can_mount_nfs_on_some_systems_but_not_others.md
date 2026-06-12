---
title: "Can mount nfs on some systems but not others"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by icedown on 2010-04-16
I have 4 systems, all linux, all on the same network and subnet.  
```

galaxy     Gentoo x86            10.0.0.1
phantom    Ubuntu x86    karmic  10.0.0.7
atlantis   Ubuntu x86_64 karmic  10.0.0.5
enterprise Gentoo x86_64         10.0.0.10

```
Here is my /etc/exports for phantom

```
/var/noaaport/data/gempak 10.0.0.0/24(ro,async,no_subtree_check)
/var/noaaport/data 10.0.0.0/24(ro,async,no_subtree_check)
/var/noaaport/nbsp/stats 10.0.0.1/24(ro,async,no_subtree_check)

```

I am trying to get the last one to mount on galaxy but it fails with:

```
mount.nfs: mount to NFS server 'phantom:/var/noaaport/nbsp/stats' failed: RPC Error: Program not registered 
```

I have no errors mounting the first 2 on enterprise.  There is an identical export on atlantis and galaxy has no problems mounting it. 
I've tried mounting the other 2 from phantom on galaxy but they produce the same error.



here is the relevant part of galaxy's fstab

```
atlantis:/var/noaaport/nbsp/stats /root/scripts/stats/atlantis nfs      nfsvers=3,ro    0 0 
phantom:/var/noaaport/nbsp/stats /root/scripts/stats/phantom nfs        nfsvers=3,ro    0 0 
``` 


Any idea what is going on here?

---

