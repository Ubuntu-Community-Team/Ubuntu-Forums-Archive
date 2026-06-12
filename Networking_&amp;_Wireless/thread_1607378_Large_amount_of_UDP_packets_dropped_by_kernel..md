---
title: "Large amount of UDP packets dropped by kernel."
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by peely on 2010-10-27
I wonder is anyone can help me?

We are running VoIP services using Freeswitch on Ubuntu 10.04 server x64. Each server is not particularly busy (~25 concurrent session at peak) and in most scenarios we don't even process media, so we can assume only around 7 calls on each server is processing media. Thus, each server's NIC is utilised very little.

Our servers use RTP over UDP to carry media and we are experiencing something in the order of 10-15% packet loss on calls when any number of calls are in progress, say over 5 calls. For the life of me I can't figure out why we are losing so many UDP packets.

So far I have tried all combinations of:

Disabling IPV6 and checking it's disabled in /proc/sys/net/ipv6/conf/all/disable_ipv6
Increasing UDP receive buffers, anything from 8MB to 64MB!
Disabling all offloading using ethtool

In all scenarios, a netstat -su shows a rapidly increasing number of packet receive errors and RcvBufErrors (both values always identical).

Servers are HP DL/360g5 with dual quad-core processors and 4gb RAM, neither CPU or RAM show any signs of stress whatsoever.

I'm kind of tearing my hair out now, I've ran VoIP services on other distros without any such problems previously, could somebody please give me any clues as to what it could be that's causing packets to be dropped by the kernel? Does anyone know how I can get the kernel to perhaps log dropped packets to syslog with a valid reason?

TCP seems fine, I can transfer reasonably large files without a problem.


Thanks in advance,




Neil.

---

### Post by relay_man on 2010-10-30
I'm no authority on your problem, but I did a little searching
and I found this.

[http://www.29west.com/docs/THPM/udp-buffer-sizing.html](http://www.29west.com/docs/THPM/udp-buffer-sizing.html)

hope this may be of some help.

---

