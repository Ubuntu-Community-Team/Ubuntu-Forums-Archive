---
title: "Onboard network card not working"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by nikolay.kuchumov on 2010-05-14
Introduction:

I was running Ubuntu 9.04 on Asus P5QL-E, having an onboard Atheros ethernet controller, and it worked.
Then I moved to OpenSUSE.
Then I installed the second network card: a PCI 3Com Ethernet adapter.
I did that to make my home PC a gateway.
Then I got issues with ATI graphics card and moved back to Ubuntu 10.04.

The issue:

Now i'm having only eth0, which is the 3Com card, connected to the local router.
And eth1 is not present, and is not found, if i try to "up" it using ifconfig.

The output of ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:04:76:14:80:78  
          inet addr:190.170.1.123  Bcast:190.170.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fe14:8078/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59612 errors:0 dropped:0 overruns:1 frame:0
          TX packets:47315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25478224 (25.4 MB)  TX bytes:12767910 (12.7 MB)
          Interrupt:18 Base address:0x2c00 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1918141 (1.9 MB)  TX bytes:1918141 (1.9 MB)

virbr0    Link encap:Ethernet  HWaddr 9e:58:3c:b3:e3:01  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::9c58:3cff:feb3:e301/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:18456 (18.4 KB)

```

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 190.170.1.123
netmask 255.255.255.0
gateway 190.170.1.1

```

lspci:
```

02:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device 8304
	Flags: fast devsel, IRQ 17
	Memory at fe9c0000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at cc00 [size=128]
	Capabilities: <access denied>
	Kernel modules: atl1e

05:02.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
	Subsystem: 3Com Corporation Device 1000
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at ec00 [size=128]
	Memory at febffc00 (32-bit, non-prefetchable) [size=128]
	Expansion ROM at f0800000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x

```

lsmod | grep atl1e
```

atl1e                  33233  0 

```

lsmod | grep 3c59x
```

3c59x                  37031  0 
mii                     5237  1 3c59x

```

dmesg | grep atl1e

```


```

dmesg | grep 3c59x
```

[    2.121777] 3c59x 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.121807] 3c59x: Donald Becker and others.

```

dmesg | grep atl1e
```


```

dmesg | grep eth
```

[    8.962278] eth0:  setting full-duplex.
[   19.712504] eth0: no IPv6 routers present

```

sudo lshw -C Network
```

  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fe9c0000-fe9fffff ioport:cc00(size=128)
  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth0
       version: 74
       serial: 00:04:76:14:80:78
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=190.170.1.123 latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:ec00(size=128) memory:febffc00-febffc7f memory:f0800000-f081ffff(prefetchable)

```

Can you advice me any way of bringing the onboard eth1 up?

It says, the onboard card is UNCLAIMED.
I think, I'll try to "CLAIM" it somehow.

---

### Post by nikolay.kuchumov on 2010-05-14
I've tried to make a dist-upgrade.
That's not likely to resolve the issue, but i'll go reboot.

---

### Post by nikolay.kuchumov on 2010-05-14
I've rebooted without the PCI ethernet card, and it didn't activate the Atheros onboard ethernet card - it just said that network not found.
I'll go report this issue to launchpad

---

### Post by nikolay.kuchumov on 2010-05-14
And also I've updated my BIOS somewhere between 9.04 and 10.04 - maybe it could cause the issue.

---

### Post by nikolay.kuchumov on 2010-05-14
The ASUS drivers aren't compiling because of the Linux Kernel update:

```

/home/kuchumovn/LinuxDrivers/Lan/atl1e/src/at_main.c:397: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/home/kuchumovn/LinuxDrivers/Lan/atl1e/src/at_main.c:398: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/home/kuchumovn/LinuxDrivers/Lan/atl1e/src/at_main.c:399: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/kuchumovn/LinuxDrivers/Lan/atl1e/src/at_main.c:400: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/kuchumovn/LinuxDrivers/Lan/atl1e/src/at_main.c:401: error: &#8216;struct net_device&#8217; has no member named &#8216;set_multicast_list&#8217;
/home/kuchumovn/LinuxDrivers/Lan/atl1e/src/at_main.c:402: error: &#8216;struct net_device&#8217; has no member named &#8216;set_mac_address&#8217;
/home/kuchumovn/LinuxDrivers/Lan/atl1e/src/at_main.c:403: error: &#8216;struct net_device&#8217; has no member named &#8216;change_mtu&#8217;
/home/kuchumovn/LinuxDrivers/Lan/atl1e/src/at_main.c:404: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/kuchumovn/LinuxDrivers/Lan/atl1e/src/at_main.c:415: error: &#8216;struct net_device&#8217; has no member named &#8216;tx_timeout&#8217;
/home/kuchumovn/LinuxDrivers/Lan/atl1e/src/at_main.c:423: error: &#8216;struct net_device&#8217; has no member named &#8216;vlan_rx_register&#8217;
/home/kuchumovn/LinuxDrivers/Lan/atl1e/src/at_main.c:426: error: &#8216;struct net_device&#8217; has no member named &#8216;poll_controller&#8217;

```


I've installed drivers from the Atheros site, but it  didn't take effect:
[http://ubuntuforums.org/showthread.php?p=9257623](http://ubuntuforums.org/showthread.php?p=9257623)

(also, the archive is corrupted)

---

