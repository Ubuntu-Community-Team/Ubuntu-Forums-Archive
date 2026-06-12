---
title: "nfs client in 10.10 times out"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by miko3k on 2010-11-03
hey guys,

I'm sharing some directories using NFS between my machines. I recently upgraded client machine to 10.10 and my nfs mounts stopped working. Server is 10.04, running stock unfsd (version 0.9.21+dfsg-1). Both systems are 32 bit. 

I worked around this issue by downgrading nfs-common to 1:1.2.0-4ubuntu4 (lucid version). 

My fstab entry looks like this:
```
blackstar:/var/www /var/www nfs port=2049,mountport=2049,mountproto=tcp,nomand,tcp 0 0
```

Mount used to tell me:
```
mount.nfs: Connection timed out
```

I don't like my solution at all. Anybody got an idea what went wrong or what changed?

---

### Post by chuckbennett1961 on 2011-04-27
I have an older RH 9 system I was trying to nfs mouunt.  I had a heck of a time, I always got the timeout message from mouunt.  Then I put this line in my fstab and it worked.  Can't remember where I got it.  My server is Ubuntu server 10.10.

(server.com):/backup /backup  nfs  nfsvers=2,suid,dev,exec       0  0

---

