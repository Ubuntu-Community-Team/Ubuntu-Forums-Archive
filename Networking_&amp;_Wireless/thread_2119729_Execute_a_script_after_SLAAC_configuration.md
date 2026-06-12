---
title: "Execute a script after SLAAC configuration"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by nvtshax0r on 2013-02-24
Is it possible to execute a custom script after receiving a new route advertisement which would cause an ethernet interface to be reconfigured using SLAAC?  This is pretty straightforward with dhcp (both v4 and v6) since it uses a userspace daemon, but since SLAAC is in-kernel, i'm not sure it's even possible - hence I'm asking... It is not as simple as putting something in an if-up.d directory, since the interface will be up when the RA arrives and the new ipv6 address is generated.

---

