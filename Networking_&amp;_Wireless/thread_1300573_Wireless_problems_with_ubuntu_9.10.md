---
title: "Wireless problems with ubuntu 9.10"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by johan666 on 2009-10-25
Hello everyone... Sorry 4 my bad english =)

Heres my problem i would like to get som help with..

I just updated my ubuntu 9.04 > 9.10. In 9.04 my wireless alfa adpater just worked fine.
I could connect to internet but the signal was poor. But i got my ip and it worked. I had som problems with the driver but it worked fine. Now that i updated my system the signal from my alfa usb adapter is great but i dont get ip. I have one wireless card in my laptop that is under wlan0 and the signal is **** but i can connect with it. And this sucks =)

My usb adapter is wlan1 and the wireless card is wlan0.

Why does it not connect now that i updated my system.. Plz need som help with this..

Johan From Sweden


*-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster1
       version: 00
       serial: 00:21:6b:69:73:be
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.2.106 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:94600000-94601fff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 00:23:5a:df:dc:af
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:93500000-9353ffff ioport:1000(size=128)
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 00:c0:ca:2f:a3:f7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11abgn

---

### Post by 101011010010 on 2009-10-25
Hello there,
If you have a look at this very good thread (the last post tells you what you need to do) everything should be explained. [http://ubuntuforums.org/showthread.php?t=960642 ]("http://ubuntuforums.org/showthread.php?t=960642")
I hope this helps

---

