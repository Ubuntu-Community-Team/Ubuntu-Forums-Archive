---
title: "WPA option?"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by Xoanan on 2009-06-09
Hi All

I just got my wireless network working on Xubuntu 9.04 but I noticed something.  In the network manager, there does not appear to be a WPA option for security.  I see WEP ascii and WEP Hex, but no WPA.

Is this the norm or is there something about my card that prevents WPA on Xubuntu?

Just curious.

My card is a Gigabit PCI card btw!

---

### Post by reeseslover531 on 2009-06-09
What kind of Gigabit PCI card are you using? you can find out by running ```
 lspci 
```  also I can't remember because I use Wicd (another option you might want to try) but I think the option won't show up unless the connection you are connecting to offers WPA.

---

### Post by Xoanan on 2009-06-09
Thanx; I will post it when I get back; 

I know the router offers WPA and was originally set up for WPA; I changed it to WEP because I did not see the WPA option in the network manager

---

### Post by Xoanan on 2009-06-09
> **reeseslover531 said:**
> What kind of Gigabit PCI card are you using? you can find out by running ```
 lspci 
```  also I can't remember because I use Wicd (another option you might want to try) but I think the option won't show up unless the connection you are connecting to offers WPA.

Here we go

```
01:0b.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: Giga-byte Technology Device e934
	Flags: bus master, slow devsel, latency 64, IRQ 9
	Memory at ff8f8000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci
```

---

### Post by reeseslover531 on 2009-06-10
Check [this ]("http://ubuntuforums.org/showthread.php?t=832809")forum post out, it should be of help

---

