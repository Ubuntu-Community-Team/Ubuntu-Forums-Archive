---
title: "Which is the best WLAN PCI-card in Ubuntu 10.04?"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by mvanderlaen on 2010-05-23
Hi all,

[B]Does anyone has good experiences with specific Ubuntu supported WLAN PCI-cards?
This link shows a list of supported PCI-cards, but which is best:[/B]
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

And the installation needs to be easy!

I’ve tried installing these PCI-cards in my computer, useing Linux drivers, NdisWrapper, etc. Unforutately without any success:
- DWL-G510, Ralink Chipset, Ralink RT2561/RT61
- Realtek Semiconductor, RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller

Many thanks!

---

### Post by 1roxtar on 2010-07-30
In my experience, the DYNEX brand PCI wireless cards are the easiest to install and get up and running.  Just make sure to go to Synaptic (using a wired connection) and type in the search box "Broadcom Modalias", add and install.  Your hardware will then be detected and you will simply be asked to activate the driver and voila!, wireless internet.  I use these cards exclusively now.

---

