---
title: "Cable doesn't work, wireless does!"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by Moustaffa on 2010-01-16
Hi,

I can't connect tot the internet through the UTP Cable, but my wireless internet works. Usually when I click on the connection icon next to my clock, it should show eth0 (which is cable connection) and below it should show my wireless connections. Now it only shows the wireless connections...

I assume it's not a hardware problem because the wireless actually works (on it right now). Also, it happened right after something else happened: lately, sometimes when I boot my laptop, it shows my login in the kernel, my terminal appears in there and asks for my login and password. After I do so, it loads a few things and then stays in that terminal. Only when I press ALT + F8 it goes to my Ubuntu login screen...

Hope someone can help because this is really annoying

PS: when I plug in the UTP cable in my laptop it shows 2 lights, a red one and an orange one, flickering. So I suppose the cable is still OK and the problem isn't there.

---

### Post by Iowan on 2010-01-16
> **Moustaffa said:**
> I assume it's not a hardware problem because the wireless actually works (on it right now).:confused: Why does working wireless rule out a hardware problem with the wired connection? (Although it DOES sound like something else may be going on.) Do you have another cable you could try? **lshw -C network** should show details about interfaces.

---

### Post by Moustaffa on 2010-01-16
> **Iowan said:**
> :confused: Why does working wireless rule out a hardware problem with the wired connection? (Although it DOES sound like something else may be going on.) Do you have another cable you could try? **lshw -C network** should show details about interfaces.

Don't shoot me for being a newbie, it was just an assumption I made :)

This is the output I get for the sudo lshw -C network command

moustaffa@moustaffa-laptop:~$ sudo lshw -C network
[sudo] password for moustaffa: 
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1c:26:4a:0b:0c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=172.16.71.123 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:c0200000-c0203fff
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1_rename
       version: 02
       serial: 00:19:b9:88:c9:29
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no multicast=yes port=twisted pair
       resources: irq:21 memory:c0300000-c0301fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

Any useful interpretation that can be made out of this?

---

### Post by Iowan on 2010-01-16
I didn't mean to be critical...
I'm still not sure what to do with "vboxnet0", but it looks like the ethernet connection is called "eth1_rename". I've seen a couple of other similar threads - I'll try to search for them to see if any had a solution. Editing */etc/udev/rules.d/70-persistent-net.rules* is an option, but I don't remember if it helped.

---

### Post by drpjkurian on 2010-01-16
Hi
Just type ath0 in the field related to 'connection' 'name'.
you will get this when you double click the network manager icon near the clock.

---

