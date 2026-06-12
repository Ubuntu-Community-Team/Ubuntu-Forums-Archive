---
title: "Host and ping command not working"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by viterminator on 2010-02-27
Hi,
I am working behind a http proxy (172.30.x.x:3128). I have configured it in my terminal. All the applications such as wget,lynx firefox etc. are working correctly.However all dns utilities like nslookup, host and even ping too are not working.Following is output of host command:
```
root@ding:~# host google.com
;; connection timed out; no servers could be reached
```
Output of host -T:
```
root@ding:~# host -T google.com
;; Connection to 4.2.2.2#53(4.2.2.2) for google.com failed: connection refused.
```
similarly for nslookup:
```
root@ding:~# host google.com
;; connection timed out; no servers could be reached

```

ping doesn't give any output at all just hangs there.

Contents of my resolv.conf:
```
nameserver 4.2.2.2
```
my ifconfig eth0:
```
eth0      Link encap:Ethernet  HWaddr 00:22:19:e4:2f:dd
          inet addr:172.30.104.174  Bcast:172.30.105.255  Mask:255.255.254.0
          inet6 addr: fe80::222:19ff:fee4:2fdd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3651099 (3.6 MB)  TX bytes:261345 (261.3 KB)
          Interrupt:19 Base address:0x4000
```
my uname-a:
```
Linux ding 2.6.30.9 #1 SMP Tue Dec 1 21:51:08 EST 2009 i686 GNU/Linux
```
Using Ubuntu 8.10
To connect to net I have to first run dhclient3(learnt from this forum!).It gives me my ip but where is dns address sent I don't have and idea. Kindly do help me about as I am learning about these stuff and doesnot have clear idea how all that dns etc. works.
Thanks in advance

---

