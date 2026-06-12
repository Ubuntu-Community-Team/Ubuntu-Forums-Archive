---
title: "Network not working properely!!"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by cmacia06 on 2013-04-25
I had it working but im not sure what went wrong.

I have my cable modem connect to my server through usb, then the server forwards to the wireless router.
The internet works on the server but not on the router (The router is not the issue). Im guessing it has something to do with nat.. here is my information.

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:30:67:41:0c:3a  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:67ff:fe41:c3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:677 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75977 (75.9 KB)  TX bytes:67910 (67.9 KB)

eth1      Link encap:Ethernet  HWaddr 00:14:04:e7:24:b7  
          inet addr:72.191.165.30  Bcast:255.255.255.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:37 errors:4 dropped:1 overruns:0 frame:4
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4032 (4.0 KB)  TX bytes:2124 (2.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10844 (10.8 KB)  TX bytes:10844 (10.8 KB)
```

eth0 internal network
eth1 external network

iptables -L
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere             LOG level warning

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


```

The strange this is that if i pung, traceroute, or dig, they all work on a client computer but webpages do not show up
I connected it directly to my xbox as well and the xbox claims its an mtu error, which i doubt.

---

### Post by cmacia06 on 2013-04-25
I connected my phones connection through a usb tether application and then configured the server to use that connection instead and it works. That connection is labled as usb0. Is there a way i can see what is going on with this? Everything looks like it is the same.

---

