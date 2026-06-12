---
title: "Network hanging in weird places"
date: 2012-11-09
forum: Networking &amp; Wireless
---

### Post by onetrickwolf on 2012-11-09
Edit: Solved by looking through this thread: [http://ubuntuforums.org/showthread.php?t=1376506&page=3](http://ubuntuforums.org/showthread.php?t=1376506&page=3)

Specifically this code did it:

```
sudo ifconfig eth0 mtu 1492
ifconfig | grep MTU
```


--Original Post--

(Somewhat of a new user sorry if I am dumb)

I'm using Ubuntu server 12.0.4.1 64-bit.

I have a headless server so I installed Ubuntu on another computer then deleted /etc/udev/rules.d/70-persistent-net.rules so it would be regenerated when I moved it.

It worked fine and I'm able to SSH into the headless server but for some reason various network connections are hanging indefinitely (I haven't seen one terminate yet but the longest I waited was about 10 minutes).

wget google.com works fine but here's one example that doesn't:

```
me@ubuntu:~$ wget u12.amahi.org/install-amahi
--2012-11-09 20:25:30--  http://u12.amahi.org/install-amahi
Resolving u12.amahi.org (u12.amahi.org)... 208.115.201.197
Connecting to u12.amahi.org (u12.amahi.org)|208.115.201.197|:80... connected.
HTTP request sent, awaiting response...

```

Also updates like this get stuck:

```
ubuntu:~$ sudo apt-get update
[sudo] password for brent:
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease
Ign http://us.archive.ubuntu.com precise-backports InRelease
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:2 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]
Ign http://security.ubuntu.com precise-security InRelease
Hit http://us.archive.ubuntu.com precise Release
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]
97% [Waiting for headers] [Waiting for headers] [Waiting for headers]
```

I'm pretty confused because most other network things I use are working (SSH and wget on pages like google).

If I plug my drive back into my other computer it works fine so I'm pretty sure it's not just the sites being down or something.

Any idea what's going on or how I could start debugging this?

---

### Post by onetrickwolf on 2012-11-09
Here's my ifconfig output (saw on another thread it might be useful for someone to help me):

```
me@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:87:51:aa
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe87:51aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:924 errors:81 dropped:0 overruns:0 frame:81
          TX packets:495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:82774 (82.7 KB)  TX bytes:74044 (74.0 KB)
          Interrupt:19 Base address:0xdead

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by onetrickwolf on 2012-11-09
More info:

```
**me@ubuntu:~$ ping 192.168.1.1 -c 1 -s 1400 -M do**
PING 192.168.1.1 (192.168.1.1) 1400(1428) bytes of data.
1408 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=0.939 ms

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.939/0.939/0.939/0.000 ms
**me@ubuntu:~$ ping 192.168.1.1 -c 1 -s 1501 -M do**
PING 192.168.1.1 (192.168.1.1) 1501(1529) bytes of data.
From 192.168.1.103 icmp_seq=1 Frag needed and DF set (mtu = 1500)

--- 192.168.1.1 ping statistics ---
0 packets transmitted, 0 received, +1 errors

**me@ubuntu:~$ ping localhos**t
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.052 ms
64 bytes from localhost (127.0.0.1): icmp_req=2 ttl=64 time=0.030 ms
64 bytes from localhost (127.0.0.1): icmp_req=3 ttl=64 time=0.026 ms
64 bytes from localhost (127.0.0.1): icmp_req=4 ttl=64 time=0.036 ms
64 bytes from localhost (127.0.0.1): icmp_req=5 ttl=64 time=0.027 ms
64 bytes from localhost (127.0.0.1): icmp_req=6 ttl=64 time=0.024 ms
64 bytes from localhost (127.0.0.1): icmp_req=7 ttl=64 time=0.026 ms
64 bytes from localhost (127.0.0.1): icmp_req=8 ttl=64 time=0.024 ms
64 bytes from localhost (127.0.0.1): icmp_req=9 ttl=64 time=0.025 ms
64 bytes from localhost (127.0.0.1): icmp_req=10 ttl=64 time=0.024 ms
64 bytes from localhost (127.0.0.1): icmp_req=11 ttl=64 time=0.024 ms
64 bytes from localhost (127.0.0.1): icmp_req=12 ttl=64 time=0.023 ms
64 bytes from localhost (127.0.0.1): icmp_req=13 ttl=64 time=0.024 ms
64 bytes from localhost (127.0.0.1): icmp_req=14 ttl=64 time=0.022 ms
64 bytes from localhost (127.0.0.1): icmp_req=15 ttl=64 time=0.027 ms
64 bytes from localhost (127.0.0.1): icmp_req=16 ttl=64 time=0.024 ms
^C
--- localhost ping statistics ---
16 packets transmitted, 16 received, 0% packet loss, time 14999ms
rtt min/avg/max/mdev = 0.022/0.027/0.052/0.008 ms

```

---

### Post by onetrickwolf on 2012-11-09
More info:

```
me@ubuntu:~$ ping www.cisco.com -c 1 -s 1472 -M do
PING e144.dscb.akamaiedge.net (23.10.64.170) 1472(1500) bytes of data.

--- e144.dscb.akamaiedge.net ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

```

Sorry for spamming replies I'm just reading other threads and it looks like these are what a lot of the experts ask people to run so I wanted to save you guys time.

---

