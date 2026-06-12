---
title: "Bonding with bridge not starting on boot"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by jmandawg on 2011-10-30
I'm trying to set up a bridge for kvm with a bonded adapter.  For some reason, it won't come when i boot, but if i do an:

```
ifdown br0
ifdown bond0

ifup bond0
ifup br0
```

Everything works fine.  

Here is the contents of /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto bond0
iface bond0 inet manual
 bond-slaves eth0 eth1
 bond_mode balance-alb
 bond_miimon 100

auto br0
iface br0 inet static
 bridge_ports bond0
 address 192.168.1.119
 gateway 192.168.1.1
 netmask 255.255.255.0
 bridge_fd 9
 bridge_hello 2
 bridge_maxage 12
 bridge_stp off

```

It's bad though because if i reboot remotely, i'm dead.


This is on 11.10 x64 server.

Thanks in advance

---

### Post by jmandawg on 2011-10-30
Here is what's in the kern.log from boot up. 

```
Oct 30 20:06:49 i72600K kernel: [   14.812410] EXT4-fs (sde4): mounted filesystem with ordered data mode. Opts: errors=remount-ro
Oct 30 20:06:49 i72600K kernel: [   14.821303] bonding: Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)
Oct 30 20:06:49 i72600K kernel: [   14.821305] bonding: Warning: either miimon or arp_interval and arp_ip_target module parameters must be specified, otherwise bonding will not detect link failures! see bonding.txt for details.
Oct 30 20:06:49 i72600K kernel: [   14.822979] bonding: bond0: Adding slave eth0.
Oct 30 20:06:49 i72600K kernel: [   14.826829] Bridge firewalling registered
Oct 30 20:06:49 i72600K kernel: [   14.967755] r8169 0000:0b:00.0: eth0: link down
Oct 30 20:06:49 i72600K kernel: [   14.969069] bonding: bond0: enslaving eth0 as an active interface with an up link.
Oct 30 20:06:49 i72600K kernel: [   14.970373] device bond0 entered promiscuous mode
Oct 30 20:06:49 i72600K kernel: [   14.971064] bonding: bond0: Adding slave eth1.
Oct 30 20:06:50 i72600K kernel: [   15.115644] r8169 0000:0d:00.0: eth1: link down
Oct 30 20:06:50 i72600K kernel: [   15.116227] device eth1 entered promiscuous mode
Oct 30 20:06:50 i72600K kernel: [   15.116911] bonding: bond0: enslaving eth1 as an active interface with an up link.
Oct 30 20:06:50 i72600K kernel: [   15.116973] device eth0 entered promiscuous mode
Oct 30 20:06:50 i72600K kernel: [   15.117342] bonding: bond0: Setting MII monitoring interval to 100.
Oct 30 20:06:50 i72600K kernel: [   15.117492] bonding: bond0: link status definitely down for interface eth0, disabling it
Oct 30 20:06:50 i72600K kernel: [   15.117496] bonding: bond0: now running without any active interface !
Oct 30 20:06:50 i72600K kernel: [   15.117497] bonding: bond0: link status definitely down for interface eth1, disabling it
Oct 30 20:06:50 i72600K kernel: [   15.119683] bonding: bond0: setting mode to balance-alb (6).
Oct 30 20:06:50 i72600K kernel: [   15.120507] ADDRCONF(NETDEV_UP): br0: link is not ready
Oct 30 20:06:50 i72600K kernel: [   15.127982] init: ssh main process (949) terminated with status 255
Oct 30 20:06:53 i72600K kernel: [   18.451098] r8169 0000:0b:00.0: eth0: link up
Oct 30 20:06:53 i72600K kernel: [   18.644160] r8169 0000:0d:00.0: eth1: link up

```

It looks like the bond drops the links before they are up.  Any suggestions?

---

