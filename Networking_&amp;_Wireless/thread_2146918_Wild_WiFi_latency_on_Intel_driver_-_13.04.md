---
title: "Wild WiFi latency on Intel driver - 13.04"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by mcdizzle on 2013-05-20
Hey Everyone

I'm getting high and inconsistent latency on WiFi connections... As a baseline I'm sitting next to the router, when I boot Windows and ping the router I get an average of 5ms. If I boot into Ubuntu 13.04 I get anything from 25ms up to 200ms and occasional lost packets...

My hardware is a relatively new Dell XPS 13 Ultrabook and the built-in WiFi device is an Intel one. My Ubuntu 13.04 is up to date and I'm just using the standard drivers provided by the Kernel/Ubuntu.

Any advice or tips for resolution would be so good!! :D

```
&#65279;C:\Users\andrew>ping 192.168.0.1 -t

Pinging 192.168.0.1 with 32 bytes of data:
Reply from 192.168.0.1: bytes=32 time=18ms TTL=64
Reply from 192.168.0.1: bytes=32 time=6ms TTL=64
Reply from 192.168.0.1: bytes=32 time=8ms TTL=64
Reply from 192.168.0.1: bytes=32 time=3ms TTL=64
Reply from 192.168.0.1: bytes=32 time=3ms TTL=64
Reply from 192.168.0.1: bytes=32 time=3ms TTL=64
Reply from 192.168.0.1: bytes=32 time=3ms TTL=64
Reply from 192.168.0.1: bytes=32 time=3ms TTL=64
Reply from 192.168.0.1: bytes=32 time=1ms TTL=64
Reply from 192.168.0.1: bytes=32 time=3ms TTL=64
Reply from 192.168.0.1: bytes=32 time=5ms TTL=64
Reply from 192.168.0.1: bytes=32 time=9ms TTL=64
Reply from 192.168.0.1: bytes=32 time=3ms TTL=64


Ping statistics for 192.168.0.1:
    Packets: Sent = 13, Received = 13, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 18ms, Average = 5ms
Control-C
^C

```
```

andrew@:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=89.6 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=109 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=29.9 ms
64 bytes from 192.168.0.1: icmp_req=4 ttl=64 time=52.4 ms
64 bytes from 192.168.0.1: icmp_req=5 ttl=64 time=75.4 ms
64 bytes from 192.168.0.1: icmp_req=6 ttl=64 time=98.3 ms
64 bytes from 192.168.0.1: icmp_req=7 ttl=64 time=19.1 ms
64 bytes from 192.168.0.1: icmp_req=8 ttl=64 time=42.1 ms
64 bytes from 192.168.0.1: icmp_req=9 ttl=64 time=65.2 ms
^C
```

---

### Post by praseodym on 2013-05-20
Deactivate the N-mode of the driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Check also:
```

ifconfig -a
```

---

### Post by mcdizzle on 2013-05-21
Thank you [COLOR=#000000]praseodym, though I found I had to run the following command to get the driver to remove correctly first:[/COLOR]

```
modprobe -rvf iwldvm
```

My latency is now a nice 2ms. :D

---

