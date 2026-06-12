---
title: "Terrible Reception with NETGEAR Wi-Fi Card"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by Unanimated on 2009-10-18
Today, I installed a NETGEAR Wi-Fi card (with the antenna sticking out of the back), and lspci reports it to be:
```
02:01.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

```
The problem is, I have a Wireless G router literally *right* above me, but yet I can only get about 30-35% reception, or so Ubuntu reports. Honestly, I got better reception with the Nintendo Wi-Fi USB Connector which Ubuntu hacked to be a Wi-Fi card. Is there a way I can make the signal strength better?

---

### Post by arvevans on 2009-10-19
Not an expert here but...
[LIST]
[*]Assuming you own the WiFi hub, try another channel.  You may have interference from another WiFi hub on the same channel.
[*]Lay both antennas (WiFi Hub and your PC Card antenna over to horizontal positioning.  there is very little signal off the tip of the antenna.  Radiation is in a ring, like a doughnut or bagel slid over the antenna
[*]Try a different computer with a different WiFi card on the same hub.  This helps to isolate the problem to being with the Hub, or being with your computer & WiFi Card.
[*]Try your computer with a different WiFi Hub.  This helps to isolate the problem to being with your WiFi hub, or with your computer and WiFi card.
[/LIST]

Marginal signal strength could cause massive amount of packet resend requests, which will be seen as an apparent slow link, when the data clock rate is fast.

It is possible to set (reset) the transmit power level on most WiFi cards.  Default mode is for them to increase power automatically until data errors are minimal.  See the man page for "iwconfig" for info on changing radio link power levels.

_._

---

