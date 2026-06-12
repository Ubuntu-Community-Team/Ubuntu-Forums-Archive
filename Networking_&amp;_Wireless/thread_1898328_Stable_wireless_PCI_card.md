---
title: "Stable wireless PCI card"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by runesvend on 2011-12-21
Hello everyone

I'm looking for people who have personal experience with a stable wireless PCI NIC for Ubuntu (or just Linux in general). I'm right now using a TP-Link TL-WN821N USD dongle which is quite unstable.

I have done quite a bit of Google searching, and it's easy to find a lot of threads on how to fix an instability problem with card X/chipset Y, but I haven't found any threads where anyone have actually recommended a card they've found to be stable.

The PC in which the card is to be used will be connected to via SSH over the internet. So stability is crucial, as if it loses its network connection, it will be unreachable.

Thanks for your input!

---

### Post by kurt18947 on 2011-12-21
I can't use a PCI card in my desktop configuration but have 2 USB dongles that give stable connections in newer Ubuntu versions, 11.xx.  


[LIST=1]
[*]Netgear WNA1100. This uses an Atheros AR9271 chipset and supports N150 and G speeds
[*]TrendNet TEW-649UB. Smaller size and works well for portables. Uses a RealTek rtl8192SU chipset.  Same speeds, N150 and G.
[/LIST]
I've not used either with SSH but both are stable with WPA2 connections.  Both adapters will work in earlier Ubuntu versions but require work/tweaks to work well.

---

