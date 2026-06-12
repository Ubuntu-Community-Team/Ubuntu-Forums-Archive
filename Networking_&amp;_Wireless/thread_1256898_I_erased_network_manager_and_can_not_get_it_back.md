---
title: "I erased network manager and can not get it back"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by lizarraga on 2009-09-03
Hi everybody,
I use a wireless connection with ubuntu 9.04 which worked perfect (I always had the connection symbol on the top) but the other day I, by mistake, unistalled network manager program and i lost the connection, now I do not have the connection sysmbol. When I try to put it back now from add or remove programs, I can not do it since I do not have connection to internet. I can not do it either from Synaptic.
Can anybody help me to install Network manager again? Or solve my problem?
 
Thanks in advance.

---

### Post by slakkie on 2009-09-03
Please have a look at the interfaces file, man interfaces and setup your network via that file..

/etc/network/interfaces

eg
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# DHCP 
auto eth0
iface eth0 inet dhcp

# Static IP
auto eth2
iface eth2 inet static
        address 194.134.x.x
        netmask 255.255.255.0
        network 194.134.x.x
        broadcast 194.134.x.255
        gateway 194.134.x.x
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 194.134.5.5 194.134.0.97
        dns-domain opperschaap.net
        dns-search opperschaap.net euronet.nl wanadoo.nl online.nl

```

---

### Post by t0mppa on 2009-09-03
If you have a Ubuntu CD lying around, you can install it back from there, just have to add it to your source list, add the CD and remove the online repositories. Or then you can just connect to your AP manually (see [here]("http://ubuntuforums.org/showthread.php?t=571188")) and install Network Manager or some other GUI to handle the connection for you the usual way.

---

### Post by lizarraga on 2009-09-03
Hi there,
Thanks a lot for your help, I will try this afternoon.

---

