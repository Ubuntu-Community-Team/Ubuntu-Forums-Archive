---
title: "About wireless router"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by satimis on 2012-01-11
Hi all,

Ubuntu 11.10 64 bit

Linksys Wireless-G Broadband Router WRT54G v2

I'm prepared changing ISP. Currently I'm running ADSL with 6MB download speed, wire LAN connection. The new ISP shall provide 4MB/4MB DSL with wireless LAN connection. The captioned wireless router will be provided by new ISP.

After searching on Internet it was found that the Data Transfer Rate of the wireless router is 54 Mbps. It will be sufficient for Internet connection of 4MB/4MB. But it will be slow for transfer of Data on LAN. It is there any suggestion other than requesting new ISP for supplying wireless router with 1G data transfer rate?

Furthermore will it be any problem on installing the Linksys wireless network interface card to Linux PC?

Thanks in advance.

B.R.
satimis

---

### Post by lukeiamyourfather on 2012-01-11
The router has Ethernet as well so you don't necessarily have to use the wireless. At 54 Mb/s you can expect around 5 MB/s (8 bits to a byte) when transferring files between machines on the network under optimal conditions. Using Fast Ethernet (100 Mb/s) you can expect around 12 MB/s when transferring files. On Gigabit Ethernet (1,000 Mb/s) you can expect as much as your hard disks can deliver which could be anywhere between 50 MB/s to 120 MB/s. To use Gigabit Ethernet you might need another switch, so the router would handle the internet connection and then a switch would be plugged into the router, and all the machines would be plugged into the switch.

---

### Post by satimis on 2012-01-11
> **lukeiamyourfather said:**
> The router has Ethernet as well so you don't necessarily have to use the wireless. At 54 Mb/s you can expect around 5 MB/s (8 bits to a byte) when transferring files between machines on the network under optimal conditions. Using Fast Ethernet (100 Mb/s) you can expect around 12 MB/s when transferring files. On Gigabit Ethernet (1,000 Mb/s) you can expect as much as your hard disks can deliver which could be anywhere between 50 MB/s to 120 MB/s. To use Gigabit Ethernet you might need another switch, so the router would handle the internet connection and then a switch would be plugged into the router, and all the machines would be plugged into the switch.

Hi,

Thanks for your advice.

If I understand it correctly.  For 100Mbps intranet connection I have to using a Cat 5 cable connecting the router port to PC.  For 1Gbps I need installing a switch behind the router.  Pls correct me if my understanding is incorrect.

The new ISP informed me on email that the wireless rounter max supports 5 PC.  What does it mean?  Whether they only supply 5 Linksys Wireless-G PCI cards?

Is there USB connection wireless PCI card for this model?

TIA

B.R.
satimis

---

### Post by lukeiamyourfather on 2012-01-12
> **satimis said:**
> 
If I understand it correctly.  For 100Mbps intranet connection I have to using a Cat 5 cable connecting the router port to PC.  For 1Gbps I need installing a switch behind the router.  Pls correct me if my understanding is incorrect.


Yup, that's correct. The connection to the outside will still be whatever the ISP provides but the speed of your network can be whatever you want to setup.

> **satimis said:**
> 
The new ISP informed me on email that the wireless rounter max supports 5 PC.  What does it mean?  Whether they only supply 5 Linksys Wireless-G PCI cards?


That might be a policy of the ISP because the router can support many more devices than five when using additional switches and wireless. You'd have to ask them how many wireless cards they supply, typically they supply none at least in the United States.

> **satimis said:**
> 
Is there USB connection wireless PCI card for this model?


Are you asking if there are USB wireless adapters? Yes, there are many and some are quite inexpensive. You would want to look for 802.11g adapters (54 Mb/s).

---

