---
title: "Wired networking stopped working"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by bkummel on 2010-11-06
Hi,

Wired *and* wireless networking have been working flawlessly for years on my HP Compaq 6710b laptop. Several weeks ago, after an automatic update via the update manager, my *wired* network stopped working. I did not notice it directly, since my wireless connection took it over. I only noticed it when I had to work in an office where I didn't know the wireless password.

Since then, I have been trying several things and searched several forums. It is hard to find any troubleshooting information about *wired* networking, as most of the problems seem to occur with wireless. 

I did verify that there is no hardware problem. My laptop is dual boot and when I boot the other operating system, the wired network works without problems (as does the wireless.)

Here's some detailed information about my networking configuration:
[LIST]
[*]**lspci | grep 'Ethernet'** returns ```
18:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
```
[*]**ifconfig eth0** returns ```
eth0      Link encap:Ethernet  HWaddr 00:1f:29:8c:78:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 
```
[*]**dmesg | grep 'eth'** returns
```

[    0.180997] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    1.697220] eth0: Tigon3 [partno(none) rev b002] (PCI Express) MAC address 00:1f:29:8c:78:7f
[    1.697222] eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.697225] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.697227] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   34.579200] ADDRCONF(NETDEV_UP): eth0: link is not ready

```
[*]**sudo lshw -C network** returns:
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:50:5a:7a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.241 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:e4100000-e4100fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:18:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:29:8c:78:7f
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v2.09 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:31 memory:e4000000-e400ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```
[/LIST]
My Ubuntu version is **Ubuntu 10.04.1 LTS**. My kernel version is **2.6.32-25-generic i686**. I hope anybody can help me getting my wired network working again! Thanks in advance for any help or suggestion!

Best regards,
Bart Kummel

---

### Post by uncaspi on 2010-11-06
There is several things you can try. The card is present so no hardware problem. The first thing you could do is to look if eth0 is present in the network-manager. If not try /sbin/dhclient eth0

And we will take it from there

---

### Post by bkummel on 2010-11-06
There's an "auto eth0" entry in the Network Connections window (via System | Preferences | Network Connections). There used to be an "auto eth0" entry in the menu that appears if I click on the network symbol in the upper right corner of the screen. However, today there's just "Wired network - disconnected", without the "auto eth0" below it.

**sudo /sbin/dhclient eht0** returns:

```

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
eht0: ERROR while getting interface flags: No such device
eht0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```

---

### Post by uncaspi on 2010-11-06
dmesg tells probably everything. The line eth0 not ready indicate there is something wrong with the cable.

---

### Post by bkummel on 2010-11-07
Sorry, my fault. I was trying all sorts of things, including rebooting with and without the ethernet cable connected. Here's de **dmesg** result with the cable connected:
```

[    0.180997] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    1.685214] eth0: Tigon3 [partno(none) rev b002] (PCI Express) MAC address 00:1f:29:8c:78:7f
[    1.685217] eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.685219] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.685221] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   25.572581] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.266132] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   27.266134] tg3: eth0: Flow control is on for TX and on for RX.
[   27.266285] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   37.684026] eth0: no IPv6 routers present

```
Needless to say that my wired network is still not working. Now I have the cable reconnected, I have my **Auto eth0** entry back in the networking menu. Once I click on it, the network progress indicator is starting to spin. After a few seconds it stops spinning again and I get  a **Wired newtork - Disconnected** notification box...

---

### Post by bkummel on 2010-11-07
I also reran the **sudo lshw -C network** command. The output is slightly different now the cable is reconnected:
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:50:5a:7a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.196 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:e4100000-e4100fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:18:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:29:8c:78:7f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.09 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:31 memory:e4000000-e400ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

