---
title: "Need Some Help Getting my Nic Card Working"
date: 2012-08-28
forum: Networking &amp; Wireless
---

### Post by w201 on 2012-08-28
Hi guys- 

I have issues with one of my ethernet interfaces (eth1), so I've been trying to bring up eth0 without any luck. So far, I've tried the following:

edited /etc/network/interfaces from:
> auto lo
iface lo inet loopbackto 

> auto eth0
iface eth0 inet dhcpthen restarted networking with /etc/init.d/networking restart

logged out, logged back in. Still nothing.  Something happned along the way and now my network manager wont recognize the device I want to enable, says device not managed.

Any help would be great!

---

### Post by Iowan on 2012-08-28
Devices specified in */etc/network/interfaces* are usually not managed by Network Manager.

You will probably want to put this back in */etc/network/interfaces*:```
auto lo
iface lo inet loopback 
```
even if you choose to include the definition for eth0.

---

### Post by w201 on 2012-08-28
I had already changed it back because it wasn't helping anyway. I also tried sudo ifconfig eth1 down, and sudo ifconfig eth0 up, and restarted the network services without any luck. 

Any ideas what I might be able to do. If it helps you, I'm trying to use the first interface below and deactivate the one below it. 

>       
      description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 10:bf:48:40:ba:ac
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz


> 
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 5
       bus info: pci@0000:03:05.0
       logical name: eth1
       version: 78
       serial: 00:04:75:e9:f6:61
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz


---

### Post by Iowan on 2012-08-28
What are the results of **ifconfig -a**?

---

### Post by w201 on 2012-08-28
When I bring down eth1 and plug my ethernet cable into eth0, nothing happens. I see network manager searching for an ip address, but it doesn't find one.

> 
eth0      Link encap:Ethernet  HWaddr 10:bf:48:40:ba:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:72 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:04:75:e9:f6:61  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::204:75ff:fee9:f661/64 Scope:Link
          inet6 addr: 2001:558:6036:2e:7d52:d691:612:8cd4/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:214318 errors:0 dropped:0 overruns:1 frame:0
          TX packets:35160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67370483 (67.3 MB)  TX bytes:3527874 (3.5 MB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:8c:4f:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Also, I'm seeing this in my log files, does this have anything to do with my NIC card? 

> 
Aug 28 23:53:39 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: No buffer space available
Aug 28 23:54:09 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: error processing netlink message: Out of memory
Aug 28 23:54:39 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: No buffer space available
Aug 28 23:55:09 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: error processing netlink message: Out of memory
Aug 28 23:55:39 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: No buffer space available
Aug 28 23:56:09 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: error processing netlink message: Out of memory
Aug 28 23:56:39 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: No buffer space available
Aug 29 00:00:39 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: No buffer space available
Aug 29 00:01:59  NetworkManager[747]: last message repeated 2 times
Aug 29 00:02:59  NetworkManager[747]: last message repeated 2 times
Aug 29 00:03:09 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: error processing netlink message: Out of memory
Aug 29 00:03:39 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: No buffer space available
Aug 29 00:04:09 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: No buffer space available
Aug 29 00:04:39 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: error processing netlink message: Out of memory
Aug 29 00:05:09 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: No buffer space available
Aug 29 00:06:30  NetworkManager[747]: last message repeated 2 times
Aug 29 00:07:30  NetworkManager[747]: last message repeated 2 times
Aug 29 00:08:30  NetworkManager[747]: last message repeated 2 times
Aug 29 00:10:39 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: No buffer space available
Aug 29 00:12:00  NetworkManager[747]: last message repeated 2 times
Aug 29 00:13:00  NetworkManager[747]: last message repeated 2 times
Aug 29 00:13:09 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: error processing netlink message: Out of memory
Aug 29 00:13:39 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: error processing netlink message: Out of memory
Aug 29 00:14:09 w201 NetworkManager[747]: <warn> error monitoring device for netlink events: No buffer space available


---

### Post by dandnsmith on 2012-08-29
Looking at the details for eth0 and eth1, I note that the workable interface is the 3C905C (an old and reliable interface chipset), while the other is the RTL8111 which is currently giving rise to a lot of problems reported in these fora.
Some people talk about using RTL drivers, while others have problems even with these.
It might be worth checking other posts to see if anything there can be used by you.

---

### Post by w201 on 2012-08-29
Thank you for the info. I'll check that out to see what I can find.

---

