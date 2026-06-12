---
title: "Trouble setting up a persistent PPTP connection"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by giovannizero on 2013-05-21
I'm trying to configure a persistent PPTP interface in Ubuntu server and don't seem to be able to use the interface. The client is connecting to the server and getting an ipaddress but if I try to ping using the interface it fails, similarly, trying to curl using the interface doesn't work. Any ideas?

ifconfig output:
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 8c:89:a5:8e:7a:a0  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8e89:a5ff:fe8e:7aa0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:451346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:776172 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:61599369 (61.5 MB)  TX bytes:927422749 (927.4 MB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10060434 (10.0 MB)  TX bytes:10060434 (10.0 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.100.0.2  P-t-P:10.100.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:672 (672.0 B)  TX bytes:690 (690.0 B)
```

Routing info
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
10.100.0.1      0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
74.221.214.106  192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
```

Trying to ping with the ppp0 interface
```
$ ping -I ppp0 -c 4 google.com
PING google.com (74.125.225.200) from 192.168.1.120 ppp0: 56(84) bytes of data.

--- google.com ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3024ms
```

Trying to ping with ppp0 IP address
```
$ ping -I 10.100.0.2 -c 4 google.com
PING google.com (74.125.225.194) from 10.100.0.2 : 56(84) bytes of data.

--- google.com ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3024ms

```

Trying to curl
```
$ curl --interface eth0 google.com
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="http://www.google.com/">here</A>.
</BODY></HTML>
$ curl --interface ppp0 google.com

curl: (45) Couldn't bind to 'ppp0'
```


(This was originally posted in specialized support but I didn't get any responses over there)

---

### Post by giovannizero on 2013-05-22
It looks like I was just missing the routes needed to make the interface works. I followed this post to fix it: [http://serverfault.com/questions/228195/answering-on-the-same-interface-where-the-request-came-from](http://serverfault.com/questions/228195/answering-on-the-same-interface-where-the-request-came-from)

---

