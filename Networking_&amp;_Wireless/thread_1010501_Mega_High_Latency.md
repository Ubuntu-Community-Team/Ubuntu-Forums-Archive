---
title: "Mega High Latency"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by dazman19 on 2008-12-13
Hi, 

I am running 8.04 LTS on my notebook. Kernel 2.6.24-19-386 and for some unknown reason the latency is pretty high. 

Its a pretty decent notebook to run ubuntu, 1.5gb ram and dual core intel centrino duo processor with a gigabit network adapter. 

I have 3 machines on my home network, the notebook, a Gaming Vista PC and another windows machine. All of these machines can ping my router and any other machine on the network in under a millisecond. But for some reason for my ubuntu notebook takes between 300ms and 1200ms to respond. And occasionally loses packets. 

From the linux machine to the router.

daz@daz-laptop:~$ ping 192.168.1.10
PING 192.168.1.10 (192.168.1.10) 56(84) bytes of data.
64 bytes from 192.168.1.10: icmp_seq=1 ttl=64 time=162 ms
64 bytes from 192.168.1.10: icmp_seq=2 ttl=64 time=899 ms
64 bytes from 192.168.1.10: icmp_seq=3 ttl=64 time=1000 ms
64 bytes from 192.168.1.10: icmp_seq=4 ttl=64 time=0.964 ms
64 bytes from 192.168.1.10: icmp_seq=5 ttl=64 time=1000 ms
64 bytes from 192.168.1.10: icmp_seq=6 ttl=64 time=1.71 ms
64 bytes from 192.168.1.10: icmp_seq=7 ttl=64 time=1.10 ms
64 bytes from 192.168.1.10: icmp_seq=8 ttl=64 time=900 ms

From the windows machine to the linux machine 

Microsoft Windows [Version 6.0.6001]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.
C:\Users\daz>ping 192.168.1.14
Pinging 192.168.1.14 with 32 bytes of data:
Reply from 192.168.1.14: bytes=32 time=339ms TTL=64
Reply from 192.168.1.14: bytes=32 time=1338ms TTL=64
Reply from 192.168.1.14: bytes=32 time<1ms TTL=64
Reply from 192.168.1.14: bytes=32 time=999ms TTL=64
Ping statistics for 192.168.1.14:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 1338ms, Average = 669ms

From the windows machine to the router.

C:\Users\daz>ping 192.168.1.10
Pinging 192.168.1.10 with 32 bytes of data:
Reply from 192.168.1.10: bytes=32 time=1ms TTL=64
Reply from 192.168.1.10: bytes=32 time<1ms TTL=64
Reply from 192.168.1.10: bytes=32 time<1ms TTL=64
Reply from 192.168.1.10: bytes=32 time<1ms TTL=64
Ping statistics for 192.168.1.10:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 1ms, Average = 0ms

Edit: these were the only two machines switched on at the time I ran these tests. there should have been no network activity. The network speed is 100mbps, but i tried it with a 1000mbit switch and it did the same thing so i am assuming its something wrong with the ubuntu machine.

The throughput on the downloads off the net for the linux machine is still ok, but if i want to VNC or SSH to the notebook it goes really laggy, even typing in putty it takes a while for the text to come up and Man pages to display due to the latency.

I am thinking this could be a driver issue or something any ideas? I used to run 6.06 and it worked sweet, so it may be my hardwares compatability with the version of ubuntu. 

Let me know if you have any ideas.
Cheers
Daz

---

### Post by lensman3 on 2008-12-13
See if IP6 is running on the Linux.  I understand this can slow packets down alot.  "/sbin/ifconfig" should tell you if it is  on.  Turn it off it is.

Sorry fishing for an answer too!!!

---

