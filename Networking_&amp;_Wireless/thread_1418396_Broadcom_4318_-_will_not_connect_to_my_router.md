---
title: "Broadcom 4318 - will not connect to my router"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by cinosa on 2010-02-28
Ok, so spec's on my setup: Ubuntu 9.10 on a Dell Inspiron 530.. Q6600 w/3GB RAM, 500 GB HD w/radion 2600xt and broadcom wlan NIC.. my issue is that the broadcom will not connect to my router.. did some searching, found a link from this site detailing how to get my NIC to work on Intrepid, but that's not what I have.. I followed that guide anyway, substituting my driver for his (guide is on sampbar.com) and nothing. It's showing now as not ready. I've installed ndiswrapper and grabbed the drivers for my NIC from my Vista install, but when I use ndiswrapper to do that, I get an error saying it can't tell if the hardware is present, then showes me it is present and it still won't connect. Any idea's here?

---

### Post by cinosa on 2010-02-28
I fixed it.. Ubuntu was loading the b43 driver, which was trying to control the card. I followed the "Comprehensive ndiswrapper troubleshooting guide" at the top of this forum (which I should have done in the first place) and it said to blacklist the default driver, which worked. This reply is from within ubuntu.

---

