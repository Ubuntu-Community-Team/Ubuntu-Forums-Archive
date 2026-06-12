---
title: "Quad Port Ethernet Card does not work properly"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by FlameLicker on 2011-12-13
Dear all,

I've got 2 HP Proliant 380 G7 Servers running Ubuntu Server 10.04 LTS. They come with 4 internal ethernet ports which are working fine and as expected and with a Quad Port Ethernet PCI Card which makes me head aches.

The vendor of the Ethernet Card is QLOGIC (aka netxen?). The chip is NX3031 which should be Ubuntu-certified ([COLOR="blue"][see_here]("http://www.ubuntu.com/certification/catalog/component/pci:0100:4040-NETWORK")[/COLOR]) - at least more or less, since I'm not certain about the PCI domain number.

Both Servers are connected back-2-back via the Ethernet Card. I use CAT6 cabling and tried both streight and crossed cables. I started with used cables and ended up with brand new ones. All those attemps made no difference.

The Ethernet Card is recognized by the OS. All ports can be configured and show up in ifconfig and ip link output. 

Unfortunately it is not possible to configure ethernet-specific parameters like autonegotiaten or line speed with ethtool.

Moreover it isn't even possible to bring the link up. One control led is green and the other yellow. 

[INDENT][FONT="Courier New"]
jk@RAIDER:~$ lspci -D | grep NetXen
0000:0b:00.0 Ethernet controller: NetXen Incorporated NX3031 Multifunction 1/10-Gigabit Server Adapter (rev 42)
0000:0b:00.1 Ethernet controller: NetXen Incorporated NX3031 Multifunction 1/10-Gigabit Server Adapter (rev 42)
0000:0b:00.2 Ethernet controller: NetXen Incorporated NX3031 Multifunction 1/10-Gigabit Server Adapter (rev 42)
0000:0b:00.3 Ethernet controller: NetXen Incorporated NX3031 Multifunction 1/10-Gigabit Server Adapter (rev 42)

jk@RAIDER:~$ sudo lshw
...
        *-network:3
                description: Ethernet interface
                product: NX3031 Multifunction 1/10-Gigabit Server Adapter
                vendor: NetXen Incorporated
                physical id: 0.3
                bus info: pci@0000:0b:00.3
                logical name: eth7
                version: 42
                serial: 78:ac:c0:11:5b:7f
                size: 1GB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: msix pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=netxen_nic driverversion=4.0.50 duplex=full firmware=4.0.555 ip=172.20.7.2 latency=0 link=no multicast=yes port=twisted pair speed=1GB/s
                resources: irq:31 memory:fb800000-fb9fffff
...

jk@RAIDER:~$ ip link show eth7

9: eth7: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 78:ac:c0:11:5b:7f brd ff:ff:ff:ff:ff:ff

jk@RAIDER:~$ ifconfig eth7
eth7      Link encap:Ethernet  Hardware Adresse 78:ac:c0:11:5b:7f  
          inet Adresse:172.20.7.2  Bcast:172.20.7.3  Maske:255.255.255.252
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:95 

jk@RAIDER:~$ sudo ethtool -s eth7 autoneg off
Cannot set new settings: Input/output error
  not setting autoneg

jk@RAIDER:~$ dmesg | grep eth7
[   20.539064] eth7: could not cleanup lro flows
[   20.548039] netxen_nic 0000:0b:00.3: eth7: GbE port initialized
[   20.753540] ADDRCONF(NETDEV_UP): eth7: link is not ready
[ 7496.841204] ADDRCONF(NETDEV_UP): eth7: link is not ready


[/FONT]
[/INDENT]

I already wasted some hours by debugging. Neither QLOGIC nor the HP support pages are much of help. Also googling around didn't reveal anything substantial.

Does anyone have a clue if it is feasable to bring the ports of the QLOGIC Quad Port Ethernet Card up and running? Would it be reasonable to launch a bug report? 

Any help is appreciated.

Cheers

---

