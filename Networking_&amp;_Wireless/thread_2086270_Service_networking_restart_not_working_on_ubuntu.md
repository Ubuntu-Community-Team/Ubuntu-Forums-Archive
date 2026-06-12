---
title: "Service networking restart not working on ubuntu"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by onitlikesonic on 2012-11-20
This one has been cracking my head for quite a bit and I can't seem to find a decent answer for it, hoping you guys can shed some light to it...
```

# Loopback interface:
auto lo
iface lo inet loopback


# Ethernet 0 interface:
auto eth0
iface eth0 inet static
    address 10.10.20.100
    netmask 255.255.255.0
    network 10.10.20.0
    broadcast 10.10.20.255
    gateway 10.10.20.1
    dns-nameservers 10.10.20.1 8.8.8.8
    hwaddress ether XXXXXXXX
    dns-search defaultdomain


# Ethernet 1 interface:
auto eth1
iface eth1 inet static
    address 10.10.20.125
    netmask 255.255.255.0
    network 10.10.20.0
    broadcast 10.10.20.255
    gateway 10.10.20.1
    dns-nameservers 10.10.20.1 8.8.8.8
    hwaddress ether XXXXXX
    dns-search defaultdomain

```
When i reboot the machine i'm able to have the correct ip addresses

```
eth0      Link encap:Ethernet  HWaddr XXXXXXXXXXXXXX
          inet addr:10.10.20.100  Bcast:10.10.20.255  Mask:255.255.255.0
          inet6 addr: XXXXXXXXXXXXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1879 (1.8 KB)  TX bytes:398 (398.0 B)

eth1      Link encap:Ethernet  HWaddr XXXXXXXXXXXXXX
          inet addr:10.10.20.125  Bcast:10.10.20.255  Mask:255.255.255.0
          inet6 addr: XXXXXXXXXXXXXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8910 (8.9 KB)  TX bytes:8607 (8.6 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:35420 (35.4 KB)  TX bytes:35420 (35.4 KB)
```

However when I change anything on the networking file i can only get it to apply by doing a machine reboot at the moment (plain stupid workaround)

[LIST]
[*]service networking restart doesn't seem to do anything
[*]ifdown eth0 && ifup eth0 gives ifdown: interface eth0 not configured RTNETLINK answers: File exists Failed to bring up eth0.
[*]ip link set eth0 down && ip link set eth0 up doesn't seem to do anything
[/LIST]

How on earth do I make the network pickup the changes, seriously this is getting on my nerves...

I'm using ubuntu 12.04 virtualized using KVM inside an Ubuntu 12.04 Dom0

---

