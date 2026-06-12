---
title: "installing xmms"
date: 2009-08-17
forum: Multimedia Software
---

### Post by number3 on 2009-08-17
I'm on 8.04 Hardy trying to install xmms.

I use apt-get install xmms and get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate


I've followed the procedure on this page [https://help.ubuntu.com/community/XMMS](https://help.ubuntu.com/community/XMMS) but still get the same problem.

Can someone please tell me how they got xmms installed on their machine?

---

### Post by harry2006 on 2009-08-17
> **number3 said:**
> I'm on 8.04 Hardy trying to install xmms.

I use apt-get install xmms and get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate


I've followed the procedure on this page [https://help.ubuntu.com/community/XMMS](https://help.ubuntu.com/community/XMMS) but still get the same problem.

Can someone please tell me how they got xmms installed on their machine?
the error messages says xmms is not in the repo configured under /etc/apt/sources.lst. First make sure you have the required repos added in your sources file of apt. 
that apart, I suggest the best option would be to _UPGRADE_ to 9.04 ...else you'll find it difficult to get support for older versions of Ubuntu.

---

### Post by number3 on 2009-08-17
> **harry2006 said:**
> the error messages says xmms is not in the repo configured under /etc/apt/sources.lst. First make sure you have the required repos added in your sources file of apt. 
that apart, I suggest the best option would be to _UPGRADE_ to 9.04 ...else you'll find it difficult to get support for older versions of Ubuntu.

Thanks harry, I'll just upgrade my Ubuntu.

---

