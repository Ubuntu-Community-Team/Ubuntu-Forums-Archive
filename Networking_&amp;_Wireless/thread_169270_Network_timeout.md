---
title: "Network timeout?"
date: 2006-05-02
forum: Networking &amp; Wireless
---

### Post by nolongerlivecd on 2006-05-02
Hi, I have a problem with my firefox. Right now, it regularly times out, no matter what activity I peruse on the net. It just does not connect properly.

Also, I can only occaisionally access network share folders and printers, not all the time. Why would this be so?

---

### Post by mips on 2006-05-02
IPv6 maybe ?

---

### Post by nolongerlivecd on 2006-05-03
I don't get it. What about ipv6? I disabled it on firefox long after it (firefox) started killing me

---

### Post by mips on 2006-05-03
Try disabling IPv6 globally and also have a look at your DNS configuration.

---

### Post by nolongerlivecd on 2006-05-03
How do I do that?

---

### Post by mips on 2006-05-04
IPv6:
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak

sudo depmod -a
```

Edit your /etc/resolv.conf file. Remove your routers IP address from there and add your ISPs two DNS server IPs instead.

See if it makes a difference.

---

