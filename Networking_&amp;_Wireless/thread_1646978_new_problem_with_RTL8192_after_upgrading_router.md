---
title: "new problem with RTL8192 after upgrading router"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by rickbeton on 2010-12-16
Hi all,

I have been using my Samsung R620 laptop with no trouble since 10.10 came out and fixed the RealTek drivers. (Pre 10.10 I'd had to use ndiswrapper which was clunky but generally ok.)

Now I have a new problem. I upgraded my ADSL router from 802.11b/g to 802.11b/g/n. The new one doesn't have a way to disable 802.11n and the Samsung laptop wifi now doesn't work (my other laptops and smartphones all work OK).

What happens is that it fails when it's used. So suppose I log in to Ubuntu, start the wifi, it connects OK. It stays working until any significant data is transferred, then the wifi crashes in some way. For example, _apt-get upgrade_ runs a short while but soon freezes, then after a timeout starts complaining about DNS errors.

According to NetworkManager, the wifi is still working. But it clearly isn't.

lspci gives (in summary)
wlan0 RTL8192E Wireless LAN Controller (rev 01)
Kernel driver in use: rtl819xE

Any suggestions?
Rick

---

