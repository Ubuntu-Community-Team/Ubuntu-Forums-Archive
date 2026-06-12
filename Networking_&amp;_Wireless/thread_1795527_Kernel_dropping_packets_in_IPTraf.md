---
title: "Kernel dropping packets in IPTraf"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by Daniel T1 on 2011-07-02
Hi there, 

I was wondering if anybody has used IPTraf recently in heavily used FastEthernet interfaces.

I am using IPTraf to log the traffic details (Protocol, IP addresses and packet size) of an interface. To my surprise the file analysis revealed that large chunks of data were missing as the results were compared  with those of other tools (MRTG, RRDTool and TCPDump raw files).

Has anybody come across this problem before? Does IPTraf allow to store "raw" files just like TCPDump does? This prevented the kernel from dropping any packets but for a number of reasons I would like to stick to IPTraf instead.

Thanks!

Daniel

---

### Post by poolet on 2011-07-03
tcpdump can't keep up with the packets packet "dropped by kernel'' this is the number
of packets that were dropped, due a lack of buffer space, by the packet capture mechanism in
the OS on which tcpdump is running, if the OS reports that information to applications
if not,it wil be reported as 0......Also check your firewall....

---

