---
title: "WARNING! Do not buy Netgear WNA1000 adapter"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by bertmollar on 2010-03-03
This thing sucks. I have spent the last week trying everything from custom .inf files to using WG111 drivers. It simply will not work. Avoid this wireless usb adapter at all costs.

Does anyone have recommendations on a good solid working network card for ubuntu?

---

### Post by jclemmons on 2010-03-03
I've had pretty good luck with RT2870-based USB adapters.  The two I currently use are the Linksys WUSB600 and the D-Link DWA-160 (Rev. B I think) and both work nicely.  I found the Linksys as a refurb for $40 at Microcenter.

The drivers are included as staging drivers in Karmic (I had to blacklist the rt2800usb module to make them work properly), otherwise you can compile your own drivers.

---

