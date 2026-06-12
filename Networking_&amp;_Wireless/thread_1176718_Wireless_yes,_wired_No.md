---
title: "Wireless yes, wired No"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by HoxABCD on 2009-06-02
Hi I have an EEEPC (1008ha) with an atheros AR 9285 wifi card and an Atheros AR 8132  PCI-E Fast ethernet adapter.   I have installed the ubuntu netbook remix ver. 9.04. 
 
I can not seem to get the wired adapter to work, Network manager does not see it.    
 
This is a dual boot system and under winXp the adpater/connection are working fine.
 
I would prefer to use the network cable when possible as the connection is generally faster.  
 
Any suggestions would be terrific.  
 
Using sudo ifup eth0 ,  I get: Ignoring Unknown eth0=eth0
 
 
Using sudo lshw -C network I get:
 
 
 
*-network UNCLAIMED 
description: Ethernet controller
product: Attansic Technology Corp.
vendor: Attansic Technology Corp.
physical id: 0
bus info: pci@0000:02:00.0
version: c0
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list
configuration: latency=0
*-network
description: Wireless interface
product: AR9285 Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:01:00.0
logical name: wmaster0
version: 01
serial: 00:22:43:9d:37:b0
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath9k ip=64.213.211.66 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: a2:eb:32:67:02:02
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
 
 
Thanks in advance for any help offered.

---

### Post by DUfire on 2009-06-04
I was curious if anyone had any word on this, I just ordered this netbook it should be here tomorrow, and I might have this problem putting Ubuntu on it (hopefully not but we'll see). 

Also, anyone else with this netbook, does the wireless pretty much OOB with Ubuntu?

[http://www.liliputing.com/2009/05/asus-stays-one-step-ahead-of-ubuntu-with-eee-pc-1008ha.html](http://www.liliputing.com/2009/05/asus-stays-one-step-ahead-of-ubuntu-with-eee-pc-1008ha.html)

---

### Post by edrodgers731 on 2009-06-06
Ubuntu will work, but ironically, you need access to the online repository at this point.  I have tried 9.04 netbook and eeebuntu 3.0.  Both the same.

Moblin worked with the wireless card, but it is still a work in progress and isn't quite ready.

I put Windows back on until the drivers get included in the next distributions.

I'm sure soon we will find a convenient tutorial to get it working from the distribution with a couple of extra packages added.

---

### Post by JohnsonMR on 2009-06-09
HoxABCD, looks like your thread as been hijacked...  I too have been unable to get a wired connection to work after I upgraded to 9.10.  *Sudo ifup eth0* gives me the same results.  NM just will not use my wired connection.  I'm still looking for a solution.

---

### Post by leandromartinez98 on 2009-06-27
I have everything working here. Here is the solution, which
I found over internet and posted in another thread:

[http://ubuntuforums.org/showthread.php?p=7525735#post7525735](http://ubuntuforums.org/showthread.php?p=7525735#post7525735)

---

### Post by zuzubu on 2009-07-13
I just bought a Eee PC 1005HA.
I installed ubuntu netbook version - and both wireless and wired network did not work.

I confirm the noted fix worked.
I downloaded the driver from Aetheros, compiled and installed on the eee pc.
This fixed the wired network.

After upgrading all the software, I installed the backport modules and after reboot the wired worked also.

Thanks to all in this thread for the advice !

p.s. I very much like the ubuntu netbook installation - looks great and very functional.

---

