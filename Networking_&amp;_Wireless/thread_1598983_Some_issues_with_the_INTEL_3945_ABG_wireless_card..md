---
title: "Some issues with the INTEL 3945 A/B/G wireless card...."
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by ickyplush on 2010-10-17
I'm using an HP DV2175ea, equipped with a, until now, perfectly good wifi card. 

I have been dipping between 'buntus and 'doze and on occasion even Mac, but recently I've noticed (on 'buntu)

a) a drop in performance (speed), ran a couple tests on speedtest.com and came back with around 1.5mps on Ubuntu 10.10, but around 15mps on Leopard and over 20mps on 'dozey 7

and

b) occasionally on boot, everything connects just peachy, but when I attempt to browse le t'interwebs, just nothing, tried pingin a couple sites to no avil, host unreachable

essentially i wanna know has anyone else with a similar (or relevant) setup had/fixed a similar problem

and ive seen that the ipw3945 drivers are offered, as opposed iwl3945, is that worth a gander?

safe

---

### Post by Rybo85 on 2010-10-17
The slow download speed is apparently a known bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265)


I would suggest that you register at the ubuntu launchpad site and add yourself as one of the people affected by the bug. I would imagine that as the number of listed affected people increases, they will be more inclined to work on it.

---

### Post by chili555 on 2010-10-19
For the benefit of the searchers, I can report that the problem is not universal. I have a laptop with an Intel 3945ABG and speed tests show download speeds at or very near the maximum I have paid my ISP for. Another laptop using an Intel 2915ABG is the same.

---

### Post by QwUo173Hy on 2010-10-21
I'm having problems with it too. It can disconnect permanently, at any time - although I'm testing it now and it seems fine for the moment.

Also, it doesn't have the range that the other laptops in the house have. Unless I'm within a few meters of the router, and on the same floor of the house - it won't pick anything up. This goes for other routers too, so it's not router specific. I was considering trying Haiku, as I know they have drivers for this device in the nightly builds. But if they're all using the same Intel open source drivers then there mightn't be a difference.

edit: It's gone very slow now too.

---

