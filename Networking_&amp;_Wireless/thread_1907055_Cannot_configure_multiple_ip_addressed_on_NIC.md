---
title: "Cannot configure multiple ip addressed on NIC"
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by morris_horesh on 2012-01-10
Hi,

I have the following configuration in /etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0
broadcasr 192.168.2.255
network 192.168.2.0

auto eth1:0
iface eth1:0 inet static
name Ethernet alias LAN card
address 192.168.0.101
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0


```After rebooting, ifconfig shows eth1 but does not show eth1:0 and ping 192.168.0.101 results in a request timeout.

After I restart the network service ( /etc/init.d/networking restart ), ifconfig still doesn't show eth1:0 but pinging 192.168.0.101 succeeds.

Any idea why is eth1:0 not shown in ifconfig and why does the address become valid only after restarting the network service ?

---

### Post by drdos2006 on 2012-01-10
Check these out, did a search on "bridging" and "bonding"

[http://ubuntuforums.org/showthread.php?t=1842656](http://ubuntuforums.org/showthread.php?t=1842656)

[http://ubuntuforums.org/showthread.php?t=1840543](http://ubuntuforums.org/showthread.php?t=1840543)

regards

---

### Post by Iowan on 2012-01-10
[Here]("http://ubuntuforums.org/showthread.php?t=1905767") is a similar thread. What happens if you use eth1:1 instead of eth1:0?

---

### Post by morris_horesh on 2012-01-11
> **Iowan said:**
> [Here]("http://ubuntuforums.org/showthread.php?t=1905767") is a similar thread. What happens if you use eth1:1 instead of eth1:0?

eth1:1 causes the same behavior.

---

### Post by morris_horesh on 2012-01-11
> **drdos2006 said:**
> Check these out, did a search on "bridging" and "bonding"

[http://ubuntuforums.org/showthread.php?t=1842656](http://ubuntuforums.org/showthread.php?t=1842656)

[http://ubuntuforums.org/showthread.php?t=1840543](http://ubuntuforums.org/showthread.php?t=1840543)

regards

bonding an bridging are the opposite of what I need. I need one NIC with two addresses. bonding gives two NICS the same address and bridging connects to NICs.

---

### Post by morris_horesh on 2012-01-11
> **Iowan said:**
> [Here]("http://ubuntuforums.org/showthread.php?t=1905767") is a similar thread. What happens if you use eth1:1 instead of eth1:0?

My problem is even worse. not only that the address does not show, I cannot ping it.

---

### Post by jonobr on 2012-01-11
Hello


I tried this on a dell inspiron 710m running 10:04 LTS

I only have one Ethernet connection , ETH0

Here was my first setup using your setup- (notice I have the static config uncommented and am using DHCP on eth0)

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#iface eth0 inet static 
#address 192.168.1.22
#netmask 255.255.255.0
#broadcast 192.168.1.255
#gateway 192.168.1.22
#network 192.168.1.0

auto eth0:1
iface eth0:1 inet static
name Ethernet alias lan card
address 192.168.0.101
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0

```


The interfaced plumbed (got this term from my Solaris days, I believe, the more accepted terms is virtual interface) and I could ping it ok.
At this point I figured it may be a timing issue, maybe the plumbed or virtual interface was being assigned to a interface that wasnt ready,
so I tried to match your config with this

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static 
address 192.168.1.22
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.22
network 192.168.1.0

auto eth0:1
iface eth0:1 inet static
name Ethernet alias lan card
address 192.168.0.101
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0

```

Resulting ifconfig was ok (pasted below) and looked ok,
I was able to ping the plumbed / virtual interface

```
eth0      Link encap:Ethernet  HWaddr 00:14:22:ac:0f:88  
          inet addr:192.168.1.22  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 

eth0:1    Link encap:Ethernet  HWaddr 00:14:22:ac:0f:88  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9814 (9.8 KB)  TX bytes:9814 (9.8 KB)


```

I tried rebooting (previously I used the init.d restart method), again it came up fine.

I can only think of a couple of things,

1- The interface card you have is having a hard time with the virtual interface, see my hardware below that I used.

2- Having an existing ETH0 may be causing an issue plumbing eth1
Maybe trying uncommenting eth1 and try plumbing on ETH0 to match my config and see if it works.

3- Maybe try in a terminal looking at dmesg | grep eth and see if that gives a clue.
Again it could be the interface is not ready to be plumbed


Note I have a unused wireless card on this machine as seen below.

```
  *-network:0
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:10 memory:e0204000-e0205fff
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 02
       serial: 00:14:22:ac:0f:88
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half ip=192.168.1.22 latency=32 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:10 memory:e0206000-e0207fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:8d:c6:2d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by morris_horesh on 2012-01-11
I already did add the virtual address to eth0 and the behavior remained the same.

---

### Post by jonobr on 2012-01-11
Have you tried grepping through dmesg for instances of eth?

---

### Post by morris_horesh on 2012-01-11
> **jonobr said:**
> Have you tried grepping through dmesg for instances of eth?

yes

```

[    1.027130] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.027378] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    1.027384] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.552996] forcedeth 0000:00:14.0: ifname eth1, PHY OUI 0x732 @ 13, addr XX:XX:XX:XX:XX:XX
[    1.553001] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[   14.180673] udevd[440]: renamed network interface eth1 to eth0
[   14.181036] udevd[434]: renamed network interface eth0 to rename2
[   14.250876] udevd[434]: renamed network interface rename2 to eth1
[   14.662930] eth1:  setting half-duplex.
[   24.800035] eth1: no IPv6 routers present
[   24.936030] eth0: no IPv6 routers present



```

---

