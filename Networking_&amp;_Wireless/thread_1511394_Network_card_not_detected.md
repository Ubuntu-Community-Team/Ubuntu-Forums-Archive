---
title: "Network card not detected"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2010-06-16
I'm in serious need of some help. The network adapter on the motherboard of my main machine apparently failed about noon today. This machine serves as the firewall and router for my home office LAN, and so it has two network adapters, the second being a PCI card installed in the only PCI slot of the mobo. The mobo's adapter served the WAN while the PCI card serves the LAN.

Since the mobo has only one PCI slot, none of the other PCI cards I have on hand could be used. Instead, I pulled an unused PCI-e dialup modem card from the machine, and bought a PCI express gigabit card to put in its place.

The problem is that the machine (running Hardy 8.04.4 LTS) does not recognize the new card at all. Running lspci shows only the old PCI card that serves the LAN. Similarly, running "sudo lshw" shows only the old PCI card together with a virtual adapter that's part of my VirtualBox installation on that system.:confused:

I then dual-booted into Vista Home and attempted to install the new card there, using the CD that came with it. Vista detected the card and asked for the disk, but then was unable to find any drivers on the disk!:confused:

The box says the card is from Star Tech, and the instruction sheet says its model is ST1000SPEX.

If anyone can point me to the correct module to add to the startup list and/or remove from the blacklist, that may get me going again. Any ideas as to better ways to detect the card, in addition to lspci and lshw, neither of which find it, will also be gratefully received.

---

### Post by JKyleOKC on 2010-06-16
Well, I'm back on line at least for now, but my searches of the forum indicate that the r8169 driver I'm using to get there may not be the most reliable thing in the world. Searching StarTech's support site gave me a driver name, and searching here for that name gave me enough to get me started on the comeback trail.

I'm still puzzled as to why the card was not detected during boot time; I had to add the driver to /etc/modules, then modify my /etc/udev renaming rules to force it to be known as "eth1." Once I had done this, my connectivity came back on rebooting.

However I'll leave this thread open for a few days in hopes that someone will shed a bit of light on the mystery aspects of this not-very-productive half day...

---

### Post by JKyleOKC on 2010-06-17
No joy. The interface is down again this morning. Syslog showed only that transmissions began timing out at 4:27 a.m. local time.

I replaced the r8169 driver with the latest version r8168 driver from StarTech's web site and re-booted, but that took me back to square one with the card no longer being detected at all!

Attempted to regress to the r8169 driver but it's no longer found by modprobe.

Hellllp!!!

---

### Post by JKyleOKC on 2010-06-17
Success (of a sort) at last. Some of the corrective techniques I used trying to make the r8168/9 drivers work apparently cleared the blockage in the mobo's network adapter that had (wrongly) convinced me it was toast. When I re-enabled that adapter and restored the original configuration of /etc/udev/rules.d/70-persistent-net.rules, everything came back to life.

The PCI-express adapter with the Realtec 8168B chip in it still is not being recognized during the boot process, but now it doesn't matter. I'm marking the thread as solved.

---

