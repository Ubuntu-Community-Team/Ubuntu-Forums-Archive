---
title: "Multiple Static IPv4 &amp; IPv6 Config Ubuntu server 12.04 LTS"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by WilcoWings on 2012-10-17
It took me a long time to find an example of a static ipv4 and ipv6 configuration with multiple addresses. It will not be perfect, but it works.

> #This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 62.212.73.138
        netmask 255.255.255.224
        network 62.212.73.128
        broadcast 62.212.73.159
        gateway 62.212.73.158
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 85.17.150.123 85.17.96.69 85.17.150.123 62.212.64.122
#       dns-search eu


auto eth0:0
iface eth0:0 inet static
        address 62.212.73.149
        netmask 255.255.255.224
        gateway 62.212.73.158

auto eth0:1
iface eth0:1 inet static
        address 62.212.73.150
        netmask 255.255.255.224
        gateway 62.212.73.158

auto eth0:2
iface eth0:2 inet static
        address 62.212.73.151
        netmask 255.255.255.224
        gateway 62.212.73.158

auto eth0:3
iface eth0:3 inet static
        address 62.212.73.152
        netmask 255.255.255.224
        gateway 62.212.73.158

iface eth0 inet6 static
        up /sbin/ifconfig eth0 inet6 add 2001:1af8:4010:a015:62:212:73:149/64
        up /sbin/ifconfig eth0 inet6 add 2001:1af8:4010:a015:62:212:73:150/64
        up /sbin/ifconfig eth0 inet6 add 2001:1af8:4010:a015:62:212:73:151/64
        up /sbin/ifconfig eth0 inet6 add 2001:1af8:4010:a015:62:212:73:152/64
        address 2001:1af8:4010:a015:62:212:73:138
        netmask 64
        gateway 2001:1af8:4010:a015::1
        dns-nameservers 2001:1af8:3100:1::10 2001:1af8:4100:2::10 2001:1af8:2100:1::10 2001:1af8:4300:1::11

---

