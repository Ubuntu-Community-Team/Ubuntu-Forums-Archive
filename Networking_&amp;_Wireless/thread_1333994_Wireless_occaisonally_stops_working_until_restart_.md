---
title: "Wireless occaisonally stops working until restart in karmic"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by allspiritseve on 2009-11-22
Once in a while, my wireless connection will just cut out. I know it's not my router, as my other laptop stays connected just fine. After the connection stops working it scans but doesn't find any wireless networks. It continues on like this until I restart, and then everything works fine. Any idea what the problem is?

---

### Post by coffeecat on 2009-11-22
> **allspiritseve said:**
> Any idea what the problem is?

Could be many things, but your post is short on hardware information. Let's start with the wireless chipset your device is using. It could be that you have one with a buggy driver in Karmic.

What is the make/model of laptop?

And, more specifically, to get the actual chipset of your wireless device (among other things), post the terminal output of:

```
sudo lshw -C network
```

---

### Post by allspiritseve on 2009-11-22
I'm running on a Dell Latitude e6400

Output of the command you gave me:
```
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:ad:19:eb
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.7-7 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f6fe0000-f6ffffff memory:f6fdb000-f6fdbfff ioport:efe0(size=32)
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fb:b5:ec:9a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.2.103 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f1ffe000-f1ffffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by coffeecat on 2009-11-22
Well - that's interesting. I was expecting a Realtek or one of the Atheros chipsets, but not:

> **allspiritseve said:**
> ```

  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fb:b5:ec:9a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.2.103 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f1ffe000-f1ffffff

```

Let me show you the equivalent part of the output from the Sony laptop that I'm posting from:

```
*-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fb:23:ac:d6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.64 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:d0500000-d0501fff
```Which is interesting, because my connection has been as steady as a rock in Karmic (in Jaunty too) and since I started using Karmic somewhere at the alpha stage. Which doesn't help you very much except to point out that the Karmic driver for your wireless is just fine. Which means we need to look elsewhere.

I would have suggested changing the channel your router is broadcasting on, in case you are getting interference from a neighbour's network on the same channel - or even from a baby alarm. But you say that the other laptop stays connected. Is this in the same room, or is the disconnecting one in a place where the signal might be weak, and/or you might be getting interference?

I'll have a ponder and post back if I think of anything else.

---

### Post by allspiritseve on 2009-11-22
> **coffeecat said:**
> Is this in the same room, or is the disconnecting one in a place where the signal might be weak, and/or you might be getting interference?
They are less than a foot from each other :P

---

### Post by coffeecat on 2009-11-22
> **allspiritseve said:**
> They are less than a foot from each other :P

That *might* be the problem. :wink: Could the signals from both be interfering and the other laptop winning? I don't know but I did have something similar happen when I brought my laptop too near the USB wireless nic of my desktop.

Try two feet. :) Or even opposite sides of the room!

---

### Post by allspiritseve on 2009-11-22
> **coffeecat said:**
> That *might* be the problem. :wink: Could the signals from both be interfering and the other laptop winning? I don't know but I did have something similar happen when I brought my laptop too near the USB wireless nic of my desktop.

Try two feet. :) Or even opposite sides of the room!
I don't know, I suppose that could be what's happening, but it seems unlikely because the one laptop can't connect to ANY network, not just the one the other is connected to. Not to mention I'm pretty sure it's happened while the other computer is off-- I will check next time it happens though.

---

### Post by icepirate420 on 2009-11-24
I have the same issue with a Broadcom chipset, and it's not due to signal interference because my laptop is the only wireless device. This problem started after I upgraded to Karmic.

---

### Post by JimHQ on 2009-11-28
I have been having the same issue with an Acer Timeline 3810T with the Intel 5100 wifi. It has been driving me nuts. 
I have been down several unproductive avenues - disabling ipv6, installing WICD to replace network manager and making sure I have the latest drivers. This evening I have updated my router firmware to see if it has any effect. Will let you know if I have any joy.
Jim.

---

### Post by Bakudan00 on 2009-12-01
I have the exact same problem on my Gateway nv5207u. I'm surfing along nicely and then all of a sudden my connection dies, even though the panel applet says I have one. I try to reconnect but all it does is ask me for the security passphrase over and over. Only a restart will fix it, and it happens several times a day. This has never happened with Win 7 on the same machine.

```

*-network               
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:1f:16:cc:c6:2a
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f0300000-f030ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wmaster0
       version: 01
       serial: 0c:60:76:1c:f5:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0400000-f040ffff

