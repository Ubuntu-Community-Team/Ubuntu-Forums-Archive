---
title: "openconnect wrong route"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by pico on 2011-11-22
Hi!
I'm using openconnect to connect to my company FW (Cisco)
OS: Ubuntu 11.11 on x86
I have installed (packages):
openconnect
network-manager-openconnect

The connection is thrue a Proxy (with authentication) but I'm using cntml and the connection works fine.

Unfortunately the routing table seems to be completely wrong and I cannot reach no IP on the remote LAN.

After connection is made, the routing is:

[HTML]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         *               0.0.0.0         U     0      0        0 tun0
10.0.0.0        *               255.0.0.0       U     0      0        0 tun0
10.zzz.xxx.yyy    *               255.255.255.0   U     1      0        0 eth0
localhost       10.254.222.254  255.255.255.255 UGH   0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0[/HTML]

On a Windows machine (Windows XP) on the same LAN I can connect via AnyConnect and, after connection the routing  table is:


===========================================================================

[HTML]Active Routes:

Network Destination        Netmask          Gateway       Interface  Metric

          0.0.0.0          0.0.0.0         10.0.0.1       10.5.44.5       1

         10.0.0.0        255.0.0.0        10.5.44.5       10.5.44.5       1

        10.5.44.5  255.255.255.255        127.0.0.1       127.0.0.1       1

   10.254.210.189  255.255.255.255   10.254.230.254   10.254.230.26       1

     10.254.230.0    255.255.255.0    10.254.230.26   10.254.230.26       20

     10.254.230.0    255.255.255.0         10.0.0.1       10.5.44.5       1

    10.254.230.26  255.255.255.255        127.0.0.1       127.0.0.1       20

   10.255.255.255  255.255.255.255        10.5.44.5       10.5.44.5       1

   10.255.255.255  255.255.255.255    10.254.230.26   10.254.230.26       20
.....[/HTML]

And from my point of view the routing table on linux seems to be wrong....
Any suggestions ??

Regards

PiCo

---

