---
title: "NFS Won't Start"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by Bugs318 on 2010-05-05
After working fine for many months, suddenly my file sharing through NFS wouldn't connect.  I went back to the book that help me set it up (as I am no expert), and attempted to restart the nfs server with the command

sudo /etc/init.d/nfs-kernel-server start

It would not start and I got the following error:

Cannot register service: RPC: Unable to receive; errno = Connection refused         [fail]

A bit of searching on the internet led to discovering that this is often a common problem surrounding the 'portmapper' not being on or the port being blocked.  I am uncertain of what port this is shared over, so I don't know how to ensure it is unblocked (presumably by the firewall?), and I have no idea how to check if the portmapper is started (or how to start it, or even what it is - if this is indeed the problem).

Any help would be greatly appreciated and I thank you in advance!

---

### Post by Bugs318 on 2010-05-05
If anyone can even hint at possible ways to resolve this that would be great as I am in quite desperate need of the file sharing, without which I am forced to constantly burn discs for file transfers.

Thanks again in advance!

---

### Post by Bugs318 on 2010-05-06
After many hours of searching, I finally found instructions for how to restart portmapper and now it works fine.  Why is this information so hard to find?!?

---

### Post by airtonix on 2011-02-10
> **Bugs318 said:**
>  Why is this information so hard to find?!?

Because people like you don't bother to mention where you found the information.

IRONY MUCH!???

---

### Post by ChrisChambers on 2012-03-14
I just stumbled across this post with the same issue on Ubuntu 11.10.

Doing the following commands rectified my NFS problem - 

```
# service portmap restart
# service nfs-kernel-server restart
```

---

