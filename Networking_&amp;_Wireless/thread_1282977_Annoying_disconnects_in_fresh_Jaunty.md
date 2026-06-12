---
title: "Annoying disconnects in fresh Jaunty"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by bitchballs on 2009-10-05
I just installed a fresh jaunty and the wired ethernet is acting very strangely.  Every several seconds I have to disconnect and reconnect it.  It seems to be constantly freezing up.  This is not only very annoying but is preventing me from downloading any packages or updates.  I have to disconnect/reconnect just about every 15-10 seconds.  I have no idea why this would happen.  I have been googling for a few hours and can't find anyone else with the same issue.

---

### Post by oboedad55 on 2009-10-05
> **bitchballs said:**
> I just installed a fresh jaunty and the wired ethernet is acting very strangely.  Every several seconds I have to disconnect and reconnect it.  It seems to be constantly freezing up.  This is not only very annoying but is preventing me from downloading any packages or updates.  I have to disconnect/reconnect just about every 15-10 seconds.  I have no idea why this would happen.  I have been googling for a few hours and can't find anyone else with the same issue.

If you'll tell us what kind of computer and, even better, what wireless adapter you have you'll start to get some responses.

---

### Post by bitchballs on 2009-10-05
Its a Sager NP5793.

lshw gives me this:

*-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 01
                serial: 00:90:f5:8c:d8:77
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.116 latency=0 module=r8169 multicast=yes



Oh lawd.  Now items are randomly appearing in the menu panels, then rearranging and disappearing.

---

### Post by bitchballs on 2009-10-05
I have now read in another thread that this is a kernel issue with this adapter going back a couple of release versions.  Apparently the newest kernel is fixed.  I'm updating now.

edit: nope, still a problem.

---

### Post by oboedad55 on 2009-10-05
> **bitchballs said:**
> I have now read in another thread that this is a kernel issue with this adapter going back a couple of release versions.  Apparently the newest kernel is fixed.  I'm updating now.

edit: nope, still a problem.

Have you booted up a LiveCD of 9.10, karmic? It might be worth a try to see if your problem has been addressed. I'm not necessarily recommending karmic because it's still in beta testing and won't be ready for release until the end of the month. OTOH, if it works... Even running a beta you'd get all the updates that come along up until it's released at which point your system would be up to snuff. Just an idea.

---

### Post by bitchballs on 2009-10-05
May as well.  Gonna have to update sooner or later anyway.

---