```

---

### Post by coffeecat on 2009-12-01
> **Bakudan00 said:**
> I have the exact same problem on my Gateway nv5207u.

You have the same symptoms, but you don't have the same problem, because....

> **Bakudan00 said:**
>        product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.

You have a completely different wireless chipset from the OP. However, I have good news for you. Simply install these two packages from Synaptic:

linux-backports-modules-karmic
linux-backports-modules-wireless-karmic-generic

Reboot, and your Atheros AR928X will work just fine.

**Edit:** assuming, that is, that you are running Karmic. You don't say.

---

### Post by Bakudan00 on 2009-12-10
I completely forgot about this thread. >_<

Well, I do have Karmic and I did what you told me, and so far it's working fine. My reception bumped up nicely too.

So, thanks a bunch. ;)

---

### Post by seattle vic on 2009-12-10
I've also had the problem since I installed Karmic; after about 3 to 4 hours, it disconnects and I usually have to do a cold start to get a reconnection.  Even restarting network-manager does not do it.

I also have the Intel 5100.  The laptop ran great for many months under 9.04 without a wireless hitch.

I read in another thread that there is a kernel fix, and I did make an addition to grub:

GRUB_CMDLINE_LINUX_DEFAULT="pci=use_crs quiet splash"

(the addition was pci=use_crs)  It didn't help.

I'll try loading the backport modules as suggested and get back to this thread.

---

### Post by coffeecat on 2009-12-10
> **seattle vic said:**
> I'll try loading the backport modules as suggested and get back to this thread.

The backports modules were a fix for the Atheros wireless chipset. But you might get lucky. I hope so.

---

### Post by seattle vic on 2009-12-11
I've been running with the backport modules installed for over a day now with no disconnects, which is encouraging, even though I have the 5100.  Usually I disconnect within 3 hours.  I'll do some heavy transfers from my laptop to one of my desktops tonight and see how it fares.

---

### Post by seattle vic on 2009-12-12
Now have been running for two days with the backports loaded with no disconnects.  I don't know what they do, but it's looking like the issue has been fixed.

---

### Post by adrian_nye on 2009-12-20
For me (on Acer 5810TZ) the backports cause the wireless to not work at all after suspend, although it does not disconnect if you leave it on.

Unfortunately for a laptop this in not an improvement.

---

### Post by Elif on 2010-01-08
> **adrian_nye said:**
> For me (on Acer 5810TZ) the backports cause the wireless to not work at all after suspend, although it does not disconnect if you leave it on.

Unfortunately for a laptop this in not an improvement.
I'm having the exact problem on my 5810TZ. As far as I can recall, I didn't have any  problems with Jaunty. I'm considering a new install of Jaunty. Has anyone confirmed wireless working with the 5810TZ in 9.04?

Looks like i'll be doing a reinstall this weekend, i'll update with my results. Thx for the quick reply.

---

### Post by bkratz on 2010-01-08
> **Elif said:**
> I'm having the exact problem on my 5810TZ. As far as I can recall, I didn't have any  problems with Jaunty. I'm considering a new install of Januty. Has anyone confirmed wireless working with the 5810TZ in 9.04?

See the second post in this thread, he is using 9.04.

[http://ubuntuforums.org/showthread.php?t=1226095&highlight=5810TZ](http://ubuntuforums.org/showthread.php?t=1226095&highlight=5810TZ)

---

### Post by Elif on 2010-01-10
> **bkratz said:**
> See the second post in this thread, he is using 9.04.

[http://ubuntuforums.org/showthread.php?t=1226095&highlight=5810TZ](http://ubuntuforums.org/showthread.php?t=1226095&highlight=5810TZ)
Okay, so I backed up to 9.04 and everything was great...

then I let the updates install, and i'm back to where I was with 9.10 :-/ Actually, it the wireless is less usable now. Which is weird because I looked through the updates to make sure that there weren't any wireless updates... I guess the bug is hidden in some kernel updates.

---

### Post by bama7474 on 2010-02-05
I'm experiancing the same weak wireless connection while other computers running win vista have excellent coverage.  I'm running Ubuntu Netbook Remix 9.10 on a Toshiba NB305 -N410BL...From Terminal:

*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:08:fc:f5:72
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=10.0.0.11 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:f4:71:4d
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:2000(size=256) memory:f0520000-f0520fff(prefetchable) memory:f0510000-f051ffff(prefetchable) memory:f0540000-f055ffff(prefetchable)

Any help would be great, thanks.

---

### Post by bama7474 on 2010-02-05
Hey I just tried the backport install and everything is working great I went from 30% to 70% signal strength, just wanted to say thanks.

---

