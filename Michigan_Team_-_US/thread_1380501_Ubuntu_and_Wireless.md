---
title: "Ubuntu and Wireless"
date: 2010-01-13
forum: Michigan Team - US
---

### Post by volzec on 2010-01-13
Now, that I have introduced myself, I have a question. How do I fix the wireless instabilities in Ubuntu 9.10 with wireless? This has become quite annoying and I can not find a good fix. Everything I have seen says to disable IPv6. :(

---

### Post by castrojo on 2010-01-15
This will depend on what chipset the wireless card is: Can you run "lspci" and paste it here?

---

### Post by volzec on 2010-01-17
Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
is what I get from running *lspci*. I did some research and tried some of what I found. I then figured that I would try installing the drivers from the CD, and that seems to have fixed things. Using OpenDNS helps too.

---

### Post by volzec on 2010-01-17
Actually, it is not fixed liked I thought. I am still having the problems with the connection being unstable. The installation of the drivers of the CD seems to have only helped a little. As always, I welcome any input on this matter.

---

