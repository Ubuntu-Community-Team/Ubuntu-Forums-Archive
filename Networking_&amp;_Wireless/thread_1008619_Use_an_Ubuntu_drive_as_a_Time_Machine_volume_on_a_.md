---
title: "Use an Ubuntu drive as a Time Machine volume on a Mac"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by jamieh on 2008-12-11
I tried posting this on MacNN but never got an answer.

Is it possible to plug a USB hard drive into an Ubuntu server and use it for Time Machine on an iMac on the same network?

Thanks

---

### Post by jmoorse on 2008-12-12
It has to be formatted HFS+, but will (should) work over the network.  Don't know about Ubuntu's implementation of HFS+ or how SAMBA would handle it

---

