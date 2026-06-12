---
title: "Connection issues with Ubuntu Server 10.10"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by wasteland131 on 2010-11-04
**EDIT:** The problem has solved itself. Threatening the server with a hammer worked. :P
But seriously, restarting the router yet again, I tried DHCP again and now it worked and connectivity was restored.


Hi,

I've scoured the forum for a few days now and I can't figure out what I did wrong.

I've set up a new Ubuntu 10.10 server on an Acer Aspire H340 and am having trouble with setting up the network. The machine worked flawlessly with Ubuntu 8.10 Server for more than a year, but I decided that an upgrade was in order.
Foolish me. :(

I have a number of machines connected to a router at 192.168.178.1. None but the new server have problems with connecting via DHCP. The new server did not accept DHCP leases from the router. That problem did not exist with the 8.10 server.
To work around that problem in 10.10, I configured the server with a static IP like this:

/etc/network/interfaces
```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.178.201
    netmask 255.255.255.0
    network 192.168.178.0
    broadcast 192.168.178.255
    gateway 192.168.178.1
```While my router has a DHCP server, it only assigns IP addresses up to 192.168.178.200, so the address set is outside of the range controlled by the DHCP server.
Also, the router can "see" the server in that the server appears in the list of attaches machines.

Since the server is headless, I have set up a script to run upon reboot (@reboot cron job) to give me some information on the problem.

ifconfig eth0 shows:
```
eth0      Link encap:Ethernet  HWaddr 00:26:2d:00:ff:19
          inet addr:192.168.178.201  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:fe00:ff19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:195 (195.0 B)  TX bytes:354 (354.0 B)
          Interrupt:16

```The route is set as
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.178.0   *               255.255.255.0   U     0      0        0 eth0
default         192.168.178.1   0.0.0.0         UG    100    0        0 eth0
```My other machines have similar IP addresses and the same Bcast and Mask and route.

mii-Tool shows:
```
eth0: negotiated 1000baseT-HD flow-control, link ok
```/etc/resolv.conf contains
```
domain fritz.box
search fritz.box
nameserver 192.168.178.1
```/usr/bin/lshw -C network shows
```
  *-network
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 16
       serial: 00:26:2d:00:ff:19
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.178.201 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:31 memory:f0300000-f0303fff ioport:2000(size=256) memory:81000000-8101ffff(prefetchable)
```The firewall on the server is configured as follows:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```From what I understand, all that should be well... but when I try to ping the router from the server, this is the result:
```
PING 192.168.178.1 (192.168.178.1) 56(84) bytes of data.

--- 192.168.178.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms
```I can ping the router from all other machines.
I also can not ping the server from any other machine.


I'd be grateful for any input on how to resolve this issue. If I can provide more information, just let me know what is needed.
Thank you in advance.

---

