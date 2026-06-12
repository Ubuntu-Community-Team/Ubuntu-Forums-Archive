---
title: "Extremely slow WiFi in 9.10"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by thegodfaza on 2010-03-09
I just installed the latest version of Ubuntu [9.10] to give it another go. I was surprised to see my netword card supported right out of the box as well as ACPI in my laptop. My network card is the Atheros AR5007EG. While it does work, it has significant performance problems. I ran a speed test at [www.speakeasy.net/speedtest](www.speakeasy.net/speedtest). It took about 5 minutes to load the page on WiFi. Here are results on ethernet and WiFi.

[[IMG]http://img60.imageshack.us/img60/6049/88221364.th.png[/IMG]](http://img60.imageshack.us/img60/6049/88221364.png)
Ethernet

[[IMG]http://img60.imageshack.us/img60/466/56970473.th.png[/IMG]](http://img60.imageshack.us/img60/466/56970473.png)
WiFi

I'm about 10' from the AP and even my Palm Pre can load sites faster than my laptop. The hardware is fine as it was running Win7 perfectly before I installed 9.10 over it. Also here is a little ping test I did.

```
root@Apollo:/home/justin# ping www.google.com
PING www.l.google.com (74.125.95.99) 56(84) bytes of data.
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=1 ttl=48 time=5974 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=2 ttl=48 time=5073 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=3 ttl=48 time=4071 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=4 ttl=48 time=3265 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=5 ttl=48 time=2876 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=6 ttl=48 time=3825 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=7 ttl=48 time=238 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=8 ttl=48 time=260 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=9 ttl=48 time=692 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=10 ttl=48 time=752 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=11 ttl=48 time=138 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=12 ttl=48 time=465 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=13 ttl=48 time=183 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=14 ttl=48 time=1229 ms
^Z
[1]+  Stopped                 ping www.google.com
root@Apollo:/home/justin# ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=534 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=552 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=877 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=389 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=1128 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=1967 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=1068 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=375 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=234 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=64 time=319 ms
64 bytes from 192.168.0.1: icmp_seq=11 ttl=64 time=651 ms
^Z
[2]+  Stopped                 ping 192.168.0.1
```
192.168.0.1 is my router.

---

### Post by thegodfaza on 2010-03-10
BUMP

Also the problem persists whether I use the default ath5k/ath9k drivers, madwifi, or ndiswrapper. Again, the symptoms are an extremely slow connection, high packet loss, and variable latency between 60ms and 10000ms.

---

### Post by thegodfaza on 2010-03-12
No one has any ideas as to what could be causing this issue. I would really love to use Ubuntu but basic reliable WiFi is a must.

---

### Post by kyletstrand on 2010-03-12
> **thegodfaza said:**
> 

```
root@Apollo:/home/justin# ping www.google.com
PING www.l.google.com (74.125.95.99) 56(84) bytes of data.
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=1 ttl=48 time=5974 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=2 ttl=48 time=5073 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=3 ttl=48 time=4071 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=4 ttl=48 time=3265 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=5 ttl=48 time=2876 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=6 ttl=48 time=3825 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=7 ttl=48 time=238 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=8 ttl=48 time=260 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=9 ttl=48 time=692 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=10 ttl=48 time=752 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=11 ttl=48 time=138 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=12 ttl=48 time=465 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=13 ttl=48 time=183 ms
64 bytes from iw-in-f99.1e100.net (74.125.95.99): icmp_seq=14 ttl=48 time=1229 ms
^Z
[1]+  Stopped                 ping www.google.com

```

Is this your ethernet connection's ping results?  The ping responses are very sporadic.  Does your connection speed fluctuate a lot with both wireless and ethernet?

---

### Post by thegodfaza on 2010-03-12
I figured out the problem. The ath5k driver wasn't fully compatible with my hardware and the other pre-installed drivers and the ones I installed caused more problem. I blacklisted all wifi drivers and am using ndiswrapper. There was an issue with ndiswrapper where if I didn't unload the module before I shutdown / rebooted, my bios would freeze next post cycle. I fixed that by unloading the module automatically in the Runlevel 0 and 6 scripts.

I am having another issue now. I have a Windows Home Server where I store all my media / files. I can't access it by the network browser or by it's computer name. I have to do a "Connect to Server" and use the servers IP address.

---

