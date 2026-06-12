---
title: "PING returns no result for unreachable hosts"
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by samanca on 2012-12-28
Dear all,

I have installed Ubuntu 11.04 on a VMWare Virtual Machine. Everything is fine except for the PING command that does not return any output for unreachable hosts.
For all available hosts, regardless of calling ping with a hostname or an ip address, it works just fine. However, it does not return any response for unreachable hosts.

Apache Hadoop uses PING as a tool for checking host availability and I need to have it working for this purpose.

If you know a solution for this problem or the way that I can change the default timeout of PING requests permanently, please let me know.

---

### Post by CharlesA on 2012-12-28
Do you have a firewall that is blocking everything except for the echo-reply?

---

### Post by samanca on 2012-12-28
I am sure that this problem is not caused by the firewall, as I have stopped the firewall, but the output did't change.
Moreover, the PING command on my host operating system (Mac OS) is working fine for both reachable and unreachable hosts.

---

