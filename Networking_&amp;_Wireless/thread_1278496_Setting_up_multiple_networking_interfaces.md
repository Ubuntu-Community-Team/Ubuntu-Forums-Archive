---
title: "Setting up multiple networking interfaces"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by cyrusthevirus on 2009-09-29
I'm running into issues when I set up multiple networking interfaces. I have 2 interfaces one a public IP and the other one a private one. I  set them up as shown below in the /etc/networking/interfaces.

```

# The loopback network interface
auto lo
iface lo inet loopback

# The PUBLIC primary network interface
auto eth0
iface eth0 inet static
address 199.x.x.x
netmask 255.255.255.0
gateway 199.x.x.x

# The PRIVATE second network interface
auto eth1
iface eth1 inet static
address 192.168.x.x
netmask 255.255.255.0
gateway 192.168.x.x

```The issue is, when both ethernet cables are plugged in, I'm unable to connect to the server through the Public network. When I unplug the second(PRIVATE) network, I'm able to connect. Is there something wrong with my configuration? Thanks.

---

### Post by Iowan on 2009-09-29
Might be an issue with gateway settings - what is shown in **route -n** - both with and without eth1.

---

### Post by cyrusthevirus on 2009-09-29
here's route -n with eth1:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
199.x.x.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.x.x.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.x.x.1   0.0.0.0         UG    100    0        0 eth1
0.0.0.0         199.x.x.1    0.0.0.0         UG    100    0        0 eth0

```and without eth1:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
199.x.x.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         199.x.x.1    0.0.0.0         UG    100    0        0 eth0

```Thanks again for your help.

> **Iowan said:**
> Might be an issue with gateway settings - what is shown in **route -n** - both with and without eth1.

---

### Post by cyrusthevirus on 2009-10-01
Can someone please help me with this?

> **cyrusthevirus said:**
> I'm running into issues when I set up multiple networking interfaces. I have 2 interfaces one a public IP and the other one a private one. I  set them up as shown below in the /etc/networking/interfaces.

```

# The loopback network interface
auto lo
iface lo inet loopback

# The PUBLIC primary network interface
auto eth0
iface eth0 inet static
address 199.x.x.x
netmask 255.255.255.0
gateway 199.x.x.x

# The PRIVATE second network interface
auto eth1
iface eth1 inet static
address 192.168.x.x
netmask 255.255.255.0
gateway 192.168.x.x

```The issue is, when both ethernet cables are plugged in, I'm unable to connect to the server through the Public network. When I unplug the second(PRIVATE) network, I'm able to connect. Is there something wrong with my configuration? Thanks.

---

### Post by Iowan on 2009-10-01
Try commenting out the gateway setting for eth1, and restart networking 
(**sudo /etc/init.d/networking restart**)

---

### Post by cyrusthevirus on 2009-10-20
Just wanted to say thanks. Commenting out the second gateway worked.

> **Iowan said:**
> Try commenting out the gateway setting for eth1, and restart networking 
(**sudo /etc/init.d/networking restart**)

---

