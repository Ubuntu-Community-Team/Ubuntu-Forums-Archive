---
title: "wifi question"
date: 2012-12-08
forum: Networking &amp; Wireless
---

### Post by monkeybrain2012 on 2012-12-08
Hi,

I am experiencing a mildly annoying wifi problem. I share wifi access in a big house and the connection is not ideal, once in a while it would go off (as when someone doing a big download hogging bandwidth), in those times I cannot access the internet even though network-manager shows that I am connected. 

That is not my problem, the problem is that after these interruptions Ubuntu (12.04) on my main machine (atheros card) seems to  be unable to reconnect (network manager shows that it is connected all the time, just cannot access web) whereas another machine with lubuntu 12.04 reconnects without problem (broadcom card). Moreover, cpu usage spikes after these interruptions and the top command shows that there are some processes called "migration/0" and "migration/1" eating up cpus (around 30%), these processes seem to kick in only when the system is trying to reestablish internet connection. The only way to restore connection and kill the migration processes would be to restart the machine.


Here is the info about the wifi card

```
 *-network               
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:77:52:40
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.5.0-18-generic firmware=N/A ip=192.168.2.43 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:f6000000-f600ffff


```

Any insight?

---

### Post by Bucky Ball on 2012-12-08
*Thread moved to **Networking & Wireless***

---

### Post by monkeybrain2012 on 2012-12-12
Bump!

---

