---
title: "Weird network problem with ubuntu only"
date: 2012-11-17
forum: Networking &amp; Wireless
---

### Post by rklauco on 2012-11-17
I am running out of ideas here.

I run small home server using ubuntu and dnsmasq.
Everything worked fine until few days ago, when I noticed I am unable to ssh/ping other ubuntu machine on my private lan.
To explain:
[LIST]
[*]all clients have correct static or dynamic address delivered using DHCP
[*]all DNS requests are resolved properly, returning IPv4 addresses as expected
[*]all network clients are able to access internet
[*]all network clients are able to access the server
[*]all non-ubuntu network clients can be pinged, accessed using ssh/http and so on (openWRT, debian)
[*][COLOR="Red"]ubuntu clients cannot access other ubuntu clients with the exception of the server[/COLOR]
[/LIST]

Example:
[LIST]
[*]server IP 192.168.1.1, client1 IP 192.168.1.2 (ubuntu), client2 IP 192.168.1.3 (ubuntu), client3 192.168.1.4(openwrt)
[*]on server, ping client1 works fine, ping client2 works fine
[*][COLOR="red"]on client1, ping 192.168.1.1 works fine, ping 192.168.1.3 ends up with "destination host unreachable"[/COLOR]
[*][COLOR="Red"]on client2, ping 192.168.1.2 ends up with "destination host unreachable"[/COLOR]
[*]on client1, ping 192.168.1.4 works fine
[*]on client3, ping 192.168.1.2 or 192.168.1.3 works fine
[/LIST]

I thought it has something to do with IPv6, but disabling it did not help.
Also, I am trying to ping/ssh using IPv4 address and hostname with no success here.
Please, advice what should I look into next.

---

### Post by papibe on 2012-11-17
Hi rklauco.

Could you explain a little bit the 'topology' of your network? That is, how the devices are connected to each other?

Could you also post these commands from both the server and client1?
```
ifconfig

route -n
```
Regards.

---

### Post by rklauco on 2012-11-18
Ifconfig from one of the clients:
```
eth0      Link encap:Ethernet  HWaddr 64:31:50:8b:7f:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:467208 (467.2 KB)  TX bytes:467208 (467.2 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.233.1  Bcast:172.16.233.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.82.1  Bcast:192.168.82.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr ac:81:12:59:7f:92  
          inet addr:192.168.10.12  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55490693 (55.4 MB)  TX bytes:10357342 (10.3 MB)

```

route -n from the same client:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
172.16.233.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.10.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.82.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8

```

The same from server - ifconfig first:
```
eth0      Link encap:Ethernet  HWaddr 00:1d:60:08:ab:66  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5097848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8577878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:864823625 (864.8 MB)  TX bytes:2901246167 (2.9 GB)
          Interrupt:43 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:13:3b:14:05:be  
          inet addr:192.168.60.69  Bcast:192.168.60.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9569074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12959646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4191313000 (4.1 GB)  TX bytes:517660037 (517.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:162514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14704287 (14.7 MB)  TX bytes:14704287 (14.7 MB)

```

and route -n from the server:
```
0.0.0.0         192.168.60.1    0.0.0.0         UG    100    0        0 eth1
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.60.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1

```

I see no problem, all other clients have correct routing and IP addresses, too, all of them are able to connect to internet and non-ubuntu clients.

---

### Post by papibe on 2012-11-18
Thanks.

Have you enabled IP forwarding in your server?

Could you post the result of this command?
```
grep forward /etc/sysctl.conf 
```
Regards.

BTW: I didn't get your topology.

---

