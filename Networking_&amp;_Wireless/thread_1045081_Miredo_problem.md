---
title: "Miredo problem"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by Pitel on 2009-01-20
Hi,
I wanted to play with IPv6 and I read teredo is the easiest way, so I intalled Miredo. It worked rigth after the installation, but now, after the reboot, it doesn't.

It starts ok, it creates teredo network interface, but it doesn't work.

When I try to launch it manually, it says:
```

pitel@mana2:~/Desktop$ sudo miredo -f
miredo[15902]: Starting...
miredo[15903]: New Teredo address/MTU
miredo[15903]: Teredo pseudo-tunnel started
miredo[15903]:  (address: 2001:0:53aa:64c:4ce:38aa:a18f:67fa, MTU: 1280)
Error: argument "teredo" is wrong: "table" value is invalid

Error: argument "teredo" is wrong: invalid table ID

```

I've no idea what those errors mean. Can someone help me?

---

### Post by Pitel on 2009-01-20
Solved: disable ipv6 module.

---

