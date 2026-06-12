---
title: "Wired network stopped working 12.04"
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by st0nes on 2013-04-21
Hi all,

This morning I unplugged and moved my router.  When I booted it up again, I couldn't connect to the wired network from my desktop, which doesn't have wireless.  I have tried several of the suggestions on other threads in the forums, but met with no success.  Here is some further information:-

```
mark@mark-OptiPlex-GX520:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:7a:98:84
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5751-v3.44a latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:fe8f0000-fe8fffff
```
```
mark@mark-OptiPlex-GX520:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:72:7a:98:84  
          inet6 addr: fe80::213:72ff:fe7a:9884/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11536 (11.5 KB)  TX bytes:11799 (11.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7488 (7.4 KB)  TX bytes:7488 (7.4 KB)

```
```
mark@mark-OptiPlex-GX520:~$ cat /var/log/syslog | grep -i Network | tail -25
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]:    SCPlugin-Ifupdown: end _init.
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]:    Ifupdown: get unmanaged devices count: 1
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]:    SCPlugin-Ifupdown: (-1238357384) ... get_connections.
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]:    SCPlugin-Ifupdown: (-1238357384) ... get_connections (managed=false): return empty list.
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]:    keyfile: parsing Wired connection 1 ... 
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]:    keyfile:     read connection 'Wired connection 1'
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]:    keyfile: parsing Vodacom Default 1 ... 
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]:    keyfile:     read connection 'Vodacom Default 1'
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]:    keyfile: parsing Vodacom Default ... 
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]:    keyfile:     read connection 'Vodacom Default'
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]:    Ifupdown: get unmanaged devices count: 1
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <info> modem-manager is now available
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <info> Networking is enabled by state file
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <warn> failed to allocate link cache: (-10) Operation not supported
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <info> (eth0): carrier is ON
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 21 13:39:42 mark-OptiPlex-GX520 NetworkManager[2304]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Apr 21 13:40:37  NetworkManager[2304]: last message repeated 5 times
```
Contents of /etc/network/interfaces:--
```
auto lo
iface lo inet loopback

```
I have tried rebooting both the router and the PC, adding the lines
```
auto eth0 
iface eth0 inet dhcp
```
to /etc/network/interface file, but with no joy.  I have dual-boot setup with Windows 7, which hasn't been booted for months.  I just tested the connection via Windows, and I get the following error:--
> 'Local Area Connection' doesn't have a valid IP configuration
If any further information is required please let me know.

Thanks in advance,
Mark

---

### Post by Iowan on 2013-04-21
I presume you checked the cable...

---

### Post by st0nes on 2013-04-21
> **Iowan said:**
> I presume you checked the cable...
Yes.  LEDs light up when it's plugged in.  Tried other ports on the router too.

---

### Post by marvselby on 2013-04-22
Is this the only machine plugged into the router?  Are there any wireless connections?  Do you know the IP address of the router?  For most routers it's usually 192.168.1.1.  If you know it, try pinging the router (ping 192.168.1.1).  Are the lights on the front of the router blinking?  While it was disconnected, did the dog pee on the router?  Sorry for so many questions.

---

### Post by Iowan on 2013-04-23
Pinging won't work without an IP address for eth0... 
You should be able to set one up - either via Network Manager (preferred) or */etc/network/interfaces*.
(NM and */etc/network/interfaces* don't play nicely together.)

---

