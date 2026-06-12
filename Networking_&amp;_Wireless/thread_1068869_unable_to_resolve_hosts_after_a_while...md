---
title: "unable to resolve hosts after a while.."
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by Spitphire on 2009-02-13
I'm having some strange network problems that just started up unexplained.  After a few hours my connection is able to ping ip addresses, but it can't resolve hostnames.

If I issue the following, everything goes back to normal:
```
sudo /etc/init.d/networking restart
```

Just getting annoying doing this every few hours.  I don't know what the problem is

route -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

ifconfig: (i edited the mac addr to post)
```

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe3d:d716/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7575108 (7.2 MB)  TX bytes:5935437 (5.6 MB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:319268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:645288046 (615.3 MB)  TX bytes:645288046 (615.3 MB)

```

/etc/network/interfaces:
```

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
       address 192.168.1.100
       netmask 255.255.255.0
       gateway 192.168.1.1

```

---

### Post by jonobr on 2009-02-13
Where are you doing your name resolution to?

If you can ping hosts (particularly the DNS server) then it doesnt sound networking related. It sounds more related to DNS availability,

You may be forced to do a wireshark trace to see whats happening.

IT could be something as simple as the DNS your talking to switches or loadbalances to another dns but you are still talking to the first one.

A trace would help out with that

---

### Post by Spitphire on 2009-02-15
> **jonobr said:**
> Where are you doing your name resolution to?

If you can ping hosts (particularly the DNS server) then it doesnt sound networking related. It sounds more related to DNS availability,

You may be forced to do a wireshark trace to see whats happening.

IT could be something as simple as the DNS your talking to switches or loadbalances to another dns but you are still talking to the first one.

A trace would help out with that


I'll have to wait until it crashes again in a few hours and see what's going on.  my etc/resolv.conf is setup as follows:

```

search localdomain
nameserver 192.168.1.1

```

I'm not actually sure how my router is supplying the dns info to the box... but it is?  Maybe I try putting some opendns servers in there and see what happens..

---

