---
title: "eth0 unavailable after upgrade to 12.04"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by trumb1mj on 2013-04-25
Hey guys,

I recently upgraded to 12.04 LTS and have had some issues restoring network connectivity.  Here are some more details.

I've re-added the interface to /etc/network/interfaces:
```

auto eth0
iface eth0 inet dhcp

```

Then ran ifup eth0:
```

Ignoring unknown interface eth0=eth0.

```

etho does not show up in the ifconfig -a output at all.

Here is the output on my wireless and ethernet connections from lspci:
```

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

```

I'm convinced that once I can establish a connection through either ethernet or wireless I can update and things should just work but I'm fairly well stuck at this point.  Any help is greatly appreciated!

---

### Post by praseodym on 2013-04-25
Remove both "eth0" lines again and any profile in "cable" and "DSL" in the network-manager and reboot.

---

### Post by trumb1mj on 2013-04-25
> **praseodym said:**
> Remove both "eth0" lines again and any profile in "cable" and "DSL" in the network-manager and reboot.

There aren't any connections at all in the network manager.  I tried removing the new eth0 confs and restarting but it didn't work.  This has to be a driver issue, right?

---

### Post by praseodym on 2013-04-25
Please check:
```

uname -r
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/resolv.conf
cat /etc/network/interfaces
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

