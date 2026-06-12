---
title: "Help getting interfaces up"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by knichel on 2010-08-20
I have a box that sits between my LAN and the Internet.  I have ip _forward'ing on and my iptables rules should be fine.  I recently did a fresh install of 10.04 and copied the /etc/network/interfaces file(from prev install) to my new install  and when I reboot, only eth1 comes up.

eth0 : inside LAN adapter
eth1 : outside Internet adapter

/etc/network/interfaces :
```

auto lo eth1
iface lo inet loopback
        address 127.0.0.1
        netmask 255.0.0.0

iface eth0 inet static
        address 192.168.6.200
        netmask 255.255.255.0
        broadcast 192.168.6.255
        network 192.168.6.0
        gateway ip.of.my.provider
        pre-up iptables-restore < /etc/iptables.up.rules

```

I appreciate any help.

JuJuBee

---

### Post by Naitsirhc Hsem on 2010-08-20
try ```
ifconfig -a
``` and ```
ifconfig eth0 up
```

---

### Post by Iowan on 2010-09-02
You might add eth0 to the "auto" line in /etc/network/interfaces.

---

