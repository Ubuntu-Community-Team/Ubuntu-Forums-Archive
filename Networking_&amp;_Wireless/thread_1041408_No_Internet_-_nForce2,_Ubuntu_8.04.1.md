---
title: "No Internet - nForce2, Ubuntu 8.04.1"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by Bob Dobbs on 2009-01-16
Hi. I'm relatively new to Linux and can't connect to the Internet. The computer in question connected at one time (6 months ago) to the Internet via this Ubuntu distr., but I can't connect now. My modem is a Motorola SB5120 from Cox Cable.

Here's the commands I've run and the info I've gotten. If I'm missing some info from lsmod or dmesg, I can print the full output.

Many thanks for any help.

lspci

```
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)

```
ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:50:8d:e7:fe:dd  
          inet addr:68.11.55.181  Bcast:68.11.43.255  Mask:255.255.252.0
          inet6 addr: fe80::250:8dff:fee7:fedd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1997570 (1.9 MB)  TX bytes:33476 (32.6 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41400 (40.4 KB)  TX bytes:41400 (40.4 KB)


```
iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.
```



lsmod 

```
i2c_core               24832  1 i2c_nforce2
```

dmesg

```
[   28.643576] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:50:8d:e7:fe:dd
[   28.643583] forcedeth 0000:00:04.0: timirq lnktim desc-v1
[   67.012069] eth0: no IPv6 routers present
```

sudo lshw -C network

  ```
*-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:50:8d:e7:fe:dd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=68.11.45.191 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s

```

iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```
 lsb_release -d

```
Description:	Ubuntu 8.04.1

```
uname -mr

```
2.6.24-19-generic i686
```

---

### Post by Loosewheel on 2009-01-16
Is 'inet addr:68.11.55.181' really your network address, not something like '192.168.x.x'? If so, I don't know. If it isn't:

click on the 'nm-applet>Manual configuration>Unlock>Wired Connection>Properties' and configure for DHCP.

Here is a user manual:  
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

---

### Post by Bob Dobbs on 2009-01-16
> **Loosewheel said:**
> Is 'inet addr:68.11.55.181' really your network address, not something like '192.168.x.x'? If so, I don't know. If it isn't:

click on the 'nm-applet>Manual configuration>Unlock>Wired Connection>Properties' and configure for DHCP.

Here is a user manual:  
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

Thanks for the reply...

The IP isn't a 192.168.x.x. 

There is no router in the setup. (I plan on doing that, but figured I'd try to make sure I can connect with just Desktop-->Cable Modem first to make sure everything is kosher)

---

