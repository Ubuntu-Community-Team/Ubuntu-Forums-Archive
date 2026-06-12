---
title: "Ubuntu 8.10 + dhcp"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by syntax-error on 2009-04-14
I cloned an ubuntu intrepid installation (with gnome desktop installed and openoffice) and copied it to almost 40 workstations, Initially the based install obtains IP via dhcp, now here's my problem. among those 40+ workstations, only a few are able to obtain IP's via dhcp. most are unable to obtain an IP. If I was to check the settings on the workstations that are able obtain dhcp via 'ifconfig', ifconfig would give me eth3 and lo (which again i found weird). then if i was to check on /etc/network/interfaces lines would be  auto eth0. then upon checking dmesg | grep eth dmesg would tell me that udev is renaming eth0 to eth3 

here's an example workstation:

```
$ ifconfig
eth3      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.2.186  Bcast:192.168.3.255  Mask:255.255.252.0
          inet6 addr: fe80::213:46ff:fe2d:1e4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1862199 (1.8 MB)  TX bytes:101913 (101.9 KB)
          Interrupt:19 Base address:0xec00

eth4      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x8d00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

```
$ less /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

```
$dmesg | grep eth
[    5.103881] eth0: RealTek RTL8139 at 0xec00, xx:xx:xx:xx:xx:xx, IRQ 19
[    5.103890] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.551457] eth1: VIA Rhine II at 0xdffffd00, xx:xx:xx:xx:xx:xx, IRQ 23.
[    6.552192] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    7.900663] Driver 'sd' needs updating - please use bus_type methods
[    7.909217]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   18.416834] udev: renamed network interface eth0 to eth3
[   18.904246] udev: renamed network interface eth1 to eth4
[   46.086508] eth4: link down
[   46.088570] ADDRCONF(NETDEV_UP): eth4: link is not ready
[   46.100922] eth3: link down
[   46.102929] ADDRCONF(NETDEV_UP): eth3: link is not ready
[ 4232.745219] eth3: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 4232.746422] ADDRCONF(NETDEV_CHANGE): eth3: link becomes ready
[ 4242.892034] eth3: no IPv6 routers present
[ 4327.829815] eth3: link down
[ 4336.782437] eth3: link up, 100Mbps, full-duplex, lpa 0x45E1
```

thanks in advance guys..

---

### Post by syntax-error on 2009-04-15
anyone?

---

### Post by Floppyjoe on 2009-04-15
Are all your workstations the same with the same hardware?

Have you tried entering these lines in your /etc/network/interfaces file?
Open this file by opening a terminal and entering:
```
sudo gedit /etc/network/interfaces
```
Add this line to file:
```
auto eth3
iface eth3 inet dhcp
```
Close and save this file.

Then restart networking:
```
sudo /etc/init.d/networking restart
```

---

### Post by Iowan on 2009-04-15
Check */etc/udev/rules.d/70-persistent-net.rules*. You *might* be able to edit away the unused part... perhaps there's a definition for eth0 from the original machine.

---

