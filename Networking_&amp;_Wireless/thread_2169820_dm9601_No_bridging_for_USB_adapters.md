---
title: "dm9601: No bridging for USB adapters?"
date: 2013-08-23
forum: Networking &amp; Wireless
---

### Post by fo0 on 2013-08-23
Hi,

I bought a USB network adapter which uses the *dm9601* kernel module. It does work as expected in normal use.
Today, I tried to bridge my built-in (PCI) adapter (eth0) and my USB adapter (eth1). I disabled NetworkManager and used the following */etc/network/interfaces*:
```

auto lo
iface lo inet loopback

iface br0 inet dhcp
	bridge_ports eth0 eth1

```

The machine with the two adapters can successfully get a DHCP lease (DHCP server is somewhere behind eth0). However all clients behind eth1 are unable to communicate in any way. They can not get any DHCP response, cannot ping the gateway nor the "bridge machine".

Is bridging not possible with this USB adapter?

Thank you for you response!

---

