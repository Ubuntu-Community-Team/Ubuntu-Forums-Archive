---
title: "How to set up a Wireless connections"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by Surendra on 2009-05-24
Hi,
I installed Ubuntu Server 9.04 on my virtual PC 2007.  Now i am not able to connect wireless. 
Notebook: IBM Thinkpad T42
OS: Windows XP.

[PHP]cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
[/PHP]

[PHP]iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

[/PHP]

[PHP] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:ff:40:4e:ec
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:ffff:fe40:4eec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37087 (37.0 KB)  TX bytes:27819 (27.8 KB)
          Interrupt:11 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:440 (440.0 B)  TX bytes:440 (440.0 B)

[/PHP]

Now i am able to connect throuw Wire. Can anybody tell how to fix my wireless on this server. 

Thanks in Advance

---

