---
title: "b43 wireless latency problem on laptop when running on battery"
date: 2011-12-31
forum: Networking &amp; Wireless
---

### Post by joker99 on 2011-12-31
Hello, 

I noticed that my wireless driver (b43) works perfectly 
fine when I'm on AC. But when I plug the cable off and 
it starts running on battery, I immediately get pings
up to 2 seconds. This is how it looks like:

64 bytes from 192.168.0.1: icmp_req=21 ttl=64 time=1.32 ms
64 bytes from 192.168.0.1: icmp_req=22 ttl=64 time=1.31 ms
64 bytes from 192.168.0.1: icmp_req=23 ttl=64 time=3.23 ms
64 bytes from 192.168.0.1: icmp_req=24 ttl=64 time=1.27 ms
64 bytes from 192.168.0.1: icmp_req=25 ttl=64 time=1.30 ms
>>Plugged Off
64 bytes from 192.168.0.1: icmp_req=26 ttl=64 time=17.1 ms
64 bytes from 192.168.0.1: icmp_req=15 ttl=64 time=193 ms
64 bytes from 192.168.0.1: icmp_req=16 ttl=64 time=2056 ms
64 bytes from 192.168.0.1: icmp_req=17 ttl=64 time=1057 ms
64 bytes from 192.168.0.1: icmp_req=18 ttl=64 time=58.0 ms
64 bytes from 192.168.0.1: icmp_req=19 ttl=64 time=183 ms
64 bytes from 192.168.0.1: icmp_req=20 ttl=64 time=410 ms

It goes down to 1 ms after I plug the cable back. 

My config is like this:
XUbuntu 11.10 32 bit desktop
Kernel: 3.0.0-14-generic
b43 driver: proprietary (default from XUbuntu 11.10)

Do you know what could be a root cause for this?

---

### Post by joker99 on 2011-12-31
I saw that this problem doesn't happen on Ubuntu 11.04 with kernel
2.6.38-8-generic

Results from this system are slightly worse (3ms compared to 1.3 ms), but are constant no matter of AC/DC:

4 bytes from 192.168.0.1: icmp_req=9 ttl=64 time=2.79 ms
64 bytes from 192.168.0.1: icmp_req=10 ttl=64 time=2.78 ms
64 bytes from 192.168.0.1: icmp_req=11 ttl=64 time=3.32 ms
64 bytes from 192.168.0.1: icmp_req=12 ttl=64 time=5.02 ms
64 bytes from 192.168.0.1: icmp_req=13 ttl=64 time=2.58 ms
64 bytes from 192.168.0.1: icmp_req=14 ttl=64 time=3.84 ms
64 bytes from 192.168.0.1: icmp_req=15 ttl=64 time=3.37 ms
64 bytes from 192.168.0.1: icmp_req=16 ttl=64 time=2.66 ms
64 bytes from 192.168.0.1: icmp_req=17 ttl=64 time=3.21 ms
64 bytes from 192.168.0.1: icmp_req=18 ttl=64 time=3.53 ms
64 bytes from 192.168.0.1: icmp_req=19 ttl=64 time=3.46 ms
64 bytes from 192.168.0.1: icmp_req=20 ttl=64 time=3.53 ms
64 bytes from 192.168.0.1: icmp_req=21 ttl=64 time=2.90 ms

---

### Post by joker99 on 2011-12-31
I found that the cause of problem was wl kernel driver, which 
is shipped by default by Ubuntu. 

I installed b43 driver instead using:
sudo apt-get install firmware-b43-lpphy-installer

Then I did
sudo modprobe -r wl
sudo modprobe b43

and the problem disappeared.

---

