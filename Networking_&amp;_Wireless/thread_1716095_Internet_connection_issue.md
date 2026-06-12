---
title: "Internet connection issue"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by Ocxic on 2011-03-28
I've setup my computer to act as a router for the rest of my house.. just today while mucking about with samba, I've lost the ability to browse the web.  I can't ping and sites, and this seems to be DNS issue however the rest of the computers on the network are working fine. it's just mine that is having an issue.

Can anyone offer some insight into this??

thx

I had mad changes to my /etc/nsswitch.conf file and added "wins" to my host line.. after removing that everything returned to normal.

---

### Post by Dark_Stang on 2011-03-28
Can you ping IP addresses outside your network? That would confirm if it's a DNS issue vs. a Routing/Connection issue. You can try to ping one of the following addresses (they're just Google DNS servers).
8.8.8.8
8.8.4.4

---

### Post by Ocxic on 2011-03-28
yes I can ping actual ip addresses, so i know there is no connection issue. Plus all the other computers mine is routing and providing NAT for work fine.

I should mention that when i ping any hostname or web address ping seems to freeze and I never get any output no matter how long i wait. I end up having to hit cntl-C to stop it.

---

### Post by Dark_Stang on 2011-03-28
So we know it's a DNS issue. Let's see what your computer is set to do for DNS. Run the following command to see what DNS server(s) your computer is looking for.
```
dig | grep "SERVER"
```

---

### Post by Ocxic on 2011-03-28
```

root@xilti:~# dig | grep "SERVER"
;; SERVER: 10.0.2.1#53(10.0.2.1)
root@xilti:~# 

```

10.0.2.1 is my eth1 interface that is running a BIND9 dns server. and forwards the queries to OpenDNS. this his worked for months like this.

---

