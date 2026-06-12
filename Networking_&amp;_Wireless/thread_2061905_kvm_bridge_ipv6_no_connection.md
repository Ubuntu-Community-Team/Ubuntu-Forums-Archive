---
title: "kvm bridge ipv6 no connection"
date: 2012-09-23
forum: Networking &amp; Wireless
---

### Post by pbrille on 2012-09-23
Hi @all

I'm running a server with precise pangolin 12.04 LTS and kvm 1.0+noroms-0ubuntu13. Bridges are being used for networking:

BTW: I'm not telling my real IP-addresses.

brext for external connections.
brsrv00X for virtual machine X.

For paket filtering I use shorewall(6) 4.5.7.1.

The problem actually is, that ipv6 traffic is not being forwarded through the bridges to the virtual machines. Sometimes it works, sometimes it doesn't. It seems to be happening quite randomly.

Here are some more details about my setup:

/etc/network/interfaces

```
auto  brext
iface brext inet static
  address   1.2.3.45
  netmask   255.255.255.255
  gateway   1.2.3.33
  pointopoint 1.2.3.33
  bridge_ports eth0
  bridge_stp off
iface brext inet6 static
  address a:b:c:1::2
  netmask 64
  up ip -6 route add a:b:c:d::1 dev brext
  down ip -6 route del a:b:c:d::1 dev brext
  up ip -6 route add default via a:b:c:d::1 dev brext
  down ip -6 route del default via a:b:c:d::1 dev brext
auto brsrv003
iface brsrv003 inet static
  address 1.2.3.45
  netmask 255.255.255.255
  bridge_ports none
  bridge_stp off
  bridge_fd 0
  up ip route add 1.2.3.58/32 dev brsrv003
  down ip route del 1.2.3.58/32 dev brsrv003
iface brsrv003 inet6 static
  address 1a:2b:3c:4d:1::1
  netmask 80

```
ip -6 neigh show gets only a link local address
fe80::5054:fff:fe2c:5c32 dev brsrv003 lladdr 52:54:00:2c:5d:32 STALE

When I try to ping6 this link local address I get:
ping6 fe80::5054:fff:fe2c:5c32
connect: Invalid argument

When I ping6 srv003 (1a:2b:3c:4d:1::3) from the host computer I get:
ping: sendmsg: Network is down

ip -6 route show:
```
1a:2b:3c:4d:1::/80 dev brsrv003  proto kernel  metric 256

```
What else do you need for information in order to help me?

---

