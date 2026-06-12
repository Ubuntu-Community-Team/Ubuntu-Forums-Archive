---
title: "Install driver for wireless adaptor in 10.04"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by bobterri73 on 2012-09-07
I upgraded my internet service to a WIFI card.  I installed a Rosewill RNX-N180UBE Wireless Adaptor on my dual boot (Vista/Ubuntu 10.04.3, kernel 2.6.32-36-generic) system to communicate with the WIFI card.  The Rosewill adaptor works with the Vista system, but does not work with my Ubuntu 10.04.  I suspected I needed to install a different driver, so I downloaded a Linux driver from the Rosewill site that supports Linux kernel 2.6.x.
  
Where and how do I install the new driver?  And what are the commands I need to use?

My goal in all this is to upgrade to 12.04.  But the upgrade instructions said to update the 10.04 first; but 10.04 does not connect to the internet so I cannot update it.  By the way, I can run 12.04 on a CDROM and the Rosewill adaptor works fine.

The output to the "sudo lshw -C network" command reads in part:

*-network
  description: Ethernet controller
    .
    .
    .
*-network DISABLED
  description:Wireless interface
  physical id:  1
  logical name: wlan0
  serial  00:1a:ef:1d:34:1d
  capabilities: ethernet physical wireless
  configuration: broadcast=yes  multicast=yes  wireless=802.11b/g

---

