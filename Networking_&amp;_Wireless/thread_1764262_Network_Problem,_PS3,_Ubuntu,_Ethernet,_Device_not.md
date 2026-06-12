---
title: "Network Problem, PS3, Ubuntu, Ethernet, Device not Managed"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by shssta on 2011-05-21
Need some help here.

Last night I hooked my PS3 to Ubuntu in order to share internet through my 3g internet connection. It worked great for about an hour, then I went to bed. Woke up this morning and it would not connect to the wired network like it had done last night.

Spent an hour trying thing from the forum here with no success, decided to reboot see if any of the fixes I tried would work. On reboot it now says Device not managed under the network drop down for the wired network.

Only two things i remember doing before that were editing the /etc/network/interfaces file and installing a package from synaptic dhcpcd

running 10.04

any ideas?

---

### Post by shssta on 2011-05-21
here is the readout from ifconfig

eth0      Link encap:Ethernet  HWaddr 00:30:67:86:3c:05  
          inet6 addr: fe80::230:67ff:fe86:3c05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14946 (14.9 KB)  TX bytes:15443 (15.4 KB)
          Interrupt:27 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:30:67:86:3c:05  
          inet addr:169.254.4.154  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5456 (5.4 KB)  TX bytes:5456 (5.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:28.255.246.226  P-t-P:68.28.185.85  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1548708 (1.5 MB)  TX bytes:341334 (341.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:d3:98:c1  
          inet6 addr: fe80::211:50ff:fed3:98c1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7038 (7.0 KB)

---

### Post by shssta on 2011-05-21
here is the /etc/network/interfaces info

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp 
```

i added this part

# The primary network interface
auto eth0
iface eth0 inet dhcp

it was not there before

---

### Post by shssta on 2011-05-21
ok undid both those changes and now it no longer says device not managed, and shows the connection and i can attempt to connect but it still wont make the connection

---

### Post by shssta on 2011-05-21
i guess another thing i can add here is that it wont even establish a connection with the ps3 anymore, with or without the 3g modem connected

anyone?

---

### Post by shssta on 2011-05-21
solved following instructions here 

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Internet_connection_sharing_.28DHCP_server.29]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Internet_connection_sharing_.28DHCP_server.29")

do not know how to mark as solved

---

