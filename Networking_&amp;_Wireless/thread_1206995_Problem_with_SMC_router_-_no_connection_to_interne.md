---
title: "Problem with SMC router - no connection to internet"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by chrislang on 2009-07-07
My SMC7004VBR Barricade Router seems to have stopped working. It was fine until this morning....  

I'm using ubuntu 8.04. The little network applet at the top of the screen, says I'm connected, but when I try to connect to the internet I get "Failed to connect" error message. When I type 192.168.2.1 in a brower, I get "Firefox can't establish a connection to the server at 192.168.2.1."

Here's what I got from ifconfig:

```
~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 44:4d:50:43:15:4a  
inet6 addr: fe80::464d:50ff:fe43:154a/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B)  TX bytes:7072 (6.9 KB)
Interrupt:21 Base address:0xd800 

eth0:avahi Link encap:Ethernet  HWaddr 44:4d:50:43:15:4a  
inet addr:169.254.3.125  Bcast:169.254.255.255  Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
Interrupt:21 Base address:0xd800 

lo Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:2095 errors:0 dropped:0 overruns:0 frame:0
TX packets:2095 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:104940 (102.4 KB)  TX bytes:104940 (102.4 KB)
```

I tried nslookup pingplotter and got:

```
;; connection timed out; no servers could be reached
```

Here's cat /etc/network/interfaces

```
auto lo
iface lo inet loopback
```

I've tried resetting the router, I've used the CD that came with the router (on a Windows computer), but got the following error:

```
Adaptor gateway IP address does not match Wireless Barricade router IP address. 
Please reset Wireless Barricade for 30 seconds and run Setup Wizard again.
```

I tried resetting the router, rebooting the computer, but got the same error message again.

I've spent a while looking around the Ubuntu forums and google, but can't seem to sort this out. If you need any more information please let me know. Thanks for any suggestions! 

cheers, Chris

---

### Post by pricetech on 2009-07-07
It looks to me like your router isn't working.  I'm not as good at interpreting the output of ifconfig as others, but I'm seeing a self assigned IP, which means you're not getting an IP from your router.  Plus the fact that a winders box can't seem to find it either.

What does   "ipconfig /all"   in winders give you ???

---

### Post by superprash2003 on 2009-07-08
you could try requesting for an ip address by typing** sudo dhclient eth0**

---

### Post by chrislang on 2009-07-08
Thanks pricetech. 

Here's what "ipconfig /all" gave me:

```

Windows-IP-Konfiguration

        Hostname. . . . . . . . . . . . . : acer-5xp63ppjt3
        Primäres DNS-Suffix . . . . . . . :
        Knotentyp . . . . . . . . . . . . : Hybrid
        IP-Routing aktiviert. . . . . . . : Nein
        WINS-Proxy aktiviert. . . . . . . : Nein

Ethernetadapter LAN-Verbindung:

        Verbindungsspezifisches DNS-Suffix:
        Beschreibung. . . . . . . . . . . : Realtek RTL8139/810x Family Fast Eth
ernet NIC
        Physikalische Adresse . . . . . . : 00-02-3F-1B-36-0C
        DHCP aktiviert. . . . . . . . . . : Ja
        Autokonfiguration aktiviert . . . : Ja
        IP-Adresse. . . . . . . . . . . . : 0.0.0.0
        Subnetzmaske. . . . . . . . . . . : 0.0.0.0
        Standardgateway . . . . . . . . . :
        DHCP-Server . . . . . . . . . . . : 255.255.255.255

```

Sorry it's all in German - but hopefully still understandable....

---

### Post by chrislang on 2009-07-08
Thanks superprash2003.

I tried sudo dhclient eth0 - here's what I got:

```
:~$ sudo dhclient eth0

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/44:4d:50:43:15:4a
Sending on   LPF/eth0/44:4d:50:43:15:4a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I'm afraid I don't know what any of this means.... none of it looks good though.

---

### Post by chrislang on 2009-07-08
I decided that the router probably is kaput, so I stuck the cable in the modem and used "sudo pppoeconf" to connect. So, I'm happily back on my ubuntu computer and maybe one day I'll buy a new router....

---

