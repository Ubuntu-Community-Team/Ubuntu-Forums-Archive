---
title: "Wireless Does not detect signals until wired connection is provided and more below."
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by rakeshreddyn on 2010-09-07
Hey Guys,

I had windows and 8.10 earlier and now have single boot 10.04 !

1.) I can see wireless networks only after I am connected to the router through wired ! I guess its some thing to do with me activating ifup and ifdown, when my wired connection stopped working as i was trying to install wireless drivers.

2.) Even when I see wireless networks, i cannot connect to any of them.

I tried various things for a whole day trying to fix it and i doubt if i screwed up some thing that was running good. 

Please let me know, if you guys need any more information.

---

### Post by JBAlaska on 2010-09-07
What brand/model of wireless device do you have and what computer are you using?

---

### Post by rakeshreddyn on 2010-09-07
My Bad ! I put it there and deleted again !

Dell Inspiron 6400 / Broadcom Wireless driver . I installed it with ndiswrapper as mentioned in the wireless wiki page available !

bcm4311 i guess ! 

I will post back the exact one in a while, when i log on to that system.

Thanks.

---

### Post by rakeshreddyn on 2010-09-07
[SIZE=4]**lshw output**[/SIZE]

*-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 01
       serial: 00:19:7d:8c:9d:9d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:5 memory:efcfc000-efcfffff
  
*-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:19:b9:58:97:c5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.1.10.25 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:5 memory:ef9fe000-ef9fffff


------> am not sure if eth0 is the right name there for the wireless !

[SIZE=4]**iwlist scan**[/SIZE] 

Gives about 14 available connections for [B]eth0

[/B]and[B] 

Interface doesn't support scanning. [/B]for[B]  lo, eth1 and pan0

[SIZE=4]lspci[/SIZE][/B]gives wireless as[B] 

Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

[/B]

---

### Post by JBAlaska on 2010-09-07
Put the Ubuntu LiveCD in your drive and go to: **System, Administration, Software sources** and check the box below "Installable from CDROM". Then open a terminal and do:
```
sudo apt-get update
```

Then:
```
sudo apt-get install bcmwl-kernel-source
```
[COLOR="Blue"]Note: If you have a wired connection working you can skip the LiveCD steps and just install[/COLOR] **bcmwl-kernel-source**.

Now reboot and select the **BroadcomSTA** driver. in **System, Administration, Hardware Drivers** You may have to reboot one more time to enable the driver.

---

### Post by rakeshreddyn on 2010-09-07
Did not solve it. :-)
I think, i have additional driver along with ndiswrapper, trying to add it to the blacklist. Hopefully that works.

Thanks though.

---

### Post by JBAlaska on 2010-09-07
If you remove ndiswrapper driver the BroadcomSTA driver should work.

Good Luck!

---

