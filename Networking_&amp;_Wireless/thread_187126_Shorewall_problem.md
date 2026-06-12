---
title: "Shorewall problem"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by Dany on 2006-06-02
I have a problem with shorewall.I cant connect through it to the outside internet...
I want to be able to connect throug it for web browsing,DC++,ftp servers, Bit Torrent, IRC.
I would apreciate somebody could please give me some help with whats wrong with my configs, that Ive posted below ? I have dynamic IP and 2 NICs.


Dany:/etc# ifconfig

eth0      Link encap:Ethernet  HWaddr 00:14:6C:76:36:FC
          inet addr: xx.xxx.xxx.xx  Bcast: xx.xxx.xxx.xxx  Mask:255.255.255.128
          inet6 addr: fe80::214:6cff:fe76:36fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6812 errors:0 dropped:0 overruns:0 frame:0
          TX packets:970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:479670 (468.4 KiB)  TX bytes:138787 (135.5 KiB)
          Interrupt:3 Base address:0x1000

eth1      Link encap:Ethernet  HWaddr 00:14:6C:81:92:B1
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe81:92b1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:378 (378.0 b)
          Interrupt:10 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2996 (2.9 KiB)  TX bytes:2996 (2.9 KiB)


shorewall

startup=1


rules 

ACCEPT       net                 fw                     tcp         22
DNAT         net                 loc:192.168.1.1        tcp         www          -               $ETH0_IP
  



policy

loc             all             ACCEPT
net             all             DROP
all             all             REJECT



zones

net                     Net             The Internet
loc                     Local           Local Network



shorewall.conf

IP_FORWARDING=On
DROPINVALID=Yes


interfaces

net     eth0            detect          dhcp,routefilter,tcpflags,nobogons
loc     eth1            detect          routeback    



masq

eth0                    eth1
eth1:192.168.1.1        eth1            192.168.1.1     tcp     www



params

ETH0_IP=`find_first_interface_address eth0`

---

