---
title: "Wireless will not connect with IPv6"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by tagno25 on 2010-05-04
I cannot connect to wirelessly when I have IPv6 enabled for the wireless network card.  It works great on ethernet, but if I enable it for the wireless card then I cannot even get IPv4.

---

### Post by Iowan on 2010-05-04
Curious - do both connections go through the same router?

---

### Post by tagno25 on 2010-05-04
Both go through the same router.  My rooted Android phones, Windows 7 laptop, and another Ubuntu laptop all work fine with IPv6 on the wireless.

---

### Post by tagno25 on 2010-05-06
my Wireless card is a "Atheros AR5008" if that matters, or that is what is is according to lspci.

```
05:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
	Subsystem: Apple Computer Inc. Device 0087
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at c0200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

---

### Post by tagno25 on 2010-05-06
I found out that it is not related to the wireless.  Ubuntu (or possibly network-manager) will not allow multiple IPv6 addresses on the same computer.

---

### Post by idef1x on 2010-05-16
Looks like i've the same problem, but my ubuntu laptop gets a global ipv6 address from my ipv6 router (via a radvd daemon), so that should be fine. However no connectivity :(
When changing to ethernet connection it works all fine?? 
Anyone an idea?

---

