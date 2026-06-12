---
title: "Broadcom sees wireless networks, but doesn't connect"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by mohnkern on 2008-12-10
I recently decided to bite the bullet and install 8.10 hoping I could get wireless to work on my Aspire 9300.  Everything went flawlessly, including its discovery of my broadcom card, and the installation of the drivers.

It's seeing several wireless networks, so I assume that the driver is working right, but when I try to connect to my local non wep/wpa router, it says connecting for perhaps a minute, and then "disconnected."

I don't think it's the Linksys router on the other side, because it's working fine under Vista.

Anyone else see this where it's seeing the networks, but its not connecting to them?

---

### Post by dai_vernon on 2008-12-10
When this happened to me in Hardy with my Atheros 5007EG card, the problem turned out to be that my MAC address had an issue.  Running lspci showed me my wireless card and its MAC address, but there was a text file somewhere that needed to have my MAC address input to it.  I don't remember exactly where it was, and in fact I am trying to get that solved in Intrepid myself, because the site that had the info on it has 404'd.  Hope this helps.

---

### Post by mohnkern on 2008-12-10
Well for whatever reason, just reinstalling Ubuntu fixed the problem.

Not quite sure why, was just a guess.

---

