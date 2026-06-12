---
title: "IPTV multicast via Vlan - how to rset-up ?"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by its_johan on 2013-06-20
Hello all,
Help is appreciated

I would like to get the IPTV stream from my ISP working on my linux (ubuntu) computer via Vlan
I tried the following in /etc/network/interfaces
but no luck, no picture on VLC
Any ideas ?

```

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet manual
up ifconfig eth0 up

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet manual
up ifconfig eth2 up
  
auto vlan3
iface vlan3 inet manual
mtu 1500
vlan_raw_device eth1
route add -net 224.0.0.0 netmask 240.0.0.0 dev vlan3
up echo 0 > /sys/devices/virtual/net/vlan3/multicast_snooping
up ifconfig vlan3 up
```

---

### Post by its_johan on 2013-06-22
Nobody to help me ?  How can I set up Vlan3 to receive the IPTV stream ?

---

