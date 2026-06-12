---
title: "Acer Aspire 1 Netbook WIFI Issues (atheros card)"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by sebloss1 on 2013-02-04
Hi Everyone,
 
I recently purchased an Acer Aspire 1 Netbook D270-1865 with Windows 7 starter already installed.  I've used Ubuntu for a couple of years and wanted to dual-boot both Windows and Ubuntu, but something went wrong during the install and messed up my harddrive partitions, so I ended up having to do a clean install of Ubuntu on the whole system.  
 
I've gotten it to where I can hit the desktop without a problem, but now I'm running into issues with the wireless card.  I've been looking at forums/help sites all day, but nothing seems to work.  I don't have a way to connect the netbook directly to the internet, but I have another computer (running Win XP) that I can hit the internet on, so I've been having to download files onto a thumbdrive and transfer it over the netbook that way.  
 
Can anyone walk me through this?  After a month of messing with it myself this is clearly over my head.

---

### Post by ahallubuntu on 2013-02-04
~

---

### Post by sebloss1 on 2013-02-04
*-network
 
description:  Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet Controller
 
*-network UNCLAIMED
 
description: Network Controller
product: Atheros Communications Inc.
 
 
 
When I run the lspci command, it tells me I have an atheros device 0032, and the word "network" comes back in bold red.
 
I'm running 10.10.

---

### Post by sebloss1 on 2013-02-04
I did download the windows driver from acer and attempt to load it into the ndis wrapper program (labeled windows wireless driver) from my drop down menu, but I can't figure out what to do with it.  The .inf file downloaded, but I can't figure out if I'm doing the wrong thing entirely, or just missing a step.

---

