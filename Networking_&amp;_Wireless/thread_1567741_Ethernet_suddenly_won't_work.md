---
title: "Ethernet suddenly won't work"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by bynhffba on 2010-09-04
Ethernet suddenly won't work

Hi, 

I've recently got som problems with my ethernet connection. Ethernet have always worked before, but when I moved to a student housing I had to configure Network Manager to make the new ethernet connection work, so I did and it worked. But now, when I use ethernet connection other places than in the student housing, it won't work. 

When I plug in the ethernet-cable (other places than at the student housing) in my laptop, Network Manager try to connect using my new wired "Student" settings (when "Student" is made automatically connecting), and when it obviously can't do that, I get the message "Wired Network - Disconnected". Otherwise, when "Student" isn't configured to connect automatically, nothing happens, and I don't get the "eth0" alternative I used to get under Network Manager. (WIFI connection still work).

Settings for my "Student" network:
SETTINGS
Wired:
   MAC adress: ***
   MTU: automatic

IPv4 Settings:
   Method: Automatic (DHCP)

IPv6 Settings:
   Method: Ignore

802.1x Security:
   x "Use 802.1X security for this connection
   Authentication: Protected EAP (PEAP)
   Anonymous identity: /blank/MSCHAPv2
   CA certificate: (None)
   PEAP version: Version 0
   Inner authentication: ***
   Username: ***
   Password: ***

Commands I've seen other with ethernet problems have been asked to perform:
```
$ lspci
...
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
...
---------------------------------------------------------
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr *** 
          inet6 addr: fe80::2a0:d1ff:fec1:8cd1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55332 (55.3 KB)  TX bytes:864 (864.0 B)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4454330 (4.4 MB)  TX bytes:4454330 (4.4 MB)

wlan0 ...
---------------------------------------------------------
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
---------------------------------------------------------
$ cat /etc/NetworkManager/nm-system-settings.conf
# *comments*

[main]
plugins=ifupdown,keyfile

no-auto-default=***,

[ifupdown]
managed=false
---------------------------------------------------------
$ dmesg | grep -e eth0 -e bcm
[    1.137535] eth0: RTL8168b/8111b at 0xf80a0000, 00:a0:d1:c1:8c:d1, XID 18000000 IRQ 29
[   15.247343] r8169: eth0: link up
[   15.247353] r8169: eth0: link up
[   25.568036] eth0: no IPv6 routers present
[  281.003419] r8169: eth0: link down
[  283.515964] r8169: eth0: link up
[  366.100726] r8169: eth0: link down
[  368.875625] r8169: eth0: link up
[  385.784855] r8169: eth0: link down
[  388.254704] r8169: eth0: link up

```

OS:
Ubuntu 10.04

---

### Post by grahammechanical on 2010-09-04
I am just checking my ethernet connection under network manager - Connection Information. My Active connection lists IP address, Broadcast address, Default route, and Primary DNS. They are a similar set of numbers. From a set-up leaflet that came with my router/ modem I know the Default route and the Primary DNS  are the address of the router/modem. So, I am guessing that if you wish to connect to different routers using ethernet you may need to put in a Primary DNS for that particular router.

This is just a thought.

Regards.

---

### Post by bynhffba on 2010-09-04
> **grahammechanical said:**
> So, I am guessing that if you wish to connect to different routers using ethernet you may need to put in a Primary DNS for that particular router.
Not sure if I quite get what you mean, but both *Default Route* and *Primary DNS* have the same address, the same address as my router. Have I got you right, or was it something else that I didn't understand?

Thanks!

---

