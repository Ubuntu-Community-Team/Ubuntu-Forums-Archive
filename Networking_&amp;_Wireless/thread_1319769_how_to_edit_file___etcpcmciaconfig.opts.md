---
title: "how to edit file:   etc/pcmcia/config.opts"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by sonny123 on 2009-11-08
I am following 
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check)

I am at step 4.1.2

when i run 
```
sudo pccardctl ident
```the output is...
```
Socket 0:
  no product info available
```apparently this means the memory on the card cant be read so i need to open   etc/pcmcia/config.optsa  and add information to it. But what info do I add

the example given is 
```
card ""Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN"
  manfid 0x0271, 0x0012
  function: 6 (network)
bind "ath_pci" 
```
  
lshw gives

 ```
*-network
       description: 88W8300 802.11b Cardbus PC Card
       product: 83
       vendor: Marvell Semiconductor
       physical id: 0
       version: 01
       slot: Socket 0
       resources: irq:5
  *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 03
       serial: 00:14:bf:bc:b6:9a
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsmvnds driverversion=1.53+Linksys,10/13/2004,3.1.0.36 latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```any help much appreciated... thanks in advance

---

