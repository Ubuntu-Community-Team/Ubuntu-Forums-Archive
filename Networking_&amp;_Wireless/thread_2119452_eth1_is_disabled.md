---
title: "eth1 is disabled"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by TwinkE on 2013-02-23
I have a Gigabyte G1.Sniper 3 with onboard intel(eth0) and killer nic(eth1)'s (e1000e and alx drivers).  I patched the killer nic driver from this [post]("http://ubuntuforums.org/showthread.php?t=2008332&highlight=killer+nic") and I was able to get it to show up in ifconfig with it's own IP.  

I was working on bonding the two with 802.3ad into my managed switch and was able to see the info in the /proc/net/bonding/bond0 indicating that the switch liked the bond.  I was then having issues pinging inside my network so I started hacking up the /etc/network/interfaces file and lost it all.

Currently the lshw -C network shows the eth1(alx driver) as disabled and it has the same MAC as the eth0(e1000e driver).  I briefly had all eth's ip'd after a "udevadm trigger; service udev reload" and reboot, but the MAC's were still the same.

Any ideas on how to get eth1 behaving properly again?

lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 90:2b:34:58:4b:25
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=0.13-4 ip=192.168.49.226 latency=0 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:48 memory:f7e00000-f7e1ffff memory:f7e39000-f7e39fff ioport:f080(size=32)
  *-network
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 74:e5:43:d3:55:19
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-23-generic firmware=N/A ip=192.168.49.17 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:f7b00000-f7b7ffff memory:f7b80000-f7b8ffff
  *-network DISABLED
       description: Ethernet interface
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: rename3
       version: 10
       serial: 90:2b:34:58:4b:25
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full firmware=alx latency=0 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:49 memory:f7900000-f793ffff ioport:c000(size=128)
```

dmesg | grep -e ath -e Atheros -e alx
```
[   10.735187] Qualcomm Atheros(R) AR813x/AR815x/AR816x PCI-E Ethernet Network Driver
[   10.735226] alx 0000:0a:00.0: DMA to 64-BIT addresses
[   10.735262] alx 0000:0a:00.0: (unregistered net_device): HW Flags = 0x415
[   10.735671] alx 0000:0a:00.0: (unregistered net_device): reset PHY, pws = 1, az = 0, ptp = 0
[   10.736845] alx 0000:0a:00.0: (unregistered net_device): speed = 0x2f, autoneg = 1
[   10.737865] alx 0000:0a:00.0: irq 49 for MSI/MSI-X
[   10.737967] alx: Atheros Gigabit Network Connection
[   13.857724] ath: EEPROM regdomain: 0x6a
[   13.857725] ath: EEPROM indicates we should expect a direct regpair map
[   13.857727] ath: Country alpha2 being used: 00
[   13.857728] ath: Regpair used: 0x6a
[   13.859866] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.860018] Registered led device: ath9k-phy0
[   13.860022] ieee80211 phy0: Atheros AR9462 Rev:2 mem=0xf8b00000, irq=18

```

cat /etc/udev/rules.d/70-persistent-net.rules
```
# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.6/0000:0a:00.0 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="90:2b:34:58:4b:25", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.2/0000:07:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="74:e5:43:d3:55:19", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="90:2b:34:58:4b:25", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```

Unbonded /etc/network/interfaces:
```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.168.49.16
	netmask 255.255.255.0
	network 192.168.49.0
	broadcast 192.168.49.255
	gateway 192.168.49.1

auto wlan0
iface wlan0 inet static
	address 192.168.49.17
	netmask 255.255.255.0
	network 192.168.49.0
	broadcast 192.168.49.255
	gateway 192.168.49.1

```

Bonded /etc/network/interfaces:
```
auto lo
iface lo inet loopback

# The primary network interface
#bond0
auto eth0
iface eth0 inet manual
bond-master bond0
auto eth1
iface eth1 inet manual
bond-master bond0

auto bond0
iface bond0 inet static
	address 192.168.49.15
	netmask 255.255.255.0
	network 192.168.49.0
	broadcast 192.168.49.255
	gateway 192.168.49.1
bond-mode 802.3ad
bond-miimon 100
bond-slaves none
bond-lacp-rate 1

auto wlan0
iface wlan0 inet static
	address 192.168.49.17
	netmask 255.255.255.0
	network 192.168.49.0
	broadcast 192.168.49.255
	gateway 192.168.49.1

```

---

