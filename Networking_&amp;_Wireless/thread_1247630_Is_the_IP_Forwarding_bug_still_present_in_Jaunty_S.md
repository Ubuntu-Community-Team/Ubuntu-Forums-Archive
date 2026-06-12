---
title: "Is the IP Forwarding bug still present in Jaunty Server ?"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by jonathanross on 2009-08-23
Hello all,

I've had some trouble forwarding traffic between two NICs on a production box using Jaunty Server. Does anyone know if this is still an issue or was it fixed in Jaunty ? I can't try it until it's out-of-hours (middle of the night).

[https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537)

I'm hoping the bug caused the strangeness. (net.ipv4.ip_forward=1 was enabled but not "net.ipv4.conf.**all.**forwarding=1" in addition to "net.ipv4.conf.default.forwarding=1").

Appreciation in abundance for any help :)

JR

---

### Post by jonathanross on 2009-08-23
It's a real head scratcher ... I've done a "sysctl -A" on a kernel on a box that works (it's a different distribution) and run "diff" against the Jaunty Server but rp_filter and the forwarding were the only obvious differences.

JR :(

---

