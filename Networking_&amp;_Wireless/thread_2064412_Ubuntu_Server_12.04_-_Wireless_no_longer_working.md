---
title: "Ubuntu Server 12.04 - Wireless no longer working"
date: 2012-09-29
forum: Networking &amp; Wireless
---

### Post by jddphd on 2012-09-29
Hello,

For reasons unknown to me, I am no longer able to establish a wireless connection from my 12.04 server installation. It had been functioning properly a few days ago.

I have tried to find other cases in the forums similar to mine and have tried various things, but to no avail and of course I'm afraid I've bolloxed it up. I'd be grateful for some help.

Below are the results from the following commands. I'm hand-typing these results since I can't SSH in and moving everything so I can wire into the router is a pain, so apologies if the spacing isn't quite right. (NB: I don't have rfkill installed and thus can't post results from it.)

Many thanks in advance for your help.

lspci -nnk | grep -iA2 net
[PHP]
02:06.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
        Subsystem: Ralink corp. EW-7108PCg [1814:2561'
        Kernel driver in use: rt61pci
[/PHP]

ifconfig -a
[PHP]
lo Link encap:Local Loopback
 inet addr:127.0.0.1 Mask: 255.0.0.0
 inet6 addr: ::1/128 Scope:Host
 UP LOOPBACK RUNNING MTU:16436 Metric:1
 RX packets:44 errors:0 dropped:0 overruns:0 frame:0
 TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:0
 RX bytes:3672 (3.6 KB) TX bytes:3672 (3.6 KB)

wlan0 Link encap:Ethernet HWaddr 00:0e:2e:bd:1e:78
      inet addr:192.168.1.108 Bcast: 192.168.1.255 Mask:255.255.255.0
      UP BROADCAST MULTICAST MTU:1500 Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
[/PHP]

cat /etc/network/interfaces

[PHP]
(the usual comment lines are in place - i'm not retyping by hand)

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
 address 192.168.1.108
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.1.255
 gateway 192.168.1.1
 dns-nameservers 8.8.8.8 8.8.8.4 192.168.1.1

[/PHP]

cat /etc/resolv.conf
[PHP]
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 192.168.1.1
[/PHP]

route -n
[PHP]
Destination      Gateway       Genmask       Flags  Metric  Ref   Use  Iface
0.0.0.0          192.168.1.1   0.0.0.0       UG     100     0       0  wlan0
192.168.1.0      0.0.0.0       255.255.255.0 U      0       0       0  wlan0
[/PHP]

lsmod
[PHP]
(too much to copy by hand here - i assume i am looking for references to the wireless driver? if not let me know...)

Module     Size  Used by
rt61pci       32257  0
rt2x00pci     14566  1 rt61pci
rt2x00lib     14566  1 rt61pci,rt2x00pci
mac80211     506816  2 rt2x00pci,rt2x00lib
eeprom_93cx6  12725  1 rt61pci
crc_itu_t     12707  2 rtpci,firewire_core
[/PHP]

Many thanks in advance for your help.

---

