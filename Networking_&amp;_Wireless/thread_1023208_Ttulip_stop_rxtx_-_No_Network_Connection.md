---
title: "Ttulip_stop_rxtx - No Network Connection"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by de4db0y on 2008-12-27
Im running Linux 8.10 -- Intrepid Ibex
Kernel --  2.6.27-7-generic

Network issue -- NO CONNECTION at all  - The computer is running a Windows partition - and that has a connection all day long - so it's not a hardware / cabling issue --- 

I've tried DHCP and Static IP -- I've tried 
connecting directly to the DSL Modem and going through my Linksys router - I've tried adding modules and adjusting the BIOS -- I've shut everything down and restarted it -- a real problem solving PARTY 

Here is what I know:  

I have two NIC's, eth0 and eth1 (eth1 is BUSTED, so it can't be used) 


The drivers (lsmod):

tulip (eth0)
8139too, 8139cp (eth1)  

dmesg |grep tulip returns:

**tulip_stop_rxtx() failed (CSR5 ....) **

lspci returns:

Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)  -- (this is eth0) 

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
NOTE: REALtek is eth1 --> NOT being used  

I've seen some threads similar to this -- Most claim that the newer Kernels fix the issue -- (note: a 6.x version of Ubuntu worked fine on the same computer)  --- 

Anyone have an idea why this is busted?

Thanks for any help -
De4db0y

---

