---
title: "Bridging eth0, eth1 and OpenVPN"
date: 2013-08-24
forum: Networking &amp; Wireless
---

### Post by CraigHurlington on 2013-08-24
Hello,


I am attempting to bridge to ethernet connections on the same machine together so that a wireless router can be used at one end, and the other connecting to the internet through a vpn.


Right now I have tried adding


```
auto lo
iface lo inet loopback


iface eth0 inet manual


iface eth1 inet manual


auto br0
iface br0 inet dhcp
  bridge_ports eth0 eth1

```

to /etc/network/interfaces. Upon rebooting the machine a bridge is in place and functional with the host machine also having access to the internet. However neither eht0 or eth1 are showing up in the network manager, and I am uncertain as to how to add the VPN connection now that the bridge is in place.


Any advice is apprectiated.


Thank you.

---

