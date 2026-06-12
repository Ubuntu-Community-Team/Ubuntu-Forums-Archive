---
title: "Wireless only works for a few minutes at a time"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by kcrouse on 2011-08-08
Hi all,

I have a weird issue with my new laptop, a Toshiba Portege 835 using 11.04.  

The wireless card shows networks and connects to them, and then operates normally for a few minutes.  Then, while still connected, it stops working - or rather it stops transmitting any data.  I've verified that this happens for multiple routers and no information is transmitted either in the intranet, for the internet, or to the router itself. I can disconnect and reconnect to the same wireless network and get a few more minutes of activity. 

Any thoughts on why this is?

Kevin

lsmod suggests it is using this :
cfg80211              178528  3 iwlagn,iwlcore,mac80211


lscpci : 

04:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
	Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1305]
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at c2600000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3

---

### Post by wildmanne39 on 2011-08-08
Hi, run these commands please:
```
lspci -nn
lsmod | grep acer
rfkill list all
```
and post the results here.
Thank you

---

