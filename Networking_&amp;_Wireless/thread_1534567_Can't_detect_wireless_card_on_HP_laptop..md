---
title: "Can't detect wireless card on HP laptop."
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by cannibalistmonk on 2010-07-19
I'm on an HP Pavillion dv4-1125nr with a Broadcom BCM 4312 network card.

I only have Ubuntu 10.04 installed on this computer.

ifconfig reports:
```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:b5:b4:85  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:feb5:b485/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1002 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1258349 (1.2 MB)  TX bytes:140028 (140.0 KB)
          Interrupt:30 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

```

and iwconfig reports:
```
lo        no wireless extensions.

eth0      no wireless extensions.


```

It isn't even detecting the wireless card, and the network manager will only let me connect to wired networks (I'm connected to my router via ethernet cable right now).

I've pressed the LED killswitch but it does nothing (doesn't change from orange to blue nor does it have any noticeable effect on the network manager or the reports of the above 2 commands).

---

### Post by kuckunniwi on 2010-07-19
> **cannibalistmonk said:**
> I'm on an HP Pavillion dv4-1125nr with a Broadcom BCM 4312 network card.

I only have Ubuntu 10.04 installed on this computer.

ifconfig reports:
```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:b5:b4:85  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:feb5:b485/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1002 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1258349 (1.2 MB)  TX bytes:140028 (140.0 KB)
          Interrupt:30 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

```

and iwconfig reports:
```
lo        no wireless extensions.

eth0      no wireless extensions.


```

It isn't even detecting the wireless card, and the network manager will only let me connect to wired networks (I'm connected to my router via ethernet cable right now).

I've pressed the LED killswitch but it does nothing (doesn't change from orange to blue nor does it have any noticeable effect on the network manager or the reports of the above 2 commands).


I'm having a similar problem with an Intel Wireless Link 1000...if I get any useful feedback, I'll let you know

---

### Post by lijcam on 2010-07-19
I got the same card in my dell. You just need to install the Broadcom driver and reboot. 

```
sudo apt-get install bcmwl-kernel-source
```

---

