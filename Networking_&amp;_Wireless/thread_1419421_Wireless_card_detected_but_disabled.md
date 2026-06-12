---
title: "Wireless card detected but disabled"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by sictiburon on 2010-03-01
Hey everybody im having some trouble connecting the wireless card to my wifi network, theres is a hint using the terminal

remora@remora-laptop:~$ sudo lshw -C network
[sudo] password for remora: 
 [B] *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:8c:86:23
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical [/B]ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:25 memory:f2000000-f2000fff
  *-network
       description: Ethernet interface
       product: PRO/100 VM Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 02
       serial: 00:13:a9:f8:a8:84
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.2.7 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:f4005000-f4005fff ioport:3000(size=64)
remora@remora-laptop:~$ ^C
remora@remora-laptop:~$ 

Any help?????? What can i do???

---

### Post by sictiburon on 2010-03-01
This is my card Pro/Wireless 3945 ABG (Centrino)

---

### Post by Enigmapond on 2010-03-01
This may be really obvious but you never know. Have you tried right clicking on the network manager and enabling the network?

---

### Post by sictiburon on 2010-03-01
The network manager under preferences? (im kind of new with ubuntu)

---

### Post by Enigmapond on 2010-03-01
You should have a network icon on the top panel that shows bars when it's working. If not click the one in preferences to open it or right click on the panel and add "notification area", right click and check the network enablers. It's been awhile since I've used the stock network manager. I installed wicd and use that. I found it works better. Maybe try that???

If you decide...
```
sudo apt-get install wicd
```

---

### Post by sictiburon on 2010-03-01
Thanks man problem solved! muchas gracias from venezuela!

---

### Post by Enigmapond on 2010-03-01
De Nada!!:D

---

