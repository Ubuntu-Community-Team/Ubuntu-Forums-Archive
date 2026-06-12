---
title: "Gateway NV54 laptop wireless not working in ubuntu 11.04, 12.04"
date: 2012-12-15
forum: Networking &amp; Wireless
---

### Post by a109 on 2012-12-15
The internal wireless card of my NV54 Gateway laptop doesn't work under ubuntu, I've installed ndiswrapper and tried all different drivers but no luck. In 11.04, I still can get the wifi source list, but cannot connect. In 12.04, even no wifi source can be found. Any idea? Many thanks!

---

### Post by a109 on 2012-12-16
solved, just ensure you installed ndiswrapper-source, ndiswrapper-dkms, ndiswrapper-common and ndiswrapper-utils-1.9, as another thread mentioned, then pick right winxp driver.

---

