---
title: "autofs and vpn"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by washakie on 2009-11-04
Hello,

I'm running 9.10 64bit, using autofs and a cisco vpn client.

I have my autofs configured with a soft link at the root level to one of my mounted directories to keep it consistent with other machines I work on. I believe this causes the mount to always be active. A problem arises when I connect the VPN, then my whole directory environment (for lack of a better term) freezes. What I mean is, any terminal or file system browser hangs. The same is true when I disconnect.

My solution has been to stop autofs prior to running the VPN, but this doesn't seem like it should be necessary. My question is twofold:

1) Is this a bug in autofs? Why does it hang the entire file system just because the network configuration changes, shouldn't it just reconnect? Here is my auto.mountpoint file:
```

wrk -fstype=fuse,intr,nodev,allow_other,default_permissions,workaround=nodelaysrv,reconnect,uid=1000,gid=1000,umask=002,sshfs_debug,IdentityFile=/home/user/.ssh/id_rsa :sshfs\#user@server\:/wrk
```

2) Is there a better way to 'recreate' the /wrk root mount point rather than the soft link?

Thanks!

---

