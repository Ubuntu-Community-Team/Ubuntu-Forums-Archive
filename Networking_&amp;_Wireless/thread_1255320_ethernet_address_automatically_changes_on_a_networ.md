---
title: "ethernet address automatically changes on a network interface"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by iiv on 2009-09-01
Every time when I boot my Ubuntu 9.04  ethernet address and the name of a network interface are changed (e.g. eth14 -> eth15 ...). What is the cause of that - NetworkManager or something else?

/etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

/etc/NetworkManager/nm-system-settings.conf:
```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


```

---

### Post by Iowan on 2009-09-01
Not necessarily Network Manager... I've seen this before in a couple of threads - [this]("http://ubuntuforums.org/showthread.php?p=7870196#post7870196") being the most recent.

---

