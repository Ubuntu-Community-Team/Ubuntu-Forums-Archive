---
title: "sabrent RT2800 adapter fails to see wireless networks"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by jrn34exp on 2011-10-23
My wireless driver is the RT2860STA, successfully compiled but maybe not configured right.
1. Machine: AMD 7850 dual 2.8GHz/Foxconn MTB
2. Wireless:RALink RT2800 802.11nPCI
3. Interface: Inet6    UP   Broadcast  Multicast   MTU 1500  auto   2.4GHz   access point=not associated
4. Modules:  no WLAN
5. Kernel Boot Messages:  No WLAN
6. Network Config:
              description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 5
       bus info: pci@0000:03:05.0
       logical name: ra0
       version: 00
       serial: 00:0d:09:62:2c:d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.0 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:20 memory:febf0000-febfffff

7. Scan for networks:  failed to read scan data
8. Ubuntu version:  10.04.1 LTS/ Gnome2.30.2
9. Kernel:  2.6.32-24-generic  i686
10.  Restart network:  reconfigured okay

Well there you have it, that should be all you need. Machine works well with wireless modem out of the box, but not with installed PCI adapter. I need to access my WIFI point :)

---

