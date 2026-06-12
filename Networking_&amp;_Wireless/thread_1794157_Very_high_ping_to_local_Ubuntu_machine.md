---
title: "Very high ping to local Ubuntu machine"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by NLight on 2011-06-30
I have a machine on my local network running Ubuntu that I use for web development. I've recently set it up and I'm trying to get rid of a few teething problems. One of them is that when I connect in any way to the server from my laptop I experience huge amounts of lag. SSH is almost unusable. Both the laptop and the server are connected to the network wirelessly.

Here's a a couple of pings from my laptop to the server:

> mac:~ Ben$ ping linux
PING linux.home (192.168.1.66): 56 data bytes
64 bytes from 192.168.1.66: icmp_seq=0 ttl=64 time=154.057 ms
64 bytes from 192.168.1.66: icmp_seq=1 ttl=64 time=177.475 ms
64 bytes from 192.168.1.66: icmp_seq=2 ttl=64 time=99.184 ms
Request timeout for icmp_seq 3
64 bytes from 192.168.1.66: icmp_seq=4 ttl=64 time=4.488 ms
64 bytes from 192.168.1.66: icmp_seq=5 ttl=64 time=74.229 ms
64 bytes from 192.168.1.66: icmp_seq=6 ttl=64 time=5.018 ms
64 bytes from 192.168.1.66: icmp_seq=7 ttl=64 time=115.557 ms
64 bytes from 192.168.1.66: icmp_seq=8 ttl=64 time=6.388 ms
64 bytes from 192.168.1.66: icmp_seq=9 ttl=64 time=61.661 ms
64 bytes from 192.168.1.66: icmp_seq=10 ttl=64 time=14.681 ms
64 bytes from 192.168.1.66: icmp_seq=11 ttl=64 time=509.364 ms
^C
--- linux.home ping statistics ---
13 packets transmitted, 11 packets received, 15.4% packet loss
round-trip min/avg/max/stddev = 4.488/111.100/509.364/138.732 ms
mac:~ Ben$ 


It's odd that on some of them, the ping is a decent speed, or at least reasonable for a wireless network. I first thought there may have been a problem with my wireless adapter my server uses (Belkin Wireless G) but if I SSH into the machine and ping my router, the speeds are much better, although they still vary quite a lot.

> ben@linux:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_req=1 ttl=64 time=1.22 ms
64 bytes from 192.168.1.254: icmp_req=2 ttl=64 time=11.5 ms
64 bytes from 192.168.1.254: icmp_req=3 ttl=64 time=0.963 ms
64 bytes from 192.168.1.254: icmp_req=4 ttl=64 time=11.6 ms
64 bytes from 192.168.1.254: icmp_req=5 ttl=64 time=77.0 ms
64 bytes from 192.168.1.254: icmp_req=6 ttl=64 time=86.5 ms
64 bytes from 192.168.1.254: icmp_req=7 ttl=64 time=1.40 ms
64 bytes from 192.168.1.254: icmp_req=8 ttl=64 time=11.3 ms
64 bytes from 192.168.1.254: icmp_req=9 ttl=64 time=1.19 ms
64 bytes from 192.168.1.254: icmp_req=10 ttl=64 time=12.9 ms
64 bytes from 192.168.1.254: icmp_req=11 ttl=64 time=11.5 ms
64 bytes from 192.168.1.254: icmp_req=12 ttl=64 time=0.958 ms
64 bytes from 192.168.1.254: icmp_req=13 ttl=64 time=11.9 ms
64 bytes from 192.168.1.254: icmp_req=14 ttl=64 time=1.08 ms
64 bytes from 192.168.1.254: icmp_req=15 ttl=64 time=1.58 ms
64 bytes from 192.168.1.254: icmp_req=16 ttl=64 time=11.8 ms
64 bytes from 192.168.1.254: icmp_req=17 ttl=64 time=11.7 ms
64 bytes from 192.168.1.254: icmp_req=18 ttl=64 time=11.5 ms
64 bytes from 192.168.1.254: icmp_req=19 ttl=64 time=11.7 ms
64 bytes from 192.168.1.254: icmp_req=20 ttl=64 time=11.4 ms
^C
--- 192.168.1.254 ping statistics ---
20 packets transmitted, 20 received, 0% packet loss, time 19024ms
rtt min/avg/max/mdev = 0.958/15.074/86.526/22.827 ms
ben@linux:~$ 


I don't think there's a problem with the router as when I ping another computer in my house from my laptop, the speed is fine (averaging 5ms, which I guess isn't bad over wireless). Furthermore when I ping google from the server the speed seems fine:

> ben@linux:~$ ping google.com
PING google.com (209.85.146.147) 56(84) bytes of data.
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=1 ttl=49 time=36.1 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=2 ttl=49 time=47.3 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=3 ttl=49 time=35.9 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=4 ttl=49 time=44.2 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=5 ttl=49 time=46.2 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=6 ttl=49 time=44.8 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=7 ttl=49 time=45.4 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=8 ttl=49 time=34.7 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=9 ttl=49 time=34.6 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=10 ttl=49 time=34.3 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=11 ttl=49 time=45.1 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=12 ttl=49 time=44.8 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=13 ttl=49 time=45.4 ms
64 bytes from bru01s01-in-f147.1e100.net (209.85.146.147): icmp_req=14 ttl=49 time=45.3 ms
^C
--- google.com ping statistics ---
14 packets transmitted, 14 received, 0% packet loss, time 13005ms
rtt min/avg/max/mdev = 34.355/41.773/47.322/4.988 ms

If anyone has any ideas I'd really appreciate it. It's quite hard to work with such a slow connection.

---

