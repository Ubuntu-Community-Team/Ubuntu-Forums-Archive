---
title: "A wifi chronology 8.04 to 9.04"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by paulbary on 2009-04-26
I've noticed an interesting trend on several machines I use Ubuntu on and
a collection of wifi cards. (DLink 1320/2320/552 all using various Atheros chipsets and a Linksys WMP54G V4.1 Ralink Chipset).

On 8.04, all of these cards worked flawlessly out of the box and never  lost connections. In 8.10 the Atheros based cards all began to intermittently drop connections which could be re-established using network manager ... same symptoms with several different router brands and models. With 9.04 alpha's, beta, and final, all the Atheros and Ralink cards have started doing this. So, today I loaded ndiswrapper and windows drivers for the Dlink 2320 and the connection has been stable as a rock. (on a 9.04 box)

Has anyone else noticed anything similar ... my half baked thought is thatthe wireless implementation in later version kernels may be the source. Just curious about what others may be seeing ...

Paul

---

