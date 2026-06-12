---
title: "vpn not connecting to all subnets"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by aaronp on 2010-01-30
Hi all,

I use vpnc to connect to my work Cisco VPN.

It has worked fine in the past but we had a power outage yesterday while it was connected and after turning the PC back on and trying to run it again I got an error: ```
resolvconf: Error: /etc/resolv.conf must be a symlink
```

I found how to fix this and was able to make it go away. However, now when I connect to VPN (always successfully getting the VPN welcome message) I can only connect to certain machines on the network.

I'm figuring it may be only connecting to certain subnets but have no idea how to find out if this is the case let alone how to fix it.

I can ping the 'inaccessible' machines and it resolves the IP address of that machine in the ping request but after a few seconds it comes back as host unreachable.
Other machines I can ping and get a response asap as per normal.

Here are my attempts to ping, firstly my own machine (I was in the office using it today so I know it is working) then another machine, using the hostname and then a server that I know the direct IP address of.

Note, the second one is a bit misleading, the ping response times seem ok but they are actually taking up to 2 seconds each to arrive on my terminal output, even if the ping is only taking ~ 60ms.

```

VPNC started in background (pid: 7632)...
aaron@apbh:~$ ping aas022313
PING aas022313.aas.priv (172.20.121.90) 56(84) bytes of data.
From 172.16.102.137 icmp_seq=2 Destination Host Unreachable
From 172.16.102.137 icmp_seq=3 Destination Host Unreachable
^CFrom 172.16.102.137 icmp_seq=4 Destination Host Unreachable

--- aas022313.aas.priv ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 11216ms

aaron@apbh:~$ ping aas01132
PING aas01132.aas.priv (172.20.121.34) 56(84) bytes of data.
64 bytes from 172.20.121.34: icmp_seq=1 ttl=123 time=58.3 ms
64 bytes from 172.20.121.34: icmp_seq=2 ttl=123 time=57.6 ms
64 bytes from 172.20.121.34: icmp_seq=3 ttl=123 time=58.3 ms
64 bytes from 172.20.121.34: icmp_seq=4 ttl=123 time=59.9 ms
^C64 bytes from 172.20.121.34: icmp_seq=5 ttl=123 time=57.8 ms

--- aas01132.aas.priv ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 20578ms
rtt min/avg/max/mdev = 57.618/58.419/59.942/0.832 ms
aaron@apbh:~$ ping 172.16.16.50
PING 172.16.16.50 (172.16.16.50) 56(84) bytes of data.
64 bytes from 172.16.16.50: icmp_seq=1 ttl=59 time=85.6 ms
64 bytes from 172.16.16.50: icmp_seq=2 ttl=59 time=71.1 ms
64 bytes from 172.16.16.50: icmp_seq=3 ttl=59 time=61.0 ms
64 bytes from 172.16.16.50: icmp_seq=4 ttl=59 time=60.0 ms
64 bytes from 172.16.16.50: icmp_seq=5 ttl=59 time=59.2 ms
64 bytes from 172.16.16.50: icmp_seq=6 ttl=59 time=68.0 ms
64 bytes from 172.16.16.50: icmp_seq=7 ttl=59 time=60.4 ms
^C
--- 172.16.16.50 ping statistics ---
8 packets transmitted, 7 received, 12% packet loss, time 7008ms
rtt min/avg/max/mdev = 59.206/66.517/85.627/8.866 ms



```

Any ideas on how to track down the problem?

thanks
Aaron

---

