---
title: "sshfs not mounting at system start"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by newpipe on 2013-03-19
Hi!
I created an entry in the fstab to automount a remote directory over ssh.
Everything works fine but it does not automount on system start.

The fstab entry is:
```
sshfs#mine@server1.ath.nu:/storage/filme/Filme/        /storage/movies/server     fuse    compression=yes,uid=1000,gid=100,umask=0,allow_other,_netdev    0       0
```
It correctly mounts when typing on the command line
```
mount -a
```

Is there any way to get it automatically mounted on system start?

My system is Ubuntu 12.04

Thanks,
newpipe

---

