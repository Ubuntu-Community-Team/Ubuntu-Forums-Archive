---
title: "Wireless connection become flaky"
date: 2012-03-19
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2012-03-19
Box is running Lucid with 2 n/w cards. An ethernet, connected to 192.168.1.x and a wireless PCI card (using ndiswrapper RT61 driver) connected to 192.168.2.x

The wireless card has been fine for ages ... I used to run a continuous PING from another machine on the 192.168.2.x network, and it was rock-solid.

However, of late, the PING has become unreliable - both ways. It drops out every few seconds - but then picks up again. The average time when it succeeds is between 2 and 4 ms. However every few pings, it goes 100,1000 and then times out, before dropping back to around 4.

Could some process be causing this ? Can anyone tell me where to look in the logfiles to try and bottom this out ?

I did have this issue, when I was using the Ubuntu supplied drivers. Which is why I switched to the ndiswrapper version ....

---

