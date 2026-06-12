---
title: "Messed up my /etc/network/interfaces!!!"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by bluet0oth on 2010-05-24
I'm trying to setup my interfaces along side GNS3 for study purposes, and came across a youtube vid saying to try this (my current config)
*****************************************
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet static
#address ***.***.***.***
#netmask ***.***.***.***
#gateway ***.***.***.***

auto br0
iface br0 inet static
 address ***.***.***.***
 netmask ***.***.***.***
 gateway ***.***.***.***

pre-up tunctl -u root -t tap0
pre-up ifconfig eth0 0.0.0.0 promisc up
pre-up ifconfig tap0 0.0.0.0 promisc up
pre-up brctl addbr br0
pre-up brctl addif br0 eth0
pre-up brctl addif br0 tap0
post-down tunctl -d tap0
post-down brctl delbr br0

allow-hotplug eth0
iface eth0 inet manual
pre-up ifconfig eth0 0.0.0.0 promisc up
pre-up brctl addif br0 eth0
pre-down brctl delif br0 eth0
pre-down ifconfig eth0 down
**************************************************

and now I've lost all network access
upon - sudo /etc/init.d/networking restart
   * Reconfiguring network interfaces...
/bin/sh: tunctl: not found
Failed to bring up br0.

I'm praying for some crappy syntax error, also in Network Connections... its now blank, the original auto eth0 setup is missing

---

### Post by Iowan on 2010-05-24
The Auto eth0 is probably missing due to the eth0 definition in */etc/network/interfaces* The quick/dirty fix would be to rename (or copy) the file and build another with the original name (or edit this one) containing only: ```
auto lo
iface lo inet loopback
``` If that works - you can rename back and forth to try out your own configuration.

---

