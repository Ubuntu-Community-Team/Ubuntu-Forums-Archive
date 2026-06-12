---
title: "Broadcom BCM5761e on Latitude 13 + Ubuntu 10.04 = not working"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by yang on 2010-08-25
Just installed Ubuntu 10.04 on a Dell Latitude 13 which originally had 9.10 working fine.  This has:

[LIST]
[*]BCM5761e Ethernet
[*]BCM4312 Wifi
[/LIST]

Both were initially broken, but I managed to fix the Wifi by installing bcmwl-kernel-sources (getting apt to use the install USB was another ordeal).

Now, BCM5761e is still not working.  DHCP requests always fail (and the DHCP server & network work).  Google isn't as helpful for this one.  Any hints?

More details follow.

```

$ lspci -vvnn
...
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe [14e4:1680] (rev 10)
	Subsystem: Dell Device [1028:0432]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 30
	Region 0: Memory at f65e0000 (64-bit, non-prefetchable) [size=64K]
	Region 2: Memory at f65f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth2
       version: 01
       serial: c4:17:fe:dc:21:50
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.0.0.160 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5761e Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 10
       serial: 00:26:b9:68:c6:94
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5761e-v3.73 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:f65e0000-f65effff memory:f65f0000-f65fffff

$ uname -a 
Linux fl 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux

$ tail -f -n 0 /var/log/syslog # plugging in network card now
Aug 25 12:17:50 fl NetworkManager: <info>  (eth1): carrier now ON (device state 2)
Aug 25 12:17:50 fl kernel: [ 2538.209095] tg3: eth1: Link is up at 100 Mbps, full duplex.
Aug 25 12:17:50 fl kernel: [ 2538.209100] tg3: eth1: Flow control is on for TX and on for RX.
Aug 25 12:17:50 fl kernel: [ 2538.209555] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 25 12:17:50 fl NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
Aug 25 12:17:50 fl NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Aug 25 12:17:50 fl NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Aug 25 12:17:50 fl NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Aug 25 12:17:50 fl NetworkManager: <info>  dhclient started with pid 2273
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Aug 25 12:17:50 fl NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 25 12:17:50 fl dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 25 12:17:50 fl dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 25 12:17:50 fl dhclient: All rights reserved.
Aug 25 12:17:50 fl dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 25 12:17:50 fl dhclient: 
Aug 25 12:17:50 fl NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
Aug 25 12:17:50 fl dhclient: Listening on LPF/eth1/00:26:b9:68:c6:94
Aug 25 12:17:50 fl dhclient: Sending on   LPF/eth1/00:26:b9:68:c6:94
Aug 25 12:17:50 fl dhclient: Sending on   Socket/fallback
Aug 25 12:17:51 fl avahi-daemon[723]: Registering new address record for fe80::226:b9ff:fe68:c694 on eth1.*.
Aug 25 12:17:52 fl dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Aug 25 12:17:58 fl dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Aug 25 12:18:00 fl kernel: [ 2548.440056] eth1: no IPv6 routers present
Aug 25 12:18:05 fl dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Aug 25 12:18:20 fl dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
^C

$ dmesg # these are the new messages that appeared after plugging in
...
[ 2538.209095] tg3: eth1: Link is up at 100 Mbps, full duplex.
[ 2538.209100] tg3: eth1: Flow control is on for TX and on for RX.
[ 2538.209555] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 2548.440056] eth1: no IPv6 routers present

```

---

