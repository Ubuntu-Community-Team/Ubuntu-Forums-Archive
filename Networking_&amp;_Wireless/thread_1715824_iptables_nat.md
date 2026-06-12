---
title: "iptables nat"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by Mrusful on 2011-03-27
Decided to teach ubuntu. As a result:
router:
```
dir320 = 192.168.0.1/24
```
Vbox = gw server = ubuntu 10.10:
```

eth0: 10.0.0.1/22 gw *
eth1: 192.168.0.107 gw *

```
#route
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth1
10.0.0.0        *               255.255.252.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         dir-320         0.0.0.0         UG    0      0        0 eth1

```

/etc/sysctl.conf --> net.ipv4.ip_forward=1 - unncomment
/proc/sys/net/ipv4/ip_forward - entered 1

```
#iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```
Policy all ACCEPT

VBox=XP
```

>ping ya.ru
Pinging ya.ru [93.158.134.3] with 5000 bytes of data:
Reply from 93.158.134.3: bytes = 5000 time = 12ms TTL = 58
Reply from 93.158.134.3: bytes = 5000 time = 13ms TTL = 58
Reply from 93.158.134.3: bytes = 5000 time = 13ms TTL = 58
Reply from 93.158.134.3: bytes = 5000 time = 14ms TTL = 58

Ping statistics for 93.158.134.3:
     Packets: Sent = 4, Received = 4, Lost = 0
     (0% loss)
Estimated round-trip time in milliseconds:
     Minimum = 12msek, Max = 14 ms, Average = 13 ms

```
tracert ya.ru
```
>tracert ya.ru

Tracing route to ya.ru [93.158.134.3]
with a maximum of 30 hops:

   1 <1 ms <1 ms <1 ms 10.0.0.1
   February 2 ms 2 ms 1 ms 192.168.8.1
   March 2 ms 5 ms 2 ms 212.34.35.5
   April 6 ms 5 ms 2 ms 10.0.76.225
   May 2 ms 2 ms 2 ms 10.0.4.65
   June 25 ms 3 ms 3 ms msk-ix-m10.yandex.net [193.232.246.93]
   7117 ms 4 ms 3 ms l3-s3500-marionetka.yandex.net [213.180.213.76]

   8 * * * timed request.
   September 4 ms 3 ms 4 ms www.yandex.ru [93.158.134.3]

Trace complete.
```

everything cool?
But!
```
>telnet ya.ru 80
Connecting to ya.ru. .. Could not open connection to the site on port 80: connection failed
```

tcpdump -i eth1 -n -nn -t port 80
```
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
IP 192.168.0.107.1093 > 77.88.21.3.80: Flags [S], seq 3780960087, win 64240, options [mss 1460,nop,nop,sackOK], length 0
IP 10.0.0.5.1093 > 77.88.21.3.80: Flags [S], seq 3780960087, win 64240, options [mss 1460,nop,nop,sackOK], length 0
IP 192.168.0.107.1093 > 77.88.21.3.80: Flags [S], seq 3780960087, win 64240, options [mss 1460,nop,nop,sackOK], length 0
IP 10.0.0.5.1093 > 77.88.21.3.80: Flags [S], seq 3780960087, win 64240, options [mss 1460,nop,nop,sackOK], length 0
IP 192.168.0.107.1093 > 77.88.21.3.80: Flags [S], seq 3780960087, win 64240, options [mss 1460,nop,nop,sackOK], length 0
IP 10.0.0.5.1093 > 77.88.21.3.80: Flags [S], seq 3780960087, win 64240, options [mss 1460,nop,nop,sackOK], length 0

```
ya.ru = 77.88.21.3
 I know nothing about the dump, but i think packets go in one direction only, the client waits for a response, but it does not come, the question is why?

---

