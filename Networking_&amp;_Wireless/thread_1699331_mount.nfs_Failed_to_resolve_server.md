---
title: "mount.nfs: Failed to resolve server"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by n8_sl8er on 2011-03-03
I'm running Ubuntu 10.10 with all the updates. I'm in an NFS/NIS networked environment. My mounts eventually work, but mountall fails with this message in /var/log/boot.log:

mount.nfs: Failed to resolve server myservername: Name or service not known

Here's the entry in /etc/fstab:
myservername:/nfs/share/path /mount/path  nfs     rw,_netdev,bg,hard,intr,rsize=8192,wsize=8192 0 0

Here's the host entry in /etc/hosts:
123.45.678.901		myservername

I've seen several "fixed" bugs relating to this, but for some reason the fixes don't seem to apply to me. Anyone else experiencing this issue?

I've noticed that mountall seems to be trying to mount my share before it has network access.

---

### Post by gadLinux on 2011-03-05
I have the same issue. It worked fine before upgrading...

Don't know but seems as if network resolution was not in place before trying to mount

---

### Post by tehsi on 2011-03-17
I have this problem too.

---

