---
title: "No internet"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by anon404 on 2010-01-20
I am unable to access webpages unless i use an IP address and that only works for a few pages.
 
Info:
-Using Ubuntu 9.10
-Accessed internet with wireless router via wireless at another residence without problem
-XP has internet access without problem at current residence
 
ifconfig:
```
 
eth0      Link encap:Ethernet  HWaddr 00:26:b9:08:46:bc  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:fe08:46bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:125868 (125.8 KB)  TX bytes:63671 (63.6 KB)
          Interrupt:28 Base address:0xc000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:448 (448.0 B)  TX bytes:448 (448.0 B)
wlan0     Link encap:Ethernet  HWaddr 00:24:d6:04:2a:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
wmaster0  Link encap:UNSPEC  HWaddr 00-24-D6-04-2A-F0-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
```

  *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:04:00.0"]pci@0000:04:00.0[/EMAIL]
       logical name: wmaster0
       version: 00
       serial: 00:24:d6:04:2a:f0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f8000000-f8001fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:06:00.0"]pci@0000:06:00.0[/EMAIL]
       logical name: eth0
       version: 03
       serial: 00:26:b9:08:46:bc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:28 ioport:4000(size=256) memory:f4004000-f4004fff(prefetchable) memory:f4000000-f4003fff(prefetchable) memory:f4020000-f403ffff(prefetchable)

```

---

### Post by chili555 on 2010-01-20
Please post:```
cat /etc/resolv.conf
```

---

### Post by Cabs21 on 2010-01-20
hardware looks like it is running fine.  Could be your browser settings.

---

### Post by anon404 on 2010-01-20
> **chili555 said:**
> Please post:```
cat /etc/resolv.conf
```
 
resolv.conf is empty apart from the comment.

---

### Post by chili555 on 2010-01-20
That's the problem. Please run:```
route -n
```If it turns out that your gateway is 192.168.1.1, please do:```
sudo gedit /etc/resolv.conf
```Add a single line:```
nameserver 192.168.1.1
```Proofread, save and close gedit. Substitute your gateway address if it's not 192.168.1.1.

---

### Post by anon404 on 2010-01-20
route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```
 
I checked resolv.conf when the ethernet wasn't connected so that nameserver was in the file while connected.

---

### Post by chili555 on 2010-01-20
May we please see:```
traceroute www.google.com
ping -c3 www.google.com
```Thanks.

---

### Post by wojox on 2010-01-20
Look at Solution [FOT005]: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

To turn it of system wide look here [http://wojox.homelinux.net/?p=4](http://wojox.homelinux.net/?p=4)

---

### Post by anon404 on 2010-01-20
Disabling IPv6 fixed it. Thanks everyone.

---

