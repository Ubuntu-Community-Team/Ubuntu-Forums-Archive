---
title: "Iperf throughput test between two NIC'S"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by luk-a-sz on 2011-05-30
Hi,

I have pc with two NIC's (eht0 and eth1). I want to test throughput switch/router.
I can ping on both interfaces.

Connection Diagram:

eth0 -> Patchcord -> testing devices -> Patchcord -> eth1

I run two iperf:

-s -B 192.168.1.10 (eth0)
-c 192.168.1.20 -B 192.168.1.20 (eth1)

Results:
[  3]  0.0-10.0 sec  4.45 GBytes  3.82 Gbits/sec

The test results are false because I use 100Mb/s NIC's.  I can't use two pc's for test.
I tried to do the same test under windows 7 x64 it and works properly, but under windows xp there occurs 

the same problem like under ubuntu. I think problem is in OS.

Could You help me find a solution?

---

### Post by luk-a-sz on 2011-05-31
Nobody knows?

---

