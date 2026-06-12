---
title: "Problems with BitTorrent clients"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by lamadredelsapo on 2010-07-31
I've a Ralink rt2500 wireless card that worked put of the box with the network manager but whenever I start a bittorrent client my internet connection gets killed. I'm using 10.04 x64 with all latest updates installed and haven't got a clue of why this is happening because using Vuze with the same config in windows worked like a charm. Should I try using ndiswrapper with the windows driver?

---

### Post by lamadredelsapo on 2010-10-13
It was all about the kernel rt2500 driver, after replacing it with ndiswrapper and windows driver vuze works like a charm.

---

