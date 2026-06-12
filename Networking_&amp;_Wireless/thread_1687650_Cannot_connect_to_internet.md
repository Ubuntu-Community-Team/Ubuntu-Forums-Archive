---
title: "Cannot connect to internet"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by mwotsch on 2011-02-14
Hi!

I have ubuntu 10.04 installed, which has been working fine until today. Today when booting the machine I cannot establish any sort of connection to the outside world. I have tried 

```
#sudo dhclient
```which just keeps trying 
```
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval x
```, then tells me that no DHCPOFFERS were received and goes to sleep afterwards.

Then I ran 

```
#sudo ifconfig
eth0      Link encap:Ethernet  HWaddr <removedMacAddress>  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5191 (5.1 KB)
          Interrupt:27 Base address:0xa000 

eth0:avahi Link encap:Ethernet  HWaddr <removedMacAddress>  
          inet addr:xxx.xxx.11.94  Bcast:xxx.xxx.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:27 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73649 (73.6 KB)  TX bytes:73649 (73.6 KB)

```I cleaned up the IP addresses and Mac addresses above.

This very same machine connectes fine (both wired and wirelessly) on its Windows 7 partition, which leads me to believe I might have a driver issue.

I have already turned of ipv6, which according to ```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```is 1 (disabled)

Edit: I should perhaps add that I have a Realtek RTL8111/8168B PCI card. This seems to give people trouble. I'll keep looking into that.

Any hints?

Thanks,
Marco

---

### Post by mwotsch on 2011-02-14
I just found out that if I shutdown and unplug the machine for 20 seconds, then boot straight into ubuntu, it works.

Seems like the issue I have is the "Wake-on-lan after shutdown" problem in Windows.

Marco

---

