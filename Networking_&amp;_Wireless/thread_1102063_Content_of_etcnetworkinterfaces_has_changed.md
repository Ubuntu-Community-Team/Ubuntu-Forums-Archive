---
title: "Content of /etc/network/interfaces has changed"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by antti64 on 2009-03-21
Hi!

I found content of /etc/network/interfaces has changed between Ubuntu 7.10 and 8.04. 

I tried to release IP address of my desktop by 'ifdown'. However it failed 

```

>> ifdown eth0
ifdown: interface eth0 not configured
```

Long time ago this has worked fine. At least when my desktop was 7.10. Now I have 8.04. After some googling I learned eth0 must be included in /etc/network/interfaces. Then ifdown and ifup can work on these interfaces.

I added these lines:
```
auto eth0
iface eth0 inet dhcp
```

After this I was successfully able to ifdown and ifup my interfaces. The question is why the content of the /etc/network/interfaces has changed between 7.04 and 8.04?

Antti

---

