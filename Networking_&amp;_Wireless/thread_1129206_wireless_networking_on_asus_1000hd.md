---
title: "wireless networking on asus 1000hd"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by woodsonoversoul on 2009-04-18
Hi all. Firstly, I know this is a common topic and there are many, many articles out there explaining this topic, but none of them have helped me, so I'll try here. My situation: I've been running ubuntu-eee on my laptop since I got it (~ 6 months ago) with no problems. Two nights ago I fell asleep with the laptop on (which I believe put it in suspended mode, which may have messed with the driver). Now I can see the wireless networks in range, but can't connect to them.

lspci -v | less says:
01:00.0 Network controller: RaLink Unknown device 0781
        Subsystem: RaLink Unknown device 2790
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at f8000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

Any Help?

---

### Post by woodsonoversoul on 2009-04-20
bump

---

### Post by calvinps on 2009-04-20
From what I read is that your laptop was running alright until three nights ago, but I cannot see how suspend mode would mess the drivers up.

I would like to know what type of driver you use.

Plus, I would also like to know what wireless card is in your laptop, so open a Terminal and type:

```
lshw -class network
```... and post the results when you're done.

---

### Post by woodsonoversoul on 2009-04-20
Thanks for the reply Clavinps! The results of 'lshw -class network' are:
 *-network               
       description: Ethernet interface
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:08:52:8c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1e driverversion=1.0.0.4 firmware=L1e ip=192.168.1.3 latency=0 module=atl1e multicast=yes
  *-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:22:43:24:52:11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless


but I may have the wrong driver installed. I've been following a bunch of tutorials and messing around with it...

---

### Post by woodsonoversoul on 2009-04-20
I followed the tutorials [here]("http://forums.remote-exploit.org/showthread.php?t=21707") and [here]("http://ubuntuforums.org/showthread.php?t=683085&page=3") and pretty much feel like I've smashed my wireless with a rock...

---

### Post by woodsonoversoul on 2009-04-20
And now I lost all wireless access points, I can't even see them. Please help if possible

---

### Post by woodsonoversoul on 2009-04-20
Alright, headed to school. Thanks for all the help so far! Keep it coming!

---

### Post by calvinps on 2009-04-20
Hmm, I looked at what says to be the driver, and it said "r2860" - could that be the driver you are using?

Also, I would like to know where you got it from.

Regards;

calvinps

---

### Post by woodsonoversoul on 2009-04-20
I'm between classes right now so I can't check, but I'll let you know when I get home in about 3 1/2 hours. Any other questions?

---

### Post by woodsonoversoul on 2009-04-20
I'm using 2008_0325_RT2860_Linux_STA_v1.6.1.0 for the driver. As to where I got it from, I don't know, one of the dozens of half-written tutorials I've been reading

---

### Post by woodsonoversoul on 2009-04-21
bump for today

---

