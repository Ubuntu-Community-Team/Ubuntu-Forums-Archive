---
title: "Massive 64% packet loss"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by DyBurke on 2011-08-13
Hello everyone,

First, forgive me if this is a repeated post, but I've looked around and couldn't find a post that addressed my particular issue.  I have a computer that is connected to a WRT54G v8 with dd-wrt on it via hardwire ethernet cable; no wireless. I was previously using a Netgear WGT624 v3 (no mods) and experiencing the same issue.

The issue is that while operating in Ubuntu 11.04 64 bit, whether it be the install located on my HD or a live-usb ver, I experience massive intermittent packet loss, 64% or so.  I DO NOT experience this packet loss on Windows installed on the same machine on a separate partition.  I have a TZ68A+ motherboard and I'm using the on-board Realtek RTL8111E - 10/100/1000 Controller to connect to my router, again, via a hardwire ethernet cable.  I've tried multiple cables and multiple routers, I've also tested the cables/routers in other environments with different devices, none of them are the issue.

It may be a driver issue but I was under the impression that the correct driver modules were in this kernel.  Maybe not in the 64 bit version of 11.04?

Any help would be appreciated.  I can post any information people would like.  Thanks in advanced.

Last ping results:
```
--- 192.168.1.1 ping statistics ---
311 packets transmitted, 152 received, +59 errors, 51% packet loss, time 310118ms
rtt min/avg/max/mdev = 0.665/0.785/11.468/0.870 ms, pipe 4

```

lspci -nn results for ethernet card:
```

...
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
...

```

sudo lshw -C network results:
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 00:30:67:cb:5b:38
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.39 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff

```

**Update:**
I just uninstalled network-manager and manually configured /etc/network/interfaces with eth0 having a valid static IP and it doesn't seem to make a difference. :/

---

### Post by varunendra on 2011-08-14
> **DyBurke said:**
> 
```
*-network               
       description: Ethernet interface
       product:** [COLOR=DarkRed]RTL8111/8168B[/COLOR]** PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       configuration: autonegotiation=on broadcast=yes [COLOR=DarkRed]**driver=r8169 **[/COLOR]driverversion=2.3LK-NAPI duplex=full ip=192.168.1.39 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s

```
Hope this makes the difference you need: [http://ubuntuforums.org/showpost.php?p=11053381&postcount=6](http://ubuntuforums.org/showpost.php?p=11053381&postcount=6)

---

### Post by DyBurke on 2011-08-14
> **varunendra said:**
> Hope this makes the difference you need: [http://ubuntuforums.org/showpost.php?p=11053381&postcount=6](http://ubuntuforums.org/showpost.php?p=11053381&postcount=6)

You, my friend, are a gentleman and a scholar.  :D You've brightened my day.  Thank you for solving that.

---

### Post by varunendra on 2011-08-14
> **DyBurke said:**
> You, my friend, are a gentleman and a scholar.  :D You've brightened my day.  Thank you for solving that.
You're welcome!

And thanks for the compliments :) I think I just got lucky to get that solution post from which I had almost just copy-pasted the method and commands. Knowing a solution is good, but knowing the exact reason of the problem is definitely great!

---

### Post by DyBurke on 2011-08-14
> **varunendra said:**
> You're welcome!

And thanks for the compliments :) I think I just got lucky to get that solution post from which I had almost just copy-pasted the method and commands. Knowing a solution is good, but knowing the exact reason of the problem is definitely great!

One quick question though, how do I get that module to load on boot?  I just rebooted and had to reload it.

**Update:**
I added the line 'r8168' to /etc/modules.  I think that's the correct way to do it.  I'm rebooting to test.

**Update:**
Worked like a charm. :)  Thanks again.

---

### Post by varunendra on 2011-08-14
> **DyBurke said:**
> 
**Update:**
I added the line 'r8168' to /etc/modules.  I think that's the correct way to do it.  I'm rebooting to test.
Yeah, that's the correct way to do it if a module is not loading by default. Generally, when a default choice is 'blacklisted', the alternate one is loaded by default. But sometimes we need to 'tell' the kernel about the 'alternate' choice by adding it in /etc/modules file.

Hope it doesn't give you troubles anymore :)

---

