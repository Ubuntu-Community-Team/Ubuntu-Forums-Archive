---
title: "Port Forwarding with ICS"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by Trinexx on 2009-11-04
I'm sharing my internet connection with another computer over a crossover cable.

Modem >>> eth0 >>> My comp >>> eth1 >>> other comp


However, I can't figure out how to forward any ports. I set up ICS by following [this](https://help.ubuntu.com/community/Internet/ConnectionSharing) guide. Would someone mind pointing me in the right direction of a solution? I'd prefer not to use Firestarter/Guidedog/Whatever new-fangled iptables frontend the kids are using these days, if possible.

---

### Post by ant2ne on 2009-11-04
> **Trinexx said:**
> Firestarter/Guidedog/Whatever new-fangled iptables frontend the kids are using these days, if possible.I was just about to suggest firestarter because it has a wizard for just such a thing. I got to this last sentence and had to laugh at the wording. "new-fangled" LOL

---

### Post by Iowan on 2009-11-04
**ufw** may be even newer-fangled than Firestarter... 
I haven't used it (or the **gufw** GUI), so I dunno if it'll help.

---

