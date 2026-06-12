---
title: "Ping gives Destination Host Unreachable"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by Zeophlite on 2011-03-17
I'm unable to access the internet using my Ubuntu Server 10.4 install:

```

**daniel@workwork:~$** ping www.google.com
ping: unknown host www.google.com
**daniel@workwork:~$** ping 74.125.237.49
PING 74.125.237.49 (74.125.237.49) 56(84) bytes of data.
From 192.168.69.136 icmp_seq=1 Destination Host Unreachable
From 192.168.69.136 icmp_seq=1 Destination Host Unreachable
From 192.168.69.136 icmp_seq=1 Destination Host Unreachable
From 192.168.69.136 icmp_seq=1 Destination Host Unreachable
From 192.168.69.136 icmp_seq=1 Destination Host Unreachable
From 192.168.69.136 icmp_seq=1 Destination Host Unreachable
^C
--- 192.168.69.136 ping statistics ---
9 packets transmitted, 0 received, +6 errors, 100% packet loss, time 8368ms, pipe 4
**daniel@workwork:~$ **

```

---

### Post by crispy_420 on 2011-03-18
skip the www and just go google.com

Firewall on network?

---

