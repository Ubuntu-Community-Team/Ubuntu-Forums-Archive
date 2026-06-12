---
title: "Another wireless problem"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by pean00tz on 2013-04-06
My wireless used to work fine untill we upgraded the firmware on the router (ASUS RT-N10E). The reason why is because wireless didnt work on a samsung tab.
From that I speculated it was a problem with the router config but I cant seem to find a solution for my lenovo thinkpad with ubuntu 12.04 which just cant connect. 
I tried from WPA2 personal with AES to a completly unprotected setting. 

At the moment the wireless is set to b/g mixed with WPA2 and AES.

 Dont know if this helps but lshw -C network retuns:
```
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 01
       serial: 08:ed:b9:e1:XX:XX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:cdd00000-cdd03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 07
       serial: b8:88:e3:30:XX:XX
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.155 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:cc404000-cc404fff memory:cc400000-cc403fff

```

When I try to connect to my wireless the router log says:
```
Mar 13 17:30:54  wlan0: A wireless client is associated - 08:ED:B9:E1:XX:XX
Mar 13 17:30:54  wlan0: WPA2-AES PSK authentication in progress...
Mar 13 17:30:54  wlan0: A wireless client is associated - 08:ED:B9:E1:XX:XX
Mar 13 17:30:54  wlan0: Open and authenticated
Mar 13 17:31:40  wlan0: A wireless client is disassociated - 08:ED:B9:E1:XX:XX
```

I'm guessing the "A wireless client is disassociated" is a good clue but nothing I googled worked.
No matter how many clients are connected to the router I cant connect.
I would appreciate any help!

---

### Post by pean00tz on 2013-04-06
I guess the DHCP was causing the trouble. I simply added a static ip on my laptop and now it works...

---

