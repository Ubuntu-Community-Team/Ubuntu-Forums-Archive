---
title: "Wired connection on Packard Bell Easynote not working"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by grj23 on 2010-01-17
Hi All

My brother installed Ubuntu 9.10 on a Packard Bell Easynote NJ65.  He has a wired home connection, which seems not to be working now.  It was working with the same machine under Vista.

What are the first places I should look?  Any hints or clues or people with similar issues would be most welcome.:D

---

### Post by grj23 on 2010-01-17
So, unfortunately I'm trying to do this from a different continent and it's the blind leading the blind.  But this is what I've been able to gather but following some other hopeful looking threads (eg [this one]("http://ubuntuforums.org/showthread.php?t=1262808")).

"dmesg | grep eth0"
gave no response at all

"ifconfig"
showed information for lo only.

"sudo lspci"
revealed that the ethernet controller was BroadCom
and the network controller was RaLink

Adding 
```
auto eth0
iface eth0 inet dhcp
```
to the interfaces file didn't help.  (previously it was just
auto lo
iface lo inet loopback)

It sounds like it's a driver issue, right?  I'd love any advice!
I'll find out tomorrow whether wireless works for him...

---

### Post by Iowan on 2010-01-17
Check **lshw -C network** - should provide some more information.

---

### Post by grj23 on 2010-01-17
> **Iowan said:**
> Check **lshw -C network** - should provide some more information.

My suspicion is that it will give nothing of interest as he doesn't seem to have eth0 at all!  However, I'll get him to try and write back.

---

### Post by grj23 on 2010-01-18
> **Iowan said:**
> Check **lshw -C network** - should provide some more information.

So this is the output of that command:

```
william@william-laptop:~$ sudo lshw -C network 
  *-network DISABLED      
       description: Wireless interface 
       product: RT2860 
       vendor: RaLink 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: ra0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless 
       resources: irq:16 memory:ba000000-ba00ffff 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: NetLink BCM5784M Gigabit Ethernet PCIe 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       version: 10 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress cap_list 
       configuration: latency=0 
       resources: memory:ba100000-ba10ffff 
```

Would very much appreciate any help...

---

### Post by Iowan on 2010-01-18
Interface *seems* to be recognized as BCM5784M, but no driver is associated. I've seen other places/threads that associate the **tg3** driver with the BCM5784M. Found [this]("http://www.broadcom.com/support/ethernet_nic/netlink.php") link...

---

### Post by highboard on 2010-01-19
hi all

this is the the guy with the troubled laptop. Thanks for all your help so far. Sadly nothing worked yet.

I have downloaded, from another computer, the suggested file from broadcom but have no idea how to use or install it. I would need fairly detailed instructions as I have no idea what I'm doing!

Again, thanks all for the help. Hope we can resolve it. I'm even considering going back to *spit spit* windows!

---

### Post by Iowan on 2010-01-19
[Here]("http://ubuntuforums.org/showthread.php?t=1300245") is yet another link I found for Broadcom drivers... text suggests it is for wireless, though.
Kinda old, but same family: [BCM5787M]("http://ubuntuforums.org/showthread.php?t=811396")

I downloaded the driver ZIP file and peeked inside - there's a README.TXT that seems to explain the installation procedure. It seems to be similar to the  BCM5787M link (I didn't read it completely - or compare the two.)

---

