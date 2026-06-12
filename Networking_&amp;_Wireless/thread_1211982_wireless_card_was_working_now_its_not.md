---
title: "wireless card was working now its not??"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Chris_87 on 2009-07-13
Hi guys, 
This is my first problem i have had with intrepid since i installed it.  here is a basic description of what happend. i was using internet on wireless and the computer froze up so i turned it off. when i turned it back on the wireless was disabled and the button to turn it back on was greyed out so i cant use that now.
I used the help tab and followed procedure, i have found out that the card is still responding as it gives me details of what it is.
I think that the card is turned off but im not sure. here is copy of test.


*-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:a9:39:33
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:1e:d0:bf
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.34 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:d6:f6:bc:bd:50
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


my computer is a inspiron 6400 with 03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX 

i hope this helps

thanks

---

### Post by superprash2003 on 2009-07-13
dell machines have a shortcut key to switch on/off wireless. its the Fn key and F2 i think.. so try pressing FN+F2 to see if wifi gets enabled.. you could also try using the hardware switch found in all dell laptops..

for reference:  [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by Chris_87 on 2009-07-14
> **superprash2003 said:**
> dell machines have a shortcut key to switch on/off wireless. its the Fn key and F2 i think.. so try pressing FN+F2 to see if wifi gets enabled.. you could also try using the hardware switch found in all dell laptops..

for reference:  [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)


it worked first time thanks alot!!! i thought i was gonna have to buy new parts  :p
 thanks again!

---

