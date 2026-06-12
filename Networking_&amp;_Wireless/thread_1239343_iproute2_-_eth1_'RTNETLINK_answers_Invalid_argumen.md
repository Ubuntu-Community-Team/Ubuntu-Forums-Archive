---
title: "iproute2 - eth1 'RTNETLINK answers: Invalid argument'"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by docawk on 2009-08-13
I just added another NIC to a machine that I want to connect to a different LAN area. Usually I never had problems setting up routing via iproute2 utilities.
The newly added NIC has eth1 assigned via udev (in boot process eth0 is assigned, but I need that interface name to be associated to the existing internet bound 100mBit line)

I am running Debian 'lenny' with kernel 2.6.30.3 (quite all network options compiled in).

Setting up the interface via /etc/network/interfaces
```

iface eth0 inet static
        address XXX.XXX.250.188
        netmask 255.255.255.248
        network XXX.XXX.250.184
        broadcast XXX.XXX.250.191
        gateway XXX.XXX.250.186

auto eth1
iface eth1 inet static
        address 192.168.11.11
        netmask 255.255.255.0
        network 192.168.11.0
        broadcast 192.168.11.255

```

works fine and shows in 'ip route' properly

XXX.XXX.250.184/29 dev eth0  proto kernel  scope link  src XXX.XXX.250.188
192.168.11.0/24 dev eth1  proto kernel  scope link  src 192.168.11.11
default via XXX.XXX.250.186 dev eth0

The way I want to act is introducing the default gateway on eth0 in the main routing table and set up a separate tabel for routing packets destinated to LAN.

```

/sbin/ip route flush table main
/sbin/ip route add XXX.XXX.250.186 dev eth0 src XXX.XXX.250.189
/sbin/ip route add 192.168.11.11 dev eth1 src 192.168.11.9
RTNETLINK answers: Invalid argument
/sbin/ip route add default via XXX.XXX.250.186 dev eth0
/sbin/ip route flush cache

```

So it seems to me to iproute2 eth1 is not valid. 
Anybody a suggestion?

Thanks

---

### Post by docawk on 2009-08-13
Problem solved. My fault.

wrong way to use ip route. Should add destination with source address on interface, not mixed up.

```

/sbin/ip route add XXX.XXX.250.184/29 dev eth0 src XXX.XXX.250.189
/sbin/ip route add 192.168.11.0/24 dev eth1 src 192.168.11.11
/sbin/ip route add default via XXX.XXX.250.186 dev eth0
/sbin/ip route flush cache

```

works fine;-)

Thanks anyways.

---

