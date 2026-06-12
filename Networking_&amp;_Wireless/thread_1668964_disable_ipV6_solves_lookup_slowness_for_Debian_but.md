---
title: "disable ipV6 solves lookup slowness for Debian but not for Ubuntu"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by zhangweiwu on 2011-01-17
Hello. My office have a slow-DNS-look-up issue that seems to be caused by incompatibility between Linux's IPv6 and ISP's network. The behavior, is dns look-up takes more than 5 seconds (sometimes 30 seconds) instead of usual 1 second.

The problem can be solved on Debian by disabling IPv6 on Debian hosts, but on Ubuntu 10.10 disabling IPv6 doesn't solve the problem. Why and how to go on?

Case on Debian:

Before disabling IPv6, the difference between -t A query and normal query is very big, normal queries take too long time (5 seconds), and browsing the Internet is hard life.

```

root@houyhnhnms:~# time host -t A g.cn
g.cn has address 203.208.37.99
g.cn has address 203.208.37.104

real	0m0.269s
user	0m0.024s
sys	0m0.028s
root@houyhnhnms:~# time host g.cn
g.cn has address 203.208.37.99
g.cn has address 203.208.37.104
g.cn has address 203.208.37.99
g.cn has address 203.208.37.104
g.cn mail is handled by 10 google.com.s9b1.psmtp.com.
g.cn mail is handled by 10 google.com.s9a1.psmtp.com.
g.cn mail is handled by 10 google.com.s9b2.psmtp.com.
g.cn mail is handled by 10 google.com.s9a2.psmtp.com.

real	0m5.139s
user	0m0.032s
sys	0m0.012s

```

Disable on Debian:

```

root@houyhnhnms:~# sysctl net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.all.disable_ipv6 = 1
root@houyhnhnms:~# sysctl net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6 = 1
root@houyhnhnms:~# sysctl net.ipv6.conf.lo.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6 = 1
root@houyhnhnms:~# sysctl net.ipv6.conf.eth0.disable_ipv6=1
net.ipv6.conf.eth0.disable_ipv6 = 1

```

After disabling, the difference between -t A query and normal query is very small.

```

root@houyhnhnms:~# time host -t A g.cn
g.cn has address 203.208.37.104
g.cn has address 203.208.37.99

real	0m0.050s
user	0m0.024s
sys	0m0.020s
root@houyhnhnms:~# time host g.cn
g.cn has address 203.208.37.104
g.cn has address 203.208.37.99
g.cn has address 203.208.37.104
g.cn has address 203.208.37.99
g.cn mail is handled by 10 google.com.s9b1.psmtp.com.
g.cn mail is handled by 10 google.com.s9a1.psmtp.com.
g.cn mail is handled by 10 google.com.s9b2.psmtp.com.
g.cn mail is handled by 10 google.com.s9a2.psmtp.com.

real	0m0.093s
user	0m0.032s
sys	0m0.004s

```

Do the same thing on Ubuntu 10.10

```

root@orphalese:~# sysctl net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.all.disable_ipv6 = 1
root@orphalese:~# sysctl net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6 = 1
root@orphalese:~# sysctl net.ipv6.conf.lo.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6 = 1
root@orphalese:~# sysctl net.ipv6.conf.eth0.disable_ipv6=1
net.ipv6.conf.eth0.disable_ipv6 = 1
root@orphalese:~# sysctl net.ipv6.conf.eth1.disable_ipv6=1
net.ipv6.conf.eth1.disable_ipv6 = 1
root@orphalese:~# time host -t A g.cn
g.cn has address 203.208.39.99
g.cn has address 203.208.39.104

real	0m0.014s
user	0m0.000s
sys	0m0.008s
root@orphalese:~# time host g.cn
g.cn has address 203.208.39.99
g.cn has address 203.208.39.104
;; Question section mismatch: got g.cn/A/IN
;; Question section mismatch: got g.cn/A/IN
;; connection timed out; no servers could be reached
g.cn mail is handled by 10 google.com.s9b1.psmtp.com.
g.cn mail is handled by 10 google.com.s9a1.psmtp.com.
g.cn mail is handled by 10 google.com.s9b2.psmtp.com.
g.cn mail is handled by 10 google.com.s9a2.psmtp.com.

real	0m10.064s
user	0m0.008s
sys	0m0.008s

```

In both case, the DNS setting of the two hosts (Debian/Ubuntu) is the same.

Any hint? Thanks in advance!

P.S. In order to prove I really managed to disable IPv6 on Ubuntu, here is the ifconfig output, which shows no IPv6 address after the disabling:

```

root@orphalese:~# /sbin/ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:00:f0:6e:e9:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:04:23:4d:0f:35  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6368608 (6.3 MB)  TX bytes:1503295 (1.5 MB)
          Interrupt:5 Base address:0xe000 Memory:c0000000-c0000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5771637 (5.7 MB)  TX bytes:5771637 (5.7 MB)

```

---

### Post by lemming465 on 2011-01-17
> sysctl net.ipv6.conf.all.disable_ipv6=1
disables ipv6 at the network layer.  However, you can make AAAA DNS queries over IPv4, too. Plain "host" these days will query for both IPv4 and IPv6 by default.  Modern applications are probably calling getaddrinfo(3) with the AF_UNSPEC argument that allows for either possibility, A or AAAA.  I'm not sure how to prevent this easily.

In order of ease, things you could try include:

(1) For firefox web browsing specifically, go into *about:config*, search on 'dns', and set network.dns.disableIPv6 to 'true'.

(2) Edit /etc/gai.conf and uncomment the block of lines at the bottom that say
> #scopev4 ::ffff:169.254.0.0/112  2
#scopev4 ::ffff:127.0.0.0/104    2
#scopev4 ::ffff:0.0.0.0/96       14

(3) add a file /etc/modprobe.d/no-v6.conf containing
> alias ipv6 off
alias net-pf-10 off
and reboot.

I know the firefox change works; I'm less sure how much gai.conf or blacklisting modules will affect you.

---

### Post by zhangweiwu on 2011-01-18
The Firefox method works instantly.

The other two method are tried strictly following given requirement and tested after reboot, change is minor enough to be non-conclusive. In short, they don't work.

---

