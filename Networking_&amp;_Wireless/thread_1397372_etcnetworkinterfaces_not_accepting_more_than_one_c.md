---
title: "/etc/network/interfaces not accepting more than one config per interface"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by talvik on 2010-02-03
My old /etc/network/interfaces isn't working in 9.10. I've used it from 8.04 to 9.04 without issues.

I need to make multiple configuration per interface:
```

auto lo
iface lo inet loopback

auto lo:1
iface lo:1 inet static
address 192.168.1.10
netmask 255.255.255.0

auto eth0
iface eth0 inet dhcp

auto eth0:1
iface eth0:1 inet static
	address 192.168.1.10
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.254

```

I still can configure the interfaces manually:
```
ifconfig lo:1 192.168.1.10 netmask 255.255.255.0 up
```

Is there a way to fix this? If not how can I downgrade the program responsible for reading this file?

Thanks

---

### Post by talvik on 2010-02-03
And does anyone if this is working on server edition?

This is really useful for me. Is it common to do this?

---

### Post by Iowan on 2010-02-03
I'm not sure you should alias "lo" - and assigning two interfaces to the same address (192.168.1.10) also seems like trouble. If the two eth0 aliases are in the same subnet, the gateway statement may cause problems...

---

