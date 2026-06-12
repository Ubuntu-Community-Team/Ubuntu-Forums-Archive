---
title: "eth0 broken"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by grkuntzmd on 2009-07-27
Yesterday I was trying to repair a WRT54GL router that I had bricked (it's fixed now). During the repair, as root, I had set my wired eth0 to a fixed IP address so that I could connect to the router. I can't get it to use DHCP now. My home network is on 192.168.0.x, but during the repair, I had set eth0 to 192.168.1.101 and 192.168.2.101 at various times. I eventually set it to (static) 192.168.0.101 while doing the final configuration of the router.

I am at work now and cannot get the interface to talk to the DHCP server on 172.23.150.3.

The output of "dhcpclient eth0" is:
```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1d:09:ba:75:b3
Sending on   LPF/eth0/00:1d:09:ba:75:b3
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.101 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.101 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
Trying recorded lease 192.168.0.101
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

Why is it still trying 192.168.0.101? I did a "grep -r '192.168.0.101' /etc", but found no files containing this pattern. I even tried "ifconfig eth0 del 192.168.0.101". I have also rebooted since making the changes.

Here is the output of "ifconfig eth0":
```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:ba:75:b3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

```
and the contents of /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

# The wifi network interface
auto eth1
#iface eth1 inet dhcp

```

BTW, eth1, my wireless connection is working fine on DHCP:
```
eth1      Link encap:Ethernet  HWaddr 00:16:44:7b:ec:91  
          inet addr:172.23.150.103  Bcast:172.23.150.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fe7b:ec91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1646 errors:0 dropped:0 overruns:0 frame:842
          TX packets:984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1249367 (1.2 MB)  TX bytes:151942 (151.9 KB)
          Interrupt:17 Base address:0xc000 

```

Thanks, Ralph

---

### Post by Iowan on 2009-07-27
Jaunty? Try commenting out the "auto eth0" and restart. You can also check settings in Network Manager applet.

---

### Post by grkuntzmd on 2009-07-28
> **Iowan said:**
> Jaunty? Try commenting out the "auto eth0" and restart. You can also check settings in Network Manager applet.

I tried commenting out the "auto eth0", but it did not work.

The NetworkManager applet says that it is not managing the wired connection.

---

### Post by ZhuaSD on 2009-07-28
You can make that connection get managed if you run:

```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

and edit managed=false to managed=true

Then you will have to set up the connection again.

---

### Post by grkuntzmd on 2009-07-28
> **ZhuaSD said:**
> You can make that connection get managed if you run:

```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

and edit managed=false to managed=true

Then you will have to set up the connection again.

I already did that. Here is my nm-system-settings.conf file:
```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true
```
No change.

---

