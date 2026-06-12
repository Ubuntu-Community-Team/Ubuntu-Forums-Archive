---
title: "Why aren't I picking up wireless networks?"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by B_Master_Flash on 2009-08-07
I'm using an HP laptop with an Atheros wireless card and running ubuntu 9.04 with madwifi installed.  I was using 8.10 previously and had the same problem.  My problem is that I don't seem to pick up any wireless networks.  From my Windows laptop I can see 4 different wireless networks, but when I left click on the network icon on the task bar there are no listed wireless networks.  I've tried manually loading the network that I'm using now, with the SSID and encryption information, but the icon shows that it's attempting to connect for a while and then gives up.  Am I missing some setting to pick up wireless networks?  I've seen that previous versions of ubuntu had a "roaming" mode that could be manually set but I couldn't find it anywhere in 8.10 or 9.04.

---

### Post by Aspra on 2009-08-07
I am having a similar problem. I have a Wireless card in a desktop and it is not detecting networks either. Although it does detect them in Live disc mode for some reason, but never connects to any.

---

### Post by superprash2003 on 2009-08-07
post output of **sudo iwlist scanning** from the terminal

---

### Post by B_Master_Flash on 2009-08-15
> **superprash2003 said:**
> post output of **sudo iwlist scanning** from the terminal

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

pan0      Interface doesn't support scanning.

---

