---
title: "Missing mountd, NFS not working"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by ubuntie on 2011-01-04
Hi all,

I'm trying to set up a Ubuntu box as an NFS server. I've set up /etc/exports, /etc/hosts.allow. I've installed nfs-common. I've got everything as far as I know installed but yet, when I run rpcinfo -p, I do not see mountd. Everything else seems normal.

On the client machine, when I try to mount I get a Program not registered error.

As a matter of fact, when I do a 'find' for *mountd* in /usr and /etc I don't see anything. The literature says rpc.mountd should be a part of nfs-utils, but of course Ubuntu lacks a package by that name and nfs-common does not seem to have it.

Help?
Thanks.

---

### Post by ubuntie on 2011-01-04
I solved it.

Turns out nfs-utils is not in nfs-common as I assumed, but rather in nfs-kernel-server.

---

