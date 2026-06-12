---
title: "karmic TCP failures"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by Freezer52000 on 2010-03-11
I noticed this behavior after several days of uptime.
At some point, TCP connections start failing in all applications. I fired up Wireshark and saw my system send the usual SYN, receive SYN+ACK, but then sends RST.
It's as if I've hit some limit, perhaps a memory leak of some sort.

It's not related to one particular application, or one particular net host; logout/login doesn't help, only a full restart clears the problem.

Any ideas how to debug this?

Thanks.

---

### Post by Freezer52000 on 2010-03-22
Resolved - my router apparently messes up TCP timestamps, which are enabled by default.
"echo 0 > /proc/sys/net/ipv4/tcp_timestamps" clears the issue.

---

