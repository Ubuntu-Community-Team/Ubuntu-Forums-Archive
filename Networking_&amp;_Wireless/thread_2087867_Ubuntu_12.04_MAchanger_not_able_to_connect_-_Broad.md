---
title: "Ubuntu 12.04 MAchanger not able to connect - Broadcom BCM4313"
date: 2012-11-24
forum: Networking &amp; Wireless
---

### Post by First Last on 2012-11-24
Okay guys, So i've looked around extensively on this such  topic, Only to find that no one has a true solution, Only half explained  work arounds. Something tells me this problem can be solved for the  pure reason that i " CAN " change my wifi-cards MAC address in windows 7  both manually and using Iron Geeks madMACS. So thus leads me to  investigate why after changing my mac on ubuntu  10.04/10.10/12.04/Backtrack 5 r2/r3 why i cannot connect. 
  

Please not that this is not a case of my router i have tried it on  multiple public access and with my changed MAC i cannot even connect to a  open network,


 I've read somewhere that you have to change the mac  before the wifi-card's true MAC is released in BIOS. Is this true ? This  is the only logical explanation i can think of rite now. 
  I don't mind going out and buying a new wifi-card that does support  ubuntu MAC cloning. If any one has one working out of the box please let  me know.[INDENT]   [B]description: Wireless interface          product: BCM4313 802.11b/g/n Wireless LAN Controller

vendor: Broadcom Corporation     physical id: 0     bus info: pci@0000:02:00.0     logical [/B]      [B]

name: wlan0     version: 01     serial: c0:18:85:43:c6:e4     width: 64 bits     clock: 33MHz     [/B] [B]

capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless     [/B] [B]

configuration: broadcast=yes [/B] [B]

driver=brcmsmac driverversion=3.2.0-29-generic-pae firmware=N/A ip=10.1.1.8 [/B] [B]

latency=0       link=yes multicast=yes wireless=IEEE 8 '[/B] 
 [/INDENT]I have tried both Network-Manager & WICD both failing.
  Im using Acer Aspire D-270, First off i couldn't even change my MAC  address got the error of device busy etc. But then i added the macchange  to startup now the mac changes but it just wont connect till i set it  back to original mac.

---

### Post by wildmanne39 on 2012-11-24
Thread closed. Please do not post duplicates, it dilutes community effort.

---

