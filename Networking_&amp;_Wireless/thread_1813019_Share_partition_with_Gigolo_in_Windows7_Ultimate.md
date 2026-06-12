---
title: "Share partition with Gigolo in Windows7 Ultimate"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by simfomet on 2011-07-27
Hi,

a few days ago I installed in a netbook Xubuntu 11.04 and the only problem that I have is that I would like to share a partition of a hard drive with Windows 7 Ultimate installed. The partition is already shared in network and I can see it with a laptop with windows but I have no idea what to do in Xubuntu. 
Recently I noticed about and application called Gigolo and I think I can connect the computers with it but I don't know how. Please I need help!

---

### Post by Morbius1 on 2011-07-27
I'm confused by your post.

> a few days ago I installed in a netbook Xubuntu 11.04 and the only  problem that I have is that I would like to share a partition of a hard  drive with Windows 7 Ultimate installed.Win7 is on another machine in the network or is this a dual boot?
> The partition is already shared in network and I can see it with a  laptop with windows but I have no idea what to do in Xubuntu. That's where you lost me. If you post the output of each of the following commands from Xubuntu perhaps it will become clear:
```
testparm -s
net usershare info --long
```> Recently I noticed about and application called Gigolo and I think I can connect the computers with it but I don't know how.Gigolo is a utility to access someone else's share not to create a share for someone else to access.

---

### Post by simfomet on 2011-07-28
You're right about my post, it's a little bit confusing. Windows 7 is in another machine in the network. I would like to access to the partition of another computer from my netbook in my home network. All the computers have access to internet with the same router.

Thanks.

---

### Post by simfomet on 2011-08-05
Finally I solved the problem connecting with Gigolo [http://www.dedoimedo.com/computers/xubuntu-natty.html](http://www.dedoimedo.com/computers/xubuntu-natty.html)

---

