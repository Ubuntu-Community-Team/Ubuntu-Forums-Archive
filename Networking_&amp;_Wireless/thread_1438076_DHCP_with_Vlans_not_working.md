---
title: "DHCP with Vlans not working"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by dvlabguy on 2010-03-24
I'm trying to setup a DHCP server with Vlan sub-interfaces and having trouble with DHCP not giving out addresses. I see the bootp requests come into ETH3 (10.77.50.1), but not making it back down to the router port where it's connected to.
 
Network scenario...
 
Ubuntu DHCP Server ETH3 (10.77.50.1) - ETH3.500 (10.115.50.1) --- Router port L3 int (10.77.50.2) to an L2 vlan 500 --- Client requesting DHCP via bootp on Vlan 500.
 
I've proven that the router works as designed from it's dubug filters of RX error code 3, which means ICMP from the server is not making it back down to the router port.
 
I'm at the point of offering a cash reward here :D
 
See complete Ubuntu configs below.
 
root@ubuntu:~# cat /etc/dhcp3/dhcpd.conf
subnet 10.115.50.0 netmask 255.255.255.240 {
option subnet-mask 255.255.255.240;
option domain-name-servers 10.15.12.100;
option domain-name aaa.bbb.com;
option routers 10.115.50.1;
option broadcast-address 10.115.50.15;
default-lease-time 600;
max-lease-time 7200;
option ip-forwarding on;
range dynamic-bootp 10.115.50.2 10.115.50.14; }
!
!
root@ubuntu:~# ifconfig
eth0 Link encap:Ethernet HWaddr 00:19:b9:30:60:03
inet addr:10.15.12.11 Bcast:10.15.12.255 Mask:255.255.255.0
inet6 addr: fe80::219:b9ff:fe30:6003/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:79397 errors:0 dropped:0 overruns:0 frame:0
TX packets:1208 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:5363851 (5.3 MB) TX bytes:199057 (199.0 KB)
Interrupt:16
eth3 Link encap:Ethernet HWaddr 00:13:46:72:41:c6
inet addr:10.77.50.1 Bcast:10.77.50.255 Mask:255.255.255.0
inet6 addr: fe80::213:46ff:fe72:41c6/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2178 (2.1 KB) TX bytes:33517 (33.5 KB)
Interrupt:18
eth3.500 Link encap:Ethernet HWaddr 00:13:46:72:41:c6
inet addr:10.115.50.1 Bcast:10.115.50.15 Mask:255.255.255.240
inet6 addr: fe80::213:46ff:fe72:41c6/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:127 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:22311 (22.3 KB)
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:190 errors:0 dropped:0 overruns:0 frame:0
TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:19854 (19.8 KB) TX bytes:19854 (19.8 KB)
!
!
root@ubuntu:~# cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 10.15.12.11
netmask 255.255.255.0
network 10.15.12.0
broadcast 10.15.12.255
gateway 10.15.12.1
ifup /sbin/route add -net 10.15.12.0 netmask 255.255.255.0 gw 10.15.12.1 dev eth0
# Secondary interface via Router 10.77.50.2 for DHCP
auto eth3
iface eth3 inet static
address 10.77.50.1
netmask 255.255.255.0
network 10.77.50.0
broadcast 10.77.50.255
gateway 10.77.50.1
ifup /sbin/route add -net 10.77.50.0 netmask 255.255.255.0 gw 10.77.50.1 dev eth3
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth3.500 (for vlan500)
iface eth3.500 inet static
address 10.115.50.1
netmask 255.255.255.240
network 10.115.50.0
broadcast 10.115.50.15
mtu 1500
vlan_raw_device eth3
!
!
root@ubuntu:~# netstat -nr
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
10.15.12.11 0.0.0.0 255.255.255.255 UH 0 0 0 eth0
10.115.50.0 0.0.0.0 255.255.255.240 U 0 0 0 eth3.500
10.15.12.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
10.77.50.0 0.0.0.0 255.255.255.0 U 0 0 0 eth3
169.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0
0.0.0.0 10.15.12.1 0.0.0.0 UG 0 0 0 eth0
0.0.0.0 10.77.50.1 0.0.0.0 UG 0 0 0 eth3
0.0.0.0 10.15.12.1 0.0.0.0 UG 0 0 0 eth0
!
!
root@ubuntu:/etc# cat modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
loop
lp
8021q
!
!
root@ubuntu:~# iptables -L -v
Chain INPUT (policy ACCEPT 7924 packets, 869K bytes)
pkts bytes target prot opt in out source destination 
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
pkts bytes target prot opt in out source destination 
Chain OUTPUT (policy ACCEPT 4563 packets, 643K bytes)
pkts bytes target prot opt in out source destination
!
!
root@ubuntu:~# ping 10.77.50.2 (Router ip int)
PING 10.77.50.2 (10.77.50.2) 56(84) bytes of data.
64 bytes from 10.77.50.2: icmp_seq=1 ttl=64 time=3.74 ms
64 bytes from 10.77.50.2: icmp_seq=2 ttl=64 time=0.735 ms
!
!

---

### Post by dvlabguy on 2010-03-24
forgot to add the 70-persistent-net.rules

[EMAIL="root@ubuntu"]root@ubuntu[/EMAIL]:~# cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.
# PCI device 0x14e4:0x167a (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:b9:30:60:03", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1186:0x4c00 (skge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:46:72:41:c6", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"
# PCI device 0x1186:0x4c00 (skge)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:46:72:41:c6", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3.500"

---

