---
title: "ubuntu 12.10 (armhf) DNS issues"
date: 2013-08-04
forum: Networking &amp; Wireless
---

### Post by JoinTheRealms on 2013-08-04
Hey guys, first off im not sure this is the correct place to post this as my setup is "special" im running ubuntu 12.10 (armhf) on my asus transformer tf700

Im having trouble with dns, apt-get is working fine but anything requiring dns is failing, but strangely it works when running with su permissions for example

the output of(without sudo): 
$ping [www.google.com]("http://www.google.com")  
ping: unknown host [www.google.com]("http://www.google.com")

but sudo ping [www.google.com]("http://www.google.com") works and pings fine

This issue only occurred after a change in kernel, im really unsure on how to proceed. Im guessing some permissions need to be changed somewhere but im unsure of what need to be changed.

---

### Post by JoinTheRealms on 2013-08-05
Problem solved, the issue is with a kernel config relating to android. This issue will also affect chroot installations on some android devices.
The fix is to add these lines to /etc/groups

```
inet:x:3003:root,*user*
net_raw:x:3004:root,*user*
```

---

