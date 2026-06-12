---
title: "my network config"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by zeezam on 2009-02-24
Here is my network conf
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 172.16.0.98
netmask 255.255.0.0
gateway 172.16.1.3

auto eth0

up route add -net 172.17.0.0 gw 172.16.5.3 netmask 255.255.0.0
up route add -net 172.18.0.0 gw 172.16.17.3 netmask 255.255.0.0

```

When I try to restart my network (first realized this when I edited my network conf and wanted to restart).
```

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:11: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:11: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                    [fail]


```

What is wrong here?
I also having problem when booting my computer.
It stops on configuring network and nfs common files. It stays there for about 10-15min. After that it boots fine.

---

### Post by mpokrywka on 2009-02-24
Isn't "/etc/network/interfaces:11: misplaced option" enough?

To read more about correct "/etc/network/interfaces" file syntax use: **man interfaces**

Quick fix: move "auto eth0" above "iface eth0 inet static"

---

### Post by zeezam on 2009-02-25
> **mpokrywka said:**
> Isn't "/etc/network/interfaces:11: misplaced option" enough?

To read more about correct "/etc/network/interfaces" file syntax use: **man interfaces**

Quick fix: move "auto eth0" above "iface eth0 inet static"

Yes!

Here is the output when restarting network after moved "auto eth0" above "iface eth0 inet static";

```

* Reconfiguring network interfaces...                                           * if-up.d/mountnfs[eth0]: waiting for interface lo before doing NFS mounts
SIOCADDRT: File exists
SIOCADDRT: File exists
SIOCADDRT: File exists
run-parts: /etc/network/if-up.d/static-routes exited with return code 7
                                                                         [ OK ]

```

---

