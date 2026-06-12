---
title: "How do you choose between wifi hotspots with the same SSID?"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by ireneshusband on 2010-01-24
Hello.

I access the internet through a hotspot with the SSID "OzoneBE.net Open Access". Unfortunately this hotspot is massively overused, and on top of that the signal is weak. There are other hotspots with the same SSID nearby. They have weaker signals, but it's possible they may not be so heavily used, or that I might be able to find a line of sight to one of them, so I would at least like to try connecting to them.

Unfortunately KNetworkManager doesn't give you any way of choosing between these different access points and it automatically selects the most powerful signal, as far as I can tell. RutilT *can* distinguish between them, but when you try to connect to the one you want, it seems that KNetworkManager intervenes and chooses the alternative with the strongest signal again. However if I kill KNetworkManager, RutilT just won't connect to anything. It fails without explanation.

How can I get proper control over my network management so that I can connect to the hotspot of my choosing, regardless of whether it shares an SSID with another?

Thanks in advance :)

---

### Post by jk007 on 2010-01-24
You can try to lock your PC to a specific channel/frequency.
iwconfig && iwlist wlan0 scan

---

