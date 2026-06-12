---
title: "Only 10Mb on 1Gb interface"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by Skip Da Shu on 2009-01-05
I recently set up machine using a Asus P5KPL-CM mobo.  This uATX board has an onboard nic that I believe runs off the PCIe bus.  Anyway, this nic wasn't support in the kernel until fairly recently (2.6.2x?).  After trying to get it to work under Xubuntu v8.04 I finally gave up and just reinstalled the OS using Xubuntu v8.10 64b only to run into the gnome network-manager problem with static IP addresses...well a couple of installs later I've got the little number cruncher back up and running w/ manually configured static IP (removed gnome network manager and built my own resolv.conf and interfaces files).  

However the nic (a 1Gb nic) will only run at 10Mb.  It's currently plugged into 10/100 switch so I'd expect it to auto negotiate 100Mb and the other two computers on the same switch are running at 100Mb.  I've swapped out the cat5e between one that's at 100 and this 10Mb one and no diff.  I also tried running a 1000Mb line to it.  It doesn't even connect at 10Mb on that.

```
lspci | grep -i ethernet
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
```

I've used both ethtool and mii-tool to try and set the thing up to 100 but it just loses the link.  


```
sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: **10Mb/s**
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x00000000 (0)
	Link detected: **yes**
```
```
sudo ethtool -s eth0 speed 100 duplex full autoneg on
```
```
sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: Unknown! (65535)
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x00000000 (0)
	Link detected: **no**
```
```
sudo ethtool -i eth0
driver: ATL1E
version: 1.0.0.7-NAPI
firmware-version: L1e
bus-info: 0000:01:00.0
```
```
sudo modprobe -l atl*
/lib/modules/2.6.27-9-generic/kernel/ubuntu/atl2/atl2.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/net/atl1e/atl1e.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/net/atlx/atl1.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/input/misc/atlas_btns.ko
```

Is there any chance that the atl2 driver might work better?  Can someone point me to a link to force the kernel to use that driver (modprobe -r atl1e ??)

---

### Post by jcliburn on 2009-01-05
The atl2 driver is for the L2 chip.  Your system is fitted with the L1e chip and will operate only with the atl1e driver.

Although you said you swapped your cable already, it has been my experience that the cable is almost always the culprit whenever I encounter lower than expected autonegotiated link speeds.  It could also be a faulty switch port, or a faulty NIC, but it's not the driver; I have an engineering demo of the L1e device installed in one of my systems and it works at 1000 Mbit/s using the same driver.

---

### Post by jcliburn on 2009-01-05
One other thing...

It's probably a typo, but I notice in your post that you used ethtool to try and force link speed/duplex while enabling autonegotiation at the same time.  You should use one or the other, not both.

---

### Post by jcliburn on 2009-01-05
Erroneous duplicate post on my part.  Sorry.

---

### Post by Skip Da Shu on 2009-01-06
> **jcliburn said:**
> One other thing...

It's probably a typo, but I notice in your post that you used ethtool to try and force link speed/duplex while enabling autonegotiation at the same time.  You should use one or the other, not both.

First off... I appreciate that you took the time to respond.

I added the 'autoneg on' after reading someplace that autoneg was required (by some spec) for 1Gb.  Setting autoneg off results in an error.  I'm tearing open a bag containing one 1.5m Panduit cat6+ patch cord now (a commercial installer tells me these are the best).  Let me get over to that machine with this fresh cable and see what happens.

---

### Post by Skip Da Shu on 2009-01-06
1) The other day, in the midst of gnome-network-manager problems I tried a cheap PCI 10/100/1000 nic card (Trendnet TEG-PCIXR, main chip says RTL8169SC) in it.  I let it get a DHCP address (static wasn't working at the momement) and it connects at 100Mbps on the same port I'd at the on-board nic plugged up to.
2) Well the new cat6+ didn't help.  Still would only do 10Mbps.  
3) I disconnect a bunch of stuff and got this machine so it was running straight back to the DGL-4100 router (taking two switches out of the picture) and it would not connect at all to this 1Gbps router (at 10, 100 or 1000Mbps).
4) Hooked everything back how it was with yet a different cable from a different port on the switch to this machine.  Back connected at 10Mbps. Below is after a fresh power up. 
```
crunch23:~$ sudo ethtool eth0
[sudo] password for skip: 
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x00000000 (0)
	Link detected: yes
skip@crunch23:~$
```
4) Confirmed that autoneg off doesn't work:
```
crunch23:~$ sudo ethtool -s eth0 autoneg off
Cannot set new settings: Invalid argument
  not setting autoneg
crunch23:~$ 
 
```
[/CODE]```
crunch23:~$ sudo ethtool -s eth0 autoneg on
crunch23:~$ 
```
5) I did try setting just the speed to 100:
```
crunch23:~$ sudo ethtool -s eth0 speed 100
crunch23:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x00000000 (0)
	Link detected: yes
crunch23:~$ 
```

6) lshw output:```

crunch23:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: b0
       serial: 00:1f:c6:c9:44:e3
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.218.23 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=10MB/s
crunch23:~$ 
```


Anything else I should try?

Unless you advise differently, I'm going to declare the nic bad.  I've got about 10 more days I could exchange the mobo at Fry's but honestly for what this machine's mission in life is... it's not worth the gas or time to drive into town and stand in line at Fry's.  If that changes I can always put the spare TrendNet nic in it.

Be it right or not... this is why I own about 8 GA-G31M-S2L mobos vs Asus P5KPL-CM or Foxconn G31MV-K or ASRock G31M-S or (gag) ECS G31T-M mobos.

Let me reiterate my appreciation for your help (hmmm sounds a bit formal for me... so let's add...), Bubba.

---

