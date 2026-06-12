---
title: "20% Average of Packet Loss in local network"
date: 2010-08-16
forum: Networking &amp; Wireless
---

### Post by jjgl7 on 2010-08-16
Hi:

I'm having constantly networks blackouts with my Ubuntu 10.04.1 LTS.  I ping my router, local network 192.168.77.1 with the IP, and sometimes I loss like ten packets and then the network reestablish. 

I also like to comment that I have another computer pinging at the same time, and doesn't loss packets over the wireless, then I tried the same with my wireless on the ubuntu and doesn't loss packets.  

**My Ping Example:**

```

64 bytes from 192.168.77.1: icmp_seq=16 ttl=64 time=1.05 ms
64 bytes from 192.168.77.1: icmp_seq=26 ttl=64 time=1.05 ms
64 bytes from 192.168.77.1: icmp_seq=27 ttl=64 time=1.02 ms
...
64 bytes from 192.168.77.1: icmp_seq=67 ttl=64 time=1.03 ms
64 bytes from 192.168.77.1: icmp_seq=68 ttl=64 time=1.04 ms
64 bytes from 192.168.77.1: icmp_seq=69 ttl=64 time=1.01 ms
^C
--- 192.168.77.1 ping statistics ---
69 packets transmitted, 49 received, 28% packet loss, time 68074ms
rtt min/avg/max/mdev = 1.003/1.148/2.775/0.359 ms

```[B]My ifconfig:
[/B]```

eth0      Link encap:Ethernet  HWaddr 00:15:c5:cf:88:6f  
          inet addr:192.168.77.77  Bcast:192.168.77.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fecf:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:558523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:902900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77467909 (77.4 MB)  TX bytes:1188040888 (1.1 GB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:19:7d:2e:78:52  
          inet6 addr: fe80::219:7dff:fe2e:7852/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:889 errors:0 dropped:0 overruns:0 frame:9528
          TX packets:119 errors:24 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:133069 (133.0 KB)  TX bytes:42238 (42.2 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10357 (10.3 KB)  TX bytes:10357 (10.3 KB)

usb0      Link encap:Ethernet  HWaddr 02:80:37:21:03:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```Could anyone help me, to solve the packet loss, over my wired connection?

Thanks

---

