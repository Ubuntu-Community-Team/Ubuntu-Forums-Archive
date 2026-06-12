---
title: "Wired Connection Stopped Working"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by SpiderGuard on 2011-03-20
I'm running 10.10 on a brand new computer, and up until this afternoon the wired connection was working fine. All of a sudden it stopped working (and doesn't work in Windows either).

Any suggestions on how this went wrong?

----------
I ran sudo dhclient and it gave me:

DHCPDISCOVER on eht- to 255.255.255.255 port 67 interval 3 (7, 9, 10, 18, 13)
No DHCPOFFERS RECEIVED
No working leases in persistent database sleeping

-----------------

sudo ifconfig -a gave me

eth0 link encap: Ethernet HWaddr bc:ae:c5:4f:1e:13
UP BROADCAST MULTICAST MTU: 1500 Metric:1
RX packets: 0 errors: 0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt: 41 Base address:0x8000

eth0:avahi Link encap: ehternet HWaddr: bc:ae:c5:4f:1e:13
inet addr: 169.254.4.253 Bcast: 169.254.255.255 Mask 255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric: 1
Interrupt:41 Base address:0x8000

lo Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0 
inet6 addre: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:144 errors:0 dropped:0 overruns:0 frame:0
TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX byters:10672 (10.6 KB) TX bytes: 10672 (10.6 KB)
----------

Any advice?

---

### Post by nixxofugi on 2011-03-20
same problem here... please help

---

### Post by belkinsa on 2011-03-20
Same with me.

---

