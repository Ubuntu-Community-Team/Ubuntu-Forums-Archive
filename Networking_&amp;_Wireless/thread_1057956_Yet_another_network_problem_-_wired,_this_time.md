---
title: "Yet another network problem - wired, this time"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by Calmatory on 2009-02-02
Well, I can't get the connection working on my brothers machine.

The procedure to get the NIC working goes as follows:

```

add required rows to /etc/network/interfaces - "auto eth0" and "iface eth0 inet dhcp" 
modprobe ne2k_pci (if not loaded already)
ifup eth0

```

That has got it working twice before. Now after I took the machine off my shelf and installed fresh Feisty, it does not seem to work for some reason.

sudo ifup eth0 returns something like this
```

...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67
send_packet: Network is down
...

``` 

And that is being repeated good few times, obviously it fails.

* "auto eth0" and "iface eth0 inet dhcp" have been added to /etc/network/interfaces
* ifconfig does not show eth0. ifconfig -a does show eth0.
* rmmodding ne2k_pci and then modprobing it again wont help.
* Rebooting or changing the PCI slot wont help.
* ne2k_pci is already loaded at boot.

---

### Post by Calmatory on 2009-02-02
Anyone? Been fighting with this all day with zero success. :(

---

### Post by Calmatory on 2009-02-05
... anyone?

---

### Post by konqueror7 on 2009-02-05
is your connection through a router? try to make your ip static with the same details on your dhcp settings...

---

### Post by Iowan on 2009-02-05
**lshw -C network** should give information as to what driver is used, and whether card is aliased as eth0... among other things.

---

