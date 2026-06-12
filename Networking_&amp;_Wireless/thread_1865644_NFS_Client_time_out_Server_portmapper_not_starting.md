---
title: "NFS Client time out Server portmapper not starting after upgrade"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by Horatio on 2011-10-20
I had just recently upgraded from 11.04 to 11.10, and I then could not make NFS mounts. The client machine would try until timing out, and the first thing I noticed on my server was the error message complaining that portmapper is not started. I finally noticed when purge-ing( ***removes etc and other config files***) and re-install-ing nfs-common and nfs-kernel-server that there was a message that explained that /var/lib/nfs is not empty and will not be removed. So found a lock file( .etab.lock), and I removed it and ,'/var/lib/nfs', after purge-ing nfs-common and nfs-kernel-server. I then had search for portmap with both ,'aptitude search portmap'( usually my favorite), and apt-cache search portmap', and apt-cache gave me the hint that package rpcbind really contained portmap. So I purge-d and re-install-ed rpcbind, and then install-ed nfs-common and nfs-kernel-server. Now NFS seems to be working as needed. 

Okay. This really tortured me. Maybe this will help someone.

---

### Post by Aison on 2011-10-20
Hi,

Yes, i've got the same problem here.

-Aison

---

