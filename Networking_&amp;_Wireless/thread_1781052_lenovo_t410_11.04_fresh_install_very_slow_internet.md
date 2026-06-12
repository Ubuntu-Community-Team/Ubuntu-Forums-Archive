---
title: "lenovo t410 11.04 fresh install very slow internet connection"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by dohomi on 2011-06-12
Hello,

I'm a newbie and try to switch from Win7 to Ubuntu 11.04 with unity desktop.

My internet connection is slower than hell, and I dont know how to fix it. I tried with disable Ipv6 but it doesnt make any difference. Not sure if its disabled proper because if i do 

ip a | grep inet:
```

   inet 127.0.0.1/8 scope host lo
   inet 192.168.1.11/24 brd 192.168.1.255 scope global eth0

```

This is the output of
sysctl -p
```

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

This is my ping [www.google.com](www.google.com)
```

PING www.l.google.com (74.125.235.52) 56(84) bytes of data.
64 bytes from 74.125.235.52: icmp_req=1 ttl=56 time=85.2 ms
64 bytes from 74.125.235.52: icmp_req=2 ttl=56 time=88.5 ms

--- www.l.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 10150ms
rtt min/avg/max/mdev = 85.251/86.897/88.544/1.672 ms

```

Im sure that maybe something in the DNS configuration is wrong, but I dont know where to start. But with this slow internet its even hard to google...

Thanks for any help
Domi

---

### Post by dohomi on 2011-06-12
If I boot with Win 7 my ping result of google.com is for 4 packets only 93 ms! Where could be my misconfiguration? Thanks again

---

