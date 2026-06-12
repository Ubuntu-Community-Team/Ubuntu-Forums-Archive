---
title: "No wireless connection in the Network Manmager"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by Pablo Sunshine on 2010-01-13
Hi,

I've just got a new laptop and of course installed Ubuntu straight away.
Unfortunately wireless connection doesn't work. There is no connection available in the Network Manager and I really have no clue on how to fix it.

I read the instruction so those are the info needed, hope so.
Any suggestion it's welcome. Thanks.

**Machine brand and model**
Dell Inspiron Laptop

**Wireless Brand, Model, Wireless Chipset**
Broadcom Corporation BCM4312 802.11b/g (rev 01)

**check interface**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

lo        no wireless extensions.

**kernel boot messages**
[    9.677371] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    9.720232] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
>> I thought those are the relevant ones.

**network configuration**
*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff

**ubuntu version**
9.10

**kernel/architecture**
2.6.31-14-generic i686 (32bit)

---

### Post by bkratz on 2010-01-13
since you have the BCM4312 see this thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

You might also want to go to the terminal

Applications>>Accessories>>Terminal

and enter :

sudo lshw -C network
(that is (LSHW in lowercase and C in upper) and post the results here.

---

### Post by Pablo Sunshine on 2010-01-13
Got it! Great!
Thank you so much for your help.

---

### Post by bkratz on 2010-01-13
Please be sure to go to the thread tools and mark as [solved] just in case it helps someone else.

---

### Post by Ishmayl on 2010-01-13
Sorry, posted in wrong thread :(

---

