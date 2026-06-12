---
title: "Bridging My home server"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by DJJo on 2009-11-14
Hi
My home server got 2 network interfaces. eth0 and eth2.
Because all traffic goes over one interface.
So i want to bridge my network interfaces.
A firewall wil not be necessary, because i got a line parallel.
My server got a static address, i tested with a other computer but it won't boot up.

here is a schematic. 
```

+===========+                           +===========+
| Computers |                           | Computers |
+===========+                           +===========+
      | 1gb/s                                 |
+==========+              100mb/s             |100mb/s/WIFI
| switch   |-----------------------------+    |
+=====+====+                             |    |
      |         eth2      eth0           |    |
      | 1gb/s   +============+ 100mb/s +==========+
      +---------| Homeserver |---------|  Router  |-- Internet
                +============+         +==========+

```This is what i got so far:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto eth2
iface eth2 inet manual

# br0
auto br0
iface br0 inet static
   address 192.168.2.252
   netmask 255.255.255.0
   gateway 192.168.2.254
   network 192.168.2.0
   broadcast 192.168.2.255
   bridge_ports eth0 eth2

auto br0:1
iface br0:1 inet static
   address 192.168.2.251
   netmask 255.255.255.0
   gateway 192.168.2.254
   network 192.168.2.0
   broadcast 192.168.2.255

```
I hope i make my myself clear?
Will this work? and will this good boot up?

---

### Post by DJJo on 2009-11-14
no buddy?

---

### Post by t0mppa on 2009-11-14
If you already have a cable going from your switch to your router, why do you want to bridge the interfaces on the server? It won't speed anything up, even if you have two routes from the switch to the router.

---

