---
title: "Help fix NFS"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by speedsix on 2006-07-09
I tried to install 'portmap' not realising it was already installed. This seems to have broken the NFS server (nfs-user-server).

When I do sudo /etc/init.d/nfs-user-server start I get..
```
Starting NFS servers: nfsdCannot register service: RPC: Timed out
```

When I try to restart portmap it just seems to hang on 'Stopping Portmap Daemon...'


I also tried the nfs-kernel-server package with no joy either. I want to reinstall portmap but I cannot seem to stop the daemon, I may be barking up the wrong tree here though.

Any help much apreciated.

Thanks

Dom

---

### Post by speedsix on 2006-07-09
Something I've just noticed, on boot it comes up saying 'Not starting Portmap Daemon as it's already Running'. 

Odd.

---

