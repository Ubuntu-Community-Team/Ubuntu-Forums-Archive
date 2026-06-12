---
title: "Slow, Unreliable Wireless on HP Laptop"
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by Brad_J on 2012-02-22
Hi, I have an HP HDX-16 laptop and I'm running ubuntu 10.04 on it. Recently my internet has become very unreliable where after a couple minutes of connecting to wifi, my internet access will slow to a crawl or seem to completely stop. This can be remedied by disconnecting from wifi and reconnecting to the same SSID, but this will buy me a couple minutes at most before my internet access returns to being completely unusable.

When the slowdown happens the laptop is still connected to the network and there is still internet access, but it is so slow that most webpages will time out before anything loads. Below is the server response that I get after pinging google.ca for about 5 minutes.

```

brad@brad-laptop:~$ ping google.ca
PING google.ca (74.125.127.94) 56(84) bytes of data.
64 bytes from 74.125.127.94: icmp_seq=1 ttl=54 time=59.7 ms
64 bytes from 74.125.127.94: icmp_seq=24 ttl=54 time=227 ms
From brad-laptop.local (192.168.1.67) icmp_seq=26 Destination Host Unreachable
From brad-laptop.local (192.168.1.67) icmp_seq=27 Destination Host Unreachable
From brad-laptop.local (192.168.1.67) icmp_seq=28 Destination Host Unreachable
64 bytes from pz-in-f94.1e100.net (74.125.127.94): icmp_seq=29 ttl=54 time=24.4 ms
64 bytes from pz-in-f94.1e100.net (74.125.127.94): icmp_seq=30 ttl=54 time=23.0 ms
64 bytes from 74.125.127.94: icmp_seq=31 ttl=54 time=22.5 ms
From brad-laptop.local (192.168.1.67) icmp_seq=60 Destination Host Unreachable
From brad-laptop.local (192.168.1.67) icmp_seq=61 Destination Host Unreachable
From brad-laptop.local (192.168.1.67) icmp_seq=62 Destination Host Unreachable
64 bytes from pz-in-f94.1e100.net (74.125.127.94): icmp_seq=63 ttl=54 time=54.5 ms
64 bytes from pz-in-f94.1e100.net (74.125.127.94): icmp_seq=64 ttl=54 time=89.6 ms
64 bytes from 74.125.127.94: icmp_seq=65 ttl=54 time=52.0 ms
64 bytes from pz-in-f94.1e100.net (74.125.127.94): icmp_seq=66 ttl=54 time=267 ms
64 bytes from pz-in-f94.1e100.net (74.125.127.94): icmp_seq=67 ttl=54 time=21.6 ms
^C64 bytes from 74.125.127.94: icmp_seq=68 ttl=54 time=142 ms

--- google.ca ping statistics ---
68 packets transmitted, 11 received, +6 errors, 83% packet loss, time 303326ms
rtt min/avg/max/mdev = 21.696/89.532/267.040/82.369 ms, pipe 3

```

Let me know if there's anything that could even maybe be the cause of this and I will investigate. This is very frustrating and it is hindering my ability to get any work done on this laptop, I will post any further information as needed. Thanks.

-Brad

---

### Post by Brad_J on 2012-02-28
Bump...

---

