---
title: "Need help with a Broadcom BCM4311 on 10.04"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by Clom on 2010-09-12
Hey guys,

I'm running a live usb of 10.04 on my laptop, and I've got a somewhat bizarre  problem. I can connect to my router (I get given an IP and can connect to the router homepage if I want) but can't connect to the internet. Not by wireless, not when directly plugged in. My Xbox can connect through the wireless, no problems, and my PC works when plugged directly in, so I know the problem isn't on the router end.

Anybody have an idea on how to fix this? I suspect there's a quite simple answer that's going to make me look rather stupid, but for the life of me I can't figure it out.

Much appreciate any help on this!

Clom.

---

### Post by DirtDart on 2010-09-17
If you try to ping [www.yahoo.com](www.yahoo.com), does it resolve to an IP address and if so, does it respond?

Sounds like a routing issue.  What does your routing table look like?  Type **route** in the console to display your routing table.

---

### Post by Clom on 2010-09-18
Cheers for the reply!):P

When I try to ping yahoo, I just get an "unknown host" error. The following is the dialogue I get when I first ping myself, then the router, then a yahoo IP and finally [www.yahoo.com](www.yahoo.com)


ubuntu@ubuntu:~$ ping -c3 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_seq=1 ttl=64 time=0.061 ms
64 bytes from 192.168.1.3: icmp_seq=2 ttl=64 time=0.063 ms
64 bytes from 192.168.1.3: icmp_seq=3 ttl=64 time=0.062 ms

--- 192.168.1.3 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.061/0.062/0.063/0.000 ms

ubuntu@ubuntu:~$ ping -c3 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=254 time=6.47 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=254 time=4.46 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=254 time=4.47 ms

--- 192.168.1.254 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 4.463/5.139/6.479/0.949 ms

ubuntu@ubuntu:~$ ping -c3 87.248.122.122
PING 87.248.122.122 (87.248.122.122) 56(84) bytes of data.
From 192.168.1.3 icmp_seq=1 Destination Host Unreachable
From 192.168.1.3 icmp_seq=2 Destination Host Unreachable
From 192.168.1.3 icmp_seq=3 Destination Host Unreachable

--- 87.248.122.122 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2014ms
, pipe 3
ubuntu@ubuntu:~$ ping -c3 [www.yahoo.com](www.yahoo.com)
ping: unknown host [www.yahoo.com](www.yahoo.com)


As you can see, I can ping my router no problems, but when I try and go anywhere outside the local network and it's fail fail fail.:(

Here's the routing table.

ubuntu@ubuntu:~$ route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth1
ubuntu@ubuntu:~$ 

Any ideas?

I should also mention that I'm running a proprietary drivers on a liveusb with 2Gigs of persistence storage... It's not exactly the ideal situation to be running Ubuntu on, but goddamn it, I'd just love not to have to take the twenty-five minute walk to university every time I want to check my email!

---

### Post by DirtDart on 2010-09-18
> ping -c3 [www.yahoo.com](www.yahoo.com)
ping: unknown host [www.yahoo.com](www.yahoo.com)

Your DNS setting isn't configured or configured correctly.

In your */etc/resolv.conf* check the **nameserver** line if it exists.  This should point to either your router, if it does DNSMasq (mine does), or your ISP's DNS server.

My */etc/resolv.conf*

```
nameserver 192.168.1.1
```

---

