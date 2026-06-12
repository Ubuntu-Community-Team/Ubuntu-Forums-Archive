---
title: "Wireless pci card not working with encryption"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by wtc05 on 2008-12-29
Hi, I am using a trendnet wireless N pci card (tew-643pi) with a realtek 8190 chip. I am trying to connect to a netgear MR814v2 router but the connection fails whenever there is a wep key in place. When I remove the key I am able to connect just fine. I switched from 8.04 to 8.10 and started using wcid instead of network manager with no results. I am very new to linux and would greatly appreciate any advice to help fix this problem.

*Fixed - Got a new card.

---

### Post by fibo112358 on 2009-01-06
Hi,

I just bought the same card and was up til 2 last night trying to get it to work...

[http://ubuntuforums.org/showthread.php?t=1031999&highlight=trendnet]("http://ubuntuforums.org/showthread.php?t=1031999&highlight=trendnet")

so you disabled WEP, ultimately replacing the card. I'll let you know if I ever find a fix...sure would be nice to actually use this card since it looked so cool with the dual antennaes.

---

### Post by fibo112358 on 2009-01-06
Ok that makes two of us...disabled WEP and am now connected. I was/am using ndiswrapper to run the latest driver from [www.trendnet.com](www.trendnet.com) (its called net8190p.inf I believe). Maybe a different type of security will work.

I noticed you didn't get any replies to your problem as well. I haven't got any replies from [www.LinuxQuestions.org](www.LinuxQuestions.org), so it seems that this card is unfamiliar territory.

---

