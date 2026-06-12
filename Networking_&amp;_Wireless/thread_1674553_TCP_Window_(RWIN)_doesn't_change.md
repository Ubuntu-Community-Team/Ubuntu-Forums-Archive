---
title: "TCP Window (RWIN) doesn't change"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by ma$$ter on 2011-01-24
hi
I've followed the tutorial at [http://www.santa-li.com/linuxonbb.html]("http://www.santa-li.com/linuxonbb.html") to update my **RWIN** parameter, but to my surprise nothing updated. Please help me to find out why.

My sysctl.conf looks like this:
```
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1
net.ipv4.tcp_syncookies=1
net.ipv4.ip_forward=1
net.ipv6.conf.all.forwarding=1
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_ignore_bogus_error_responses = 1
net.ipv4.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_redirects = 0
net.core.rmem_default = 524288
net.core.rmem_max = 1027840
net.core.wmem_default = 524288
net.core.wmem_max = 1027840
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1
net.ipv4.tcp_moderate_rcvbuf = 1
net.ipv4.tcp_no_metrics_save = 1

```

A TCP/IP analysis looks like this (see bad value not changed):

> « SpeedGuide.net TCP Analyzer Results » 
Tested on: 01.23.2011 18:12 
IP address: 141.85.xxx.xx 
Client OS: Linux Ubuntu 10.04

TCP options string: 020405b40101040201030307 
MSS: 1460 
MTU: 1500 
TCP Window: **[COLOR="Red"]5888[/COLOR]** (NOT multiple of MSS) 
RWIN Scaling: 7 bits (2^7=128) 
Unscaled RWIN : 46 
Recommended RWINs: 64240, 128480, 256960, 513920, 1027840 
BDP limit (200ms): 236kbps (29KBytes/s)
BDP limit (500ms): 94kbps (12KBytes/s) 
MTU Discovery: ON 
TTL: 47 
Timestamps: OFF 
SACKs: ON 
IP ToS: 00000000 (0) 


---

### Post by ma$$ter on 2011-01-24
some 2 years ago, a similar question remained unanswered.
is it a tough question or what ?

---

### Post by KirbySmith on 2011-05-28
I think the answer is in the Santa-Li fine print.  Speedguide.net reports the first value of a dynamically increasing RWIN.

kirby

---

