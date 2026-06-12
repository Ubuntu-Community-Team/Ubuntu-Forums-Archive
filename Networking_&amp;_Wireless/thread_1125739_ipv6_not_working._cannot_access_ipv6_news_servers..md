---
title: "ipv6 not working. cannot access ipv6 news servers."
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by thespinesplitter on 2009-04-14
hi all,

so heres my problem;
last night i could fetch headers on my IPv6 Usenet servers and since this morning i am no longer able to do so, i have no clue whats up with my 6in4 but i know the server to be up.

PS: the turttle is not flapping its wings anymore.
[http://www.kame.net/](http://www.kame.net/)

here are some outputs:
ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:b3:05:94  

          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::2c0:9fff:feb3:594/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:205102 errors:0 dropped:0 overruns:0 frame:0

          TX packets:172998 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:184080063 (175.5 MB)  TX bytes:56913622 (54.2 MB)

          Interrupt:11 Base address:0xa000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:80536 errors:0 dropped:0 overruns:0 frame:0

          TX packets:80536 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:4415522 (4.2 MB)  TX bytes:4415522 (4.2 MB)


```

lshw -C network:
```
  
*-network:0             

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:05:00.0

       logical name: eth0

       version: 10

       serial: 00:c0:9f:b3:05:94

       size: 100MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

  *-network:1

       description: Network controller

       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

       vendor: Broadcom Corporation

       physical id: 2

       bus info: pci@0000:05:02.0

       version: 02

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master

       configuration: driver=b43-pci-bridge latency=64 module=ssb

  *-network DISABLED

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:90:4b:f7:ff:ba

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


```

cat /etc/network/interfaces:
```
auto lo

iface lo inet loopback

```

thanks in advance pals.

---

### Post by gombadi on 2009-04-14
> 
so heres my problem;
last night i could fetch headers on my IPv6 Usenet servers and since this morning i am no longer able to do so, i have no clue whats up with my 6in4 but i know the server to be up.


According to your configuration you currently do not have an ipv6 address allocated to eth0 with Scope:Global.

How was the ipv6 address configured last time you used it? Tunnel with a provider?

Check /var/log/syslog for any errors with bringing up the tunnel when your machine booted.

I was using tspc to provide a tunnel but in the last month or so it was so unreliable I dropped them and now use my own tunnel over OpenVPN.

---

