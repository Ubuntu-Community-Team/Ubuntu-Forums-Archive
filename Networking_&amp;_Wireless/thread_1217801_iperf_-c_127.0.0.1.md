---
title: "iperf -c 127.0.0.1"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-07-20
I iperf -c 127.0.0.1 and get around 4Gbps. What does it mean?

---

### Post by cariboo on 2009-07-20
That is a pretty useless stat, as all your are doing is checking the internal speed of a loopback connection.

To use iperf properly you need two computers on the same network, then setup one as a server, then on the other issue the command:

```
iperf -c server
```

btw I'm moving this to Networking & wireless

---

