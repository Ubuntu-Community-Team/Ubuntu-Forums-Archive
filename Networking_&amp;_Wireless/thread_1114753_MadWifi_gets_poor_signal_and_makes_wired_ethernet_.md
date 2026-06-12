---
title: "MadWifi gets poor signal and makes wired ethernet drop all packets"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by Blahah on 2009-04-03
Running Ubuntu 8.10 Intrepid Ibex on an Acer Aspire 110l with an atheros wireless chipset, I have to use MadWifi to get a consistently working wireless. There are two problems I'm encountering:

1. Even when sitting about 10ft away from a powerful wireless router I still get less than 20% signal most of the time. Another laptop sitting next to mine gets 80%. Are there some settings I can change to configure MadWifi or my wireless card to get a better signal? Even using the Ath5k drivers, I get the same weak signal levels.

2. With MadWifi drivers installed, my wired ethernet drops all packets, meaning I cannot even get an IP address on a wired network.

The output of ifconfig shows the problem with eth0:

```
ath0      Link encap:Ethernet  HWaddr 00:22:68:90:89:3f  
          inet addr:172.16.26.71  Bcast:172.16.27.255  Mask:255.255.252.0
          inet6 addr: fe80::222:68ff:fe90:893f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2521462 (2.5 MB)  TX bytes:261425 (261.4 KB)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:8f:1e:7c  
          inet6 addr: fe80::21e:68ff:fe8f:1e7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1291845555 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6176 (6.1 KB)  TX bytes:6176 (6.1 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-22-68-90-89-3F-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4192 errors:0 dropped:0 overruns:0 frame:428
          TX packets:1699 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:1634304 (1.6 MB)  TX bytes:306965 (306.9 KB)
          Interrupt:18 
```

Note that if I add madwifi to /etc/default/linux-restricted-modules-common and reboot, the wired ethernet starts working. It does not work if I just modprobe -r ath_pci.


Can anyone suggest a reason for or solution to either of these issues?


EDIT: after some playing, I found that there is a conflict between ath_pci and ath_hal. If I:

```
sudo modprobe -r ath_pci
sudo modprobe ath_hal
```

The wireless switches off and the wired connection instantly connects. Why is there a conflict?

---

