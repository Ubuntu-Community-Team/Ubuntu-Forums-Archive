---
title: "wireless is sometimes eth1, sometimes eth2"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by Zed on 2006-06-08
This /etc/network/interfaces worked in Breezy, when I was using ndiswrapper with my LinkSys WMP54GS PCI card in a desktop machine.

```

auto lo
iface lo inet loopback
iface eth1 inet dhcp
wireless-essid my_essid
auto eth1

```

 In Dapper, I'm using broadcom43xxx, but the above works only sometimes, because sometimes on boot the interface is named eth2 instead of eth1.

How can I configure my wireless card automatically without knowing what the physical interface name will be?

---

### Post by Ivan Matveich on 2006-06-08
You can use /etc/iftab to assign a unique name to each interface, like

```

joey mac 00:e0:18:ee:7e:e3
billy mac 00:14:a5:04:c9:99

```

---

### Post by Zed on 2006-06-09
Thanks -- that worked a treat.

---

