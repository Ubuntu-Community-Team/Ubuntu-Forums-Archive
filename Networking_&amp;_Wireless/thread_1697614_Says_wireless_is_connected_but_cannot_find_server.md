---
title: "Says wireless is connected but cannot find server"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by Shredthegnarnia on 2011-03-01
Just installed ubuntu 10.04 on my Dell inspiron 1525 laptop. Everything got installed right, and I elected to select the sta driver rather than the B43 driver. After restarting, the b43 option disappeared. The wireless said it connected, but when i went to firefox it wouldn't load and said server not found. My wireless card is a bcm4312. Any ideas as to why this is not working?

---

### Post by ankith13 on 2011-03-01
is your interface up and working....
please paste your ifconfig and iwconfig output ....

---

### Post by Shredthegnarnia on 2011-03-01
ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:21:9b:cd:35:c3  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:9bff:fecd:35c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9787697 (9.7 MB)  TX bytes:1587223 (1.5 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:44:e1:21:78  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fee1:2178/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1833 dropped:0 overruns:0 frame:41739
          TX packets:16 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3534 (3.5 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
 
```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

i don't know exactly what you mean by the interface being up and running  (im a noob). but i can work everything fine with ethernet and the OS itself is fine. thanks for the help

---

### Post by Shredthegnarnia on 2011-03-01
bump

---

### Post by nm_geo on 2011-03-02
Try these two 

```
sudo lshw -C network
```&

```
rfkill list
```Paste results

---

### Post by ankith13 on 2011-03-02
I think the wireless is not connected to any access point. 
just try and ping to any node in your network..

---

### Post by glongrid on 2011-03-02
I have similar problem to _shredthegnarnia_ but with a 1520 laptop. I connect but only for a few minutes but even during this time cannot get firefox to find server. Windows signal is excellent.
As a very noob, how do I "ping to any node in my network"?

---

### Post by Shredthegnarnia on 2011-03-02
```

sudo lshw -c network:
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:cd:35:c3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.0.8 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:e1:21:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.42.43.1 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fe7fc000-fe7fffff

```
```

rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
again thanks for the help

---

