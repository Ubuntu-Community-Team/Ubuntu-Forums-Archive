---
title: "Ubuntu 13.04 - Wireless network does not work"
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by mscava on 2013-06-04
Cannot connect to a particular wireless network.
[LIST]
[*]Wired network using the same router works
[*]Wireless connection works under Windows
[*]Connecting to a different wireless network also works
[*]Other PCs are able to connect (they use Windows though)
[/LIST]

```
$uname -a
Linux eggplant 3.8.0-23-generic #34-Ubuntu SMP Wed May 29 20:22:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
$lspci | grep Network
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```

```
$route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.32.1     0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
172.16.32.0     0.0.0.0         255.255.255.0   U     9      0        0 eth1
```

```
$ifconfig
eth0      Link encap:Ethernet  HWaddr 68:b5:99:ee:d8:87  
          inet addr:172.16.32.80  Bcast:172.16.32.255  Mask:255.255.255.0
          inet6 addr: fe80::6ab5:99ff:feee:d887/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7594460 (7.5 MB)  TX bytes:1133153 (1.1 MB)


eth1      Link encap:Ethernet  HWaddr ac:81:12:13:63:cf  
          inet addr:172.16.32.78  Bcast:172.16.32.255  Mask:255.255.255.0
          inet6 addr: fe80::ae81:12ff:fe13:63cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3687 errors:0 dropped:0 overruns:0 frame:13105
          TX packets:417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:454148 (454.1 KB)  TX bytes:45518 (45.5 KB)
          Interrupt:19 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100634 (100.6 KB)  TX bytes:100634 (100.6 KB)
```

```
$ping google.com
ping: unknown host google.com
$ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
--- 8.8.8.8 ping statistics ---
47 packets transmitted, 0 received, 100% packet loss, time 45999ms
$ping 172.16.32.1
--- 172.16.32.1 ping statistics ---
14 packets transmitted, 0 received, 100% packet loss, time 13105ms
```

Any idea what might be wrong?

---

### Post by chili555 on 2013-06-04
Please try the following:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.

---

### Post by mscava on 2013-06-04
Perfect! It works now, Thank you.

---

