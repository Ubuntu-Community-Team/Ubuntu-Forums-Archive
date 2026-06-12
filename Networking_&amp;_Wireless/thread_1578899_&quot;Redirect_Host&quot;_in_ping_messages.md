---
title: "&quot;Redirect Host&quot; in ping messages"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by mahmoodn on 2010-09-21
What does these messages in PING mean?
```
PING 192.25.141.248 (192.25.141.248) 56(84) bytes of data.
From 192.25.141.229: icmp_seq=1 **Redirect Host(New nexthop: 192.25.141.248)**
From 192.25.141.230: icmp_seq=1 **Redirect Host(New nexthop: 192.25.141.248)**
From 192.25.141.210: icmp_seq=2 **Redirect Host(New nexthop: 192.25.141.248)**
From 192.25.141.230: icmp_seq=2 **Redirect Host(New nexthop: 192.25.141.248)**
From 192.25.141.229: icmp_seq=2 **Redirect Host(New nexthop: 192.25.141.248)**
64 bytes from 192.25.141.248: icmp_seq=2 ttl=59 time=3.81 ms
64 bytes from 192.25.141.248: icmp_seq=2 ttl=59 time=3.83 ms **(DUP!)**
64 bytes from 192.25.141.248: icmp_seq=2 ttl=59 time=3.90 ms **(DUP!)**
64 bytes from 192.25.141.248: icmp_seq=2 ttl=59 time=48.0 ms (**DUP!)**

```

---

### Post by CharlesA on 2010-09-21
Check [here]("http://en.wikipedia.org/wiki/ICMP_Redirect_Message").

Basically it means that the packet was set along a different route to the destination then originally intended.

---

### Post by mahmoodn on 2010-09-21
I read that but I want to know why such thing happens. If you notice, in the middle of the ping, I receive a reply. That means the host is up. So Why that happens? Another thing I want to know is DUP! messages. What does that mean?

---

### Post by CharlesA on 2010-09-24
> **mahmoodn said:**
> I read that but I want to know why such thing happens. If you notice, in the middle of the ping, I receive a reply. That means the host is up. So Why that happens? Another thing I want to know is DUP! messages. What does that mean?

It's just informational. DUP! means duplicate.

It can mean there is a problem with it receiving duplicate packets.

Does it happen for every site you try to ping?

---

### Post by mahmoodn on 2010-09-24
No some times it happen when I ping my remote host. It seems there is a problem with the gateway in the remote site.

---

