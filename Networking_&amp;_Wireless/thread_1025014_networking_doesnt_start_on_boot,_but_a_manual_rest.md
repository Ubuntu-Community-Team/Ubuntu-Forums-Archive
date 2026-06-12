---
title: "networking doesnt start on boot, but a manual restart of service fixes problem"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by isaac_golding on 2008-12-29
So I&#7743; running with Intrepid and good ole cat 5.  DHCP is set as the default with my ip being assigned from the router.

On startup the machine&#347; networking appears to be in a non operational state.  However if I issue the command :

**sudo /etc/init.d/networking restart** brings eth0 up in its proper state and all is good in the world.

What I´d like to figure out is why this is happening as its annoying having to be physically at the machine to manually restart the network.  Any suggestions on where to look and what to look for would be greatly appreciated.

---

### Post by Iowan on 2008-12-29
It *should* start by itself, but check */etc/networking/interfaces* to verify the presence of an "auto eth0" line.

---

### Post by isaac_golding on 2009-01-01
I checked and this is the results
root@ubuntu-server:/etc/network# cat   /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

