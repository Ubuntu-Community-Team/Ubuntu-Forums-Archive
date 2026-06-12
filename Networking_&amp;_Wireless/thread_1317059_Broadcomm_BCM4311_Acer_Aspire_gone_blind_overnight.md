---
title: "Broadcomm BCM4311 Acer Aspire gone blind overnight. 9.10 Karmic(beta)"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by crotig on 2009-11-06
I have been using Ubuntu since 9.04 and upgraded to 9.10(beta) a couple of weeks ago and the wireless connection has always worked fine out of the box. I get up this morning and turn on the laptop and it doesn't auto connect. When I check the Network Manager my Belkin wireless network is gone.
 A nearby Linksys router is still visible as always. Windows 7, dual booted on same laptop can still see my network and connect as can two other windows devices(XP and Windowsmobile). So why has my laptop just woken up blind to my network?. I had the same problem from the start on 8.04 and stopped using it because of it but it has always worked fine on 9.04-9.10 until today.

Acer Aspire 5310

Belkin 54g router

> 
lspci -nn | grep Network

05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

iwconfig wlan0

wlan0     No such device


sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:e3:e5:f8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5787m-v3.22 ip=192.168.2.5 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:d0000000-d000ffff
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:9c:ab:38
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:d0100000-d0103fff

iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.




iwlist scan isn't showing the linksys network but it is showing up in the network manager. I tried installing Wicd with the same result and have gone back to network manager. I have also tried resetting my router. There were no updates performed last night. I have updated, through a wired connection, today.

I would be grateful if anyone could shed some light.

Thanks

---

### Post by squareff255 on 2009-11-08
I'm having this same problem...

---

### Post by Comodidit on 2009-11-08
Try the fix listed on this page. Worked perfectly for me with 9.10 netbook remix.
[http://blog.alvonsi.us/2009/10/30/broadcom-bcm4311-on-karmic-koala/](http://blog.alvonsi.us/2009/10/30/broadcom-bcm4311-on-karmic-koala/)
Good luck.

---

### Post by crotig on 2009-11-08
Thanks for the replies guys.

Strangely I was having some problems with my router today and I did a firmware update on it and Ubuntu could see it again.

I have no idea why this would be.

Thanks again.

---

### Post by crotig on 2009-11-09
Same thing again this morning. My network not visible. I did the 30 sec router restart an viola! it appears. Obviously the firmware update included a router restart and that is what made it re-appear. I will have to look at this further and try some of the fixes suggested.

---

