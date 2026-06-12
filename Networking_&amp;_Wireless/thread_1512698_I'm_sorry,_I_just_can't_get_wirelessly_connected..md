---
title: "I'm sorry, I just can't get wirelessly connected."
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by Milkmanyeti on 2010-06-18
I really want to use Ubuntu but my wireless card isn't working or something. I really cannot figure out what is wrong, and looking at others posts to try to find similar situations only confused me more. Can anyone help?
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e2:98:92
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.0.15 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe7fc000-fe7fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:69:3e:f2:54
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

---

### Post by bkratz on 2010-06-18
Look at posts 8 and 10 and then page two.

[http://ubuntuforums.org/showthread.php?t=1509557](http://ubuntuforums.org/showthread.php?t=1509557)

---

### Post by 11hjpphty76lkjj on 2010-06-18
I ran:

```
sudo apt-get install bcmwl-kernel-source
```

then rebooted and my broadcom wifi worked.

A

---

### Post by Naggobot on 2010-06-18
To me (and I am just guessing here) this 

> configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe7fc000-fe7fffff
  *-network DISABLED

means that there is a driver present but the network is disabled for some reason. 
Is there a red exclamation mark on top of wireless connection symbol in the top applet bar?

If there is try enabling the network by right clicking the symbol and say enable network. 

(This does not necessarily help since when my computer comes from hibernate the exclamation mark is there and network is disabled but I can not enable it. So far I have been unable to decipher this problem)

---

### Post by Milkmanyeti on 2010-06-18
Yes, there is the red exclamation point and I tried the tips in post #2 to no avail.

---

### Post by Milkmanyeti on 2010-06-18
Thanks so much for your help! I got it!!!

---

### Post by Naggobot on 2010-06-19
More than out of curiosity, how did you fix it? I could try the same solution.

---

