---
title: "ethernet : Activation of network connection failed"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by sonee on 2011-10-26
Hi everyone,

     I have a desktop computer connected to a router using wired connection (eth0).
I opened network in gnome-control-center, and the status of the connection keeps the cycle "connected > connection failed > disconnected > cable unplugged > connecting > connected".
There is also a notification that reads "Connection failed: Activation of network connection failed".

     When the network is connected, i can ping gg, but then the network is disconnected, and ping says
"ping: sendmsg: Network is unreachable"

    My laptop still have connection and access to the internet. Also in Windows the connection is good. I believe the problem is with ubuntu, not the router nor the ethernet cable.

    Thanks in advance!

---

### Post by jonobr on 2011-10-26
Hello


In the terminal Could you show the results of 

```
lshw -C network
```
also could you post 
```
/etc/network/interfaces
```
and
```
ifconfig 
```

maybe also

```
dmesg | grep eth
```

It does however sound like a flaky cable mind you.
You could try a new cable, and then maybe set the ip address to static and see if the config is held

---

### Post by sonee on 2011-10-26
```
lshw -C network

===================================

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: 8c:89:a5:13:6f:bb
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.15 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:d000(size=256) memory:dc104000-dc104fff memory:dc100000-dc103fff
``````
/etc/network/interfaces

========================

auto lo
iface lo inet loopback

``````
ifconfig 

=========================

eth0      Link encap:Ethernet  HWaddr 8c:89:a5:13:6f:bb  
          inet6 addr: fe80::8e89:a5ff:fe13:6fbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:314 errors:0 dropped:314 overruns:0 frame:314
          TX packets:739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84836 (84.8 KB)  TX bytes:124865 (124.8 KB)
          Interrupt:41 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6855 (6.8 KB)  TX bytes:6855 (6.8 KB)

``````
dmesg | grep eth

============================

[    1.208678] r8169 0000:05:00.0: eth0: RTL8168b/8111b at 0xffffc90000c6c000, 8c:89:a5:13:6f:bb, XID 0c900800 IRQ 41
[   15.661607] r8169 0000:05:00.0: eth0: link down
[   15.661655] r8169 0000:05:00.0: eth0: link down
[   15.662037] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.382027] r8169 0000:05:00.0: eth0: link up
[   17.382469] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.158317] eth0: no IPv6 routers present
[   41.536579] r8169 0000:05:00.0: eth0: link down
[   41.536622] r8169 0000:05:00.0: eth0: link down
[   41.537011] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   41.704229] r8169 0000:05:00.0: eth0: link down
[   41.704665] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.245175] r8169 0000:05:00.0: eth0: link down
[   43.245598] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   45.662914] r8169 0000:05:00.0: eth0: link up
[   45.663338] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   56.230662] eth0: no IPv6 routers present
[   63.868094] r8169 0000:05:00.0: eth0: link down
[   63.868147] r8169 0000:05:00.0: eth0: link down
[   63.868550] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   64.215398] r8169 0000:05:00.0: eth0: link down
[   64.215880] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   65.624629] r8169 0000:05:00.0: eth0: link down
[   65.625054] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   67.299090] r8169 0000:05:00.0: eth0: link up
[   67.299515] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   77.388610] eth0: no IPv6 routers present
[   86.443203] r8169 0000:05:00.0: eth0: link down
[   86.443246] r8169 0000:05:00.0: eth0: link down
[   86.443951] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   86.638815] r8169 0000:05:00.0: eth0: link down
[   86.639567] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   88.231647] r8169 0000:05:00.0: eth0: link down
[   88.232383] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   90.890425] r8169 0000:05:00.0: eth0: link up
[   90.891139] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  101.867834] eth0: no IPv6 routers present
```

---

### Post by jonobr on 2011-10-26
> /etc/network/interfaces

========================

auto lo
iface lo inet loopback

This looks very sparse

I would expect the following lines in there also for dhcp
(assuming your using DHCP??


```
auto eth0
iface eth0 inet dhcp

```

try inserting that and restart netowking

---

### Post by sonee on 2011-10-26
> **jonobr said:**
> It does however sound like a flaky cable mind you.
You could try a new cable, and then maybe set the ip address to static and see if the config is held

I tried plugging the cable into my laptop then disable wireless interface. 
There was no problem with the wired connection.

---

### Post by papibe on 2011-10-26
> **jonobr said:**
> ...This looks very sparse...
Actually it looks OK if he's running the Desktop edition (thus network-manager is managing its network).

Regards.

---

### Post by jonobr on 2011-10-26
bugger papibe is right if your using nm to control your network settings.

I would still recommend checking cables and changing to a static temporarily to see if this issue goes away.

---

### Post by sonee on 2011-10-26
Yes, I am using network-manager and its a desktop computer.
I tried setting up static ip manually but the issue is still there :(

---

### Post by jonobr on 2011-10-26
If you have it on static and continuously ping that static IP address what happens from the same machine what happens?

What about when you swap to dhcp? same result from continuous ping?

Did you try pinging from another machine on the same network?
What happens for static, then for DHCP?

Did you try swapping cables?
See if there is any difference?

Process of elimination... mundane and boring but has to be done

---

