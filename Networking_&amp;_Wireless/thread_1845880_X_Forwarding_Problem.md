---
title: "X Forwarding Problem"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by richyrich999 on 2011-09-17
I'm having a problem with xforwarding from an ubuntu desktop to an OS X environment.  I've changed all the /etc/ssh/sshd_config files on ubuntu, and was wondering if this is a problem with OS X or an ongoing problem.

---

### Post by Mr. Sanity on 2011-09-19
I just ran into this problem after patching today.

Luckily I was able to work out the issue. In my case, the update seemed to turn on xhost server access control.
```
sudo xhost
access control enabled, only authorized clients can connect
```

To turn it off:
```
sudo xhost +
access control disabled, clients can connect from any host
```

Hopefully, this works for you!

---

