---
title: "dell wireless 1397 wlan mini-card help"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by salance on 2011-06-09
i just install ubuntu 11.04 using wubi and i cant get my wireless card to work like the title says its a dell wireless 1397 wlan mini-card. i have a dell inspiron  1545 but can some point out where thee drivers for it is please?

---

### Post by mikewhatever on 2011-06-09
As far as I know, the 'Dell wireless 1397 ...' is just a 'Broadcom 4312 802.11b/g'. You can verify that by running lspci. The driver is in the repositories, you just need to hook up a cable and install it using the Additional Drivers utility. It's under System->Administration in the Gnome2 interface, and if you use Unity, just type Additional Drivers in the search field. Alternatively, just search for 'bcmwl-kernel-source' in the Software Center and install it.

---

