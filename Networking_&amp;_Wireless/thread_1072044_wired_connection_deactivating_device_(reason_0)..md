---
title: "wired connection deactivating device (reason: 0)."
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by spaise on 2009-02-17
hey wassup guys.
Ok so i got the problem of my install not discovering DCHP.
Im on a wired connection that is deffinately up cause this box is using it.

in the syslog on my install im getting:

Feb 17 05:37:14 xps NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 17 05:37:14 xps NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 17 05:37:14 xps NetworkManager: <info>  (eth0): device state change: 4 -> 5
Feb 17 05:37:14 xps NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 17 05:37:14 xps NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 17 05:37:14 xps NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 17 05:37:14 xps NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 17 05:37:14 xps NetworkManager: <info>  (eth0): device state change: 5 -> 7
Feb 17 05:37:14 xps NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction.
Feb 17 05:37:14 xps dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb 17 05:37:14 xps dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb 17 05:37:14 xps dhclient: All rights reserved.
Feb 17 05:37:14 xps dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Feb 17 05:37:14 xps dhclient:
Feb 17 05:37:14 xps NetworkManager: <info>  dhclient started with pid 6490
Feb 17 05:37:14 xps NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 17 05:37:14 xps NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Feb 17 05:37:14 xps dhclient: Listening on LPF/eth0/00:1c:23:06:80:9d
Feb 17 05:37:14 xps dhclient: Sending on   LPF/eth0/00:1c:23:06:80:9d
Feb 17 05:37:14 xps dhclient: Sending on   Socket/fallback
Feb 17 05:37:16 xps dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb 17 05:37:24 xps dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Feb 17 05:37:34 xps dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Feb 17 05:37:48 xps dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb 17 05:37:56 xps dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Feb 17 05:37:59 xps NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it.
Feb 17 05:37:59 xps NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 6490
Feb 17 05:37:59 xps NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled...
Feb 17 05:37:59 xps NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started...
Feb 17 05:37:59 xps NetworkManager: <info>  (eth0): device state change: 7 -> 9
Feb 17 05:37:59 xps NetworkManager: <info>  Marking connection 'Auto Ethernet' invalid.
Feb 17 05:37:59 xps NetworkManager: <info>  Activation (eth0) failed.
Feb 17 05:37:59 xps NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete.
Feb 17 05:37:59 xps NetworkManager: <info>  (eth0): device state change: 9 -> 3
Feb 17 05:37:59 xps NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Feb 17 05:38:27 xps kernel: [  342.656975] tg3: eth0: Link is down.
Feb 17 05:38:27 xps NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Feb 17 05:38:27 xps NetworkManager: <info>  (eth0): device state change: 3 -> 2
Feb 17 05:38:27 xps NetworkManager: <info>  (eth0): deactivating device (reason: 0).

if anyone can shead some light on this it would be awesome

cheers

---

### Post by superprash2003 on 2009-02-17
please post output of ifconfig from the terminal

---

### Post by helmutkohlkanzler on 2009-02-28
Hi,
I have got the same problem (intrepid). See my ifconfig output below.
This problem turned up when I tested wicd instead of network-manager-gnome.
Does anybody have an idea?
WLAN is working. I am connected via Fritzbox 7270.
ciao   
   Marcus

My /etc/network/interfaces is this:
  auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet dhcp


root@bibo:/var/log# ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:21:85:dd:08:0c  
          inet6-Adresse: fe80::221:85ff:fedd:80c/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:3238002495 overruns:0 frame:0
          TX packets:0 errors:0 dropped:127 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Basisadresse:0xc000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:27739 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27739 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:61771166 (61.7 MB)  TX bytes:61771166 (61.7 MB)

pan0      Link encap:Ethernet  Hardware Adresse 46:bd:64:50:2c:5b  
          inet6-Adresse: fe80::44bd:64ff:fe50:2c5b/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 B)  TX bytes:1152 (1.1 KB)

wlan1     Link encap:Ethernet  Hardware Adresse 00:1f:3c:cf:2e:51  
          inet Adresse:192.168.170.29  Bcast:192.168.170.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21f:3cff:fecf:2e51/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:14151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17859 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6680799 (6.6 MB)  TX bytes:15790511 (15.7 MB)

wmaster0  Link encap:UNSPEC  Hardware Adresse 00-1F-3C-CF-2E-51-65-35-00-00-00-0
0-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by lupa18 on 2010-07-30
Hi, here the same problem. 
I also update to ppa network manager (actually 0.8.1~beta1~git.20100528t200614.6810ef1-0ubuntu1~nmt1~karmic) 
but doesn't work. 

Maybe this explain the problem: [https://bugs.launchpad.net/ubuntu/karmic/+source/network-manager/+bug/435073/+viewstatus](https://bugs.launchpad.net/ubuntu/karmic/+source/network-manager/+bug/435073/+viewstatus)

---

