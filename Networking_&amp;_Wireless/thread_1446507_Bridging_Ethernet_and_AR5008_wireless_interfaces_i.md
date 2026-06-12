---
title: "Bridging Ethernet and AR5008 wireless interfaces in UNE 9.10"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by ewan_coldicott on 2010-04-04
Hi guys

I'm trying to connect my desktop computer (running Ubuntu Desktop 10.04 beta 1) to my home LAN and don't have a long enough network cable. I have an eee PC 901 running Ubuntu Netbook Edition 9.10 with an Atheros AR5008 WLAN card, which uses the ath9k driver. How do I bridge the WLAN and Ethernet interfaces on the eee so I can connect my desktop to my home LAN (which has a wireless AP), via the eee? 

I've googled it a bit and most pages say only Ethernet devices can be bridged - these pages are from ~2006 though so I thought it might be possible to bridge WLAN/Ethernet now? I've got bridge-utils and tried to add both devices to a bridge then bring the bridge up. The netbook could still access the internet but the desktop didn't pick up a network on its Ethernet interface connected to the netbook. My home LAN uses DHCP not static addressing.

Any tips would be much appreciated.

---

