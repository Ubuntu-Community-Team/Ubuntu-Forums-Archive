---
title: "OpenVPN eth0: received packet with own address as source address"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by Shark36 on 2011-12-04
Hi!

I'm trying to set up OpenVPN server on Ubuntu Server **10.04**. OpenVPN server starts up, but I noticed that **/var/log/syslog** is now filled with a lot of repetitive warnings:

```

...
Dec  4 20:47:55 server kernel: [ 3827.696802] eth0: received packet with own address as source address
Dec  4 20:47:55 server kernel: [ 3827.696973] eth0: received packet with own address as source address
Dec  4 20:47:55 server kernel: [ 3827.697149] eth0: received packet with own address as source address
Dec  4 20:47:56 server kernel: [ 3828.697710] eth0: received packet with own address as source address
Dec  4 20:47:56 server kernel: [ 3828.698168] eth0: received packet with own address as source address
Dec  4 20:47:56 server kernel: [ 3828.698338] eth0: received packet with own address as source address
Dec  4 20:47:56 server kernel: [ 3828.698494] eth0: received packet with own address as source address
...

```I Googled and searched through this forum, but couldn't find an answer to my problem.

If it makes any difference, I'm running Ubuntu server inside **VMware Server 1.0.x**.

And here is my configuration **/etc/network/interfaces**:
```

# The loopback network interface
auto lo br0
iface lo inet loopback

# OpenVPN bridge
iface br0 inet static
  address 192.168.0.16
  netmask 255.255.255.0
  gateway 192.168.0.1
  bridge_ports eth0
  bridge_fd 9      ## from the libvirt docs (forward delay time)
  bridge_hello 2   ## from the libvirt docs (hello time)
  bridge_maxage 12 ## from the libvirt docs (maximum message age)
  bridge_stp off   ## from the libvirt docs (spanning tree protocol)

iface eth0 inet manual
  up ip link set $IFACE up promisc on
  down ip link set $IFACE down promisc off

```Thanks!

---

