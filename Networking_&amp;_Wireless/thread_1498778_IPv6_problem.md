---
title: "IPv6 problem?"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by djstava on 2010-06-01
Hi,I want to construct the ipv6 environment,but something strange happen to me.

```
djstava@Gateway:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:40:48:c3:05  
          inet addr:192.168.18.122  Bcast:192.168.18.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:40ff:fe48:c305/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11039 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7175307 (7.1 MB)  TX bytes:1784765 (1.7 MB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6197 (6.1 KB)  TX bytes:6197 (6.1 KB)
```Then I install the gw6c,sudo /etc/init.d/gw6c start,and everything works well.
```
djstava@Gateway:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:40:48:c3:05  
          inet addr:192.168.18.122  Bcast:192.168.18.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:40ff:fe48:c305/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7182407 (7.1 MB)  TX bytes:1787482 (1.7 MB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6197 (6.1 KB)  TX bytes:6197 (6.1 KB)

tun       Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet6 addr: 2406:a000:f0ff:fffe::1101/128 Scope:Global
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1280  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:272 (272.0 B)  TX bytes:0 (0.0 B)
```Now I'd like to connect another ipv6 lan by DHCP,but gw6c not work any more.And sudo /etc/init.d/gw6c start,nothing happened.Do I really need tunnel application like gw6c,miredo?
I hope you all can know what I mean,I don't really know ipv6,need your help.

---

