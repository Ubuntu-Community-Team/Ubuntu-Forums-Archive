---
title: "Ubuntu 12.04 internet connx on laptop but not on PC"
date: 2013-05-29
forum: Networking &amp; Wireless
---

### Post by paulemony on 2013-05-29
Have just changed ISP with new router & have a laptop and a PC both running Ubuntu 12.04. Internet no problem on laptop, wireless or ethernet, but PC won't connect (also tried wireless and ethernet, connects to router but that's it). Have checked System settings/Network and Network Tools but can't see anything wrong (but then I don't really know what I'm looking for).  Can't find definitive answer in forum, any suggestions? Thx

---

### Post by ahallubuntu on 2013-05-29
~

---

### Post by paulemony on 2013-05-29
I think you mean:

```
sudo gedit /etc/network/interfaces
```

Both machines show:

```
auto lo
iface lo inet loopback

```

PC worked OK with previous router, there's obviously something about the new one it doesn't like.

---

### Post by ahallubuntu on 2013-05-29
~

---

### Post by paulemony on 2013-05-29
Still not sure what I'm looking for:

[B]Laptop
[/B]
```
~$ ifconfigeth0      Link encap:Ethernet  HWaddr 00:1e:33:78:7e:f1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14729 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14561047 (14.5 MB)  TX bytes:3472789 (3.4 MB)
          Interrupt:43 Base address:0x8000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4303425 (4.3 MB)  TX bytes:4303425 (4.3 MB)


wlan0     Link encap:Ethernet  HWaddr 00:21:63:aa:0c:a9  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:feaa:ca9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28026346 (28.0 MB)  TX bytes:39807714 (39.8 MB)



```

**PC**

```
~$ ifconfigeth0      Link encap:Ethernet  HWaddr00:11:d8:22:17:40  
          inet6 addr:fe80::211:d8ff:fe22:1740/64 Scope:Link 
          UP BROADCAST RUNNINGMULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TXbytes:0 (0.0 B) 
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1 Mask:255.0.0.0 
          inet6 addr: ::1/128Scope:Host 
          UP LOOPBACK RUNNING MTU:16436  Metric:1 
          RX packets:13 errors:0dropped:0 overruns:0 frame:0 
          TX packets:13 errors:0dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:856 (856.0 B)  TXbytes:856 (856.0 B) 


wlan0     Link encap:Ethernet  HWaddr80:1f:02:3a:b4:c3  
          inet addr:192.168.0.2 Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr:fe80::821f:2ff:fe3a:b4c3/64 Scope:Link 
          UP BROADCAST RUNNINGMULTICAST  MTU:1500  Metric:1 
          RX packets:184 errors:0dropped:0 overruns:0 frame:0 
          TX packets:303 errors:0dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:55998 (55.9 KB)  TXbytes:35100 (35.1 KB) 



```

---

### Post by ahallubuntu on 2013-05-29
~

---

### Post by paulemony on 2013-05-29
First two ping ok but third gives  

```
ping: unknown host google.com
```

---

