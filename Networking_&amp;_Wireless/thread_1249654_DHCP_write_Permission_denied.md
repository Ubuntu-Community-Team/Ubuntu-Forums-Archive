---
title: "DHCP write Permission denied"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by ezrahoch on 2009-08-25
[html]
Hi,

My Linux started to give the following error when I do: 
sudo /etc/init.d/networking restart

* Reconfiguring network interfaces... [80G RTNETLINK answers: No such process
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0c:6e:37:63:4f
Sending on LPF/eth0/00:0c:6e:37:63:4f
Sending on Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Listening on LPF/eth0/00:0c:6e:37:63:4f
Sending on LPF/eth0/00:0c:6e:37:63:4f
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.100 from 192.168.1.1
DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCADDRT: Operation not permitted

The output of ifconfig is:
eth0 Link encap:Ethernet HWaddr 00:0c:6e:37:63:4f
inet6 addr: fe80::20c:6eff:fe37:634f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:33 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:5362 (5.2 KB) TX bytes:1152 (1.1 KB)
Interrupt:16 Base address:0x8800

eth1 Link encap:Ethernet HWaddr 00:50:fc:c4:fd:4d
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17 Base address:0x8400

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B

Any ideas?

Thanks,
Ezra
[/html]

---

### Post by chili555 on 2009-08-25
What is the output of:```
cat /etc/network/interfaces
```Thanks.

---

### Post by ezrahoch on 2009-08-25
[html]
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp
auto eth0
[/html]

---

### Post by chili555 on 2009-08-25
Please change it to:```
auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0
```Then try restarting networking and see if the result is better.

---

