---
title: "Wireless Not working? Right after install"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by CHudson on 2010-06-05
Well...Finnaly got around to getting rid of vista on my Acer Aspire 5315 Laptop...

Put Ubuntu 8.10 on it and right of the bat..My internet wont work...Cant view any wireless connections nearby..Heck it doesnt even show the option to connect to anything? I havent used Ubuntu..in a long time..and need to get my laptop up and running soon..Really soon Lol

Please help? Id be more than happy to get any driver info or anything anyone needs to help me..just tell me how to get the info..Lol

---

### Post by marcoftheknight on 2010-06-06
Hey,
GO to applications>>Accesories>>click on the terminal

paste this : 
sudo lshw -C network 
or
 lshw -C network

that way we have a little information 

also go to system >> preferences>> Netowrk connections >> clicl wireless tab

check to see if theres a connection if theres no connection then add new connection and input your networks info hopefully that works other wise my need some hacking..
Thanks

---

### Post by CHudson on 2010-06-06
Ok this is what i got Lol

*-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:6f:bb:46
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 56:4b:df:f0:f8:40
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by CHudson on 2010-06-06
And no i tried going to the wireless tab and make a connection, didnt really work It wouldent do anything Lol

---

### Post by CHudson on 2010-06-06
Btw dont expect too fast of a reply Lol..I have to copy n paste from the laptop to office..save to a flash drive and stick on my comp to post here xD

---

### Post by CHudson on 2010-06-06
Im having a problem with my wireless internet working..I just put ubuntu 8.10 on mah Acer Laptop...i cant really get anyones help to get it working though :(

---

