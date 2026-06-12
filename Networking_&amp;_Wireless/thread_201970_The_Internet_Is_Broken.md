---
title: "The Internet Is Broken"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by Princess_Tiswas on 2006-06-22
Ok - Not really.

But I am having DNS problems.

As root, I can ping both 66.102.9.104 and [www.google.com](www.google.com), but only the IP as user.

No browswers are able to resolve URLs, only IP addresses.

eth0 seems configured correctly, as /etc/resolv.conf has the correct nameserver (as is also defined in mye modem / router)

```
# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:30:1B:AF:44:89
          inet addr:192.168.1.30  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:265882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:96331010 (91.8 MiB)  TX bytes:21108918 (20.1 MiB)
          Interrupt:21 Base address:0xc000
```

Anything that I'm missing?

If it helps, the problems started after rejigging eth0 / resolv.conf to make use of a new modem router. Which didn't support pppoe. Which I then sold.

---

### Post by rbalfour on 2006-06-22
What is in your

/etc/network/interfaces
and
/etc/resolve.conf

---

### Post by Princess_Tiswas on 2006-06-22
/etc/resolv.conf
```
#nameserver 192.168.1.1
nameserver 212.23.6.100
```
/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface


iface eth0 inet static
address 192.168.1.30
netmask 255.255.255.0
gateway 192.168.1.1
```

---

