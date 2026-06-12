---
title: "Network connection suddenly disappears and gets back waking up display"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by Luc484 on 2012-05-09
Hi! This strange this is happening to me since I updated to 12.04. My  desktop PC remains up 24h, and it seems that after some time, random intervals I think, the network connection suddenly disappears. I cannot reach it anymore.

The PC is commonly up but without input devices. It is sufficient to plug in the mouse and immediately the display shows turns on (was in standby) and the connection appears again.

I did this test: noticed the system was not reachable, so I started to ping it and got repeatedly:

Request timeout for icmp_seq 1
ping: sendto: Host is down
...

I plugged in the mouse and immediately the screen turned on and the ping succeeded:

...
Request timeout for icmp_seq 17
ping: sendto: Host is down
Request timeout for icmp_seq 18
ping: sendto: Host is down
Request timeout for icmp_seq 19
ping: sendto: Host is down
Request timeout for icmp_seq 20
Request timeout for icmp_seq 21
64 bytes from 192.168.1.2: icmp_seq=22 ttl=64 time=104.507 ms
64 bytes from 192.168.1.2: icmp_seq=23 ttl=64 time=1.477 ms
64 bytes from 192.168.1.2: icmp_seq=24 ttl=64 time=1.375 ms
64 bytes from 192.168.1.2: icmp_seq=25 ttl=64 time=1.509 ms
64 bytes from 192.168.1.2: icmp_seq=26 ttl=64 time=1.487 ms
64 bytes from 192.168.1.2: icmp_seq=27 ttl=64 time=1.244 ms
...

Like the system was going to sleep. Anyone with an idea of what this might be? I've never had this problem before.
Thanks!

---

### Post by Luc484 on 2012-05-10
If anyone else found this problem, I reported it here: [https://bugs.launchpad.net/ubuntu/+bug/997767](https://bugs.launchpad.net/ubuntu/+bug/997767).

---

