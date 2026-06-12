---
title: "Ethernet Ubuntu PC to Windows XP wireless laptop"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by hougSTAR on 2008-12-27
Hi.

I have read the how-to on internet connection sharing, but I am getting no love for an internet connection:(   

My set up that I am trying to get to work is as follows:


[Ubuntu desktop] - Ethernet Cable - [Windows XP laptop] - Wireless Connection - [Wireless Router] - [ADSL modem] - [La la land]


Is there any way to get my Ubuntu box to recognize the wireless card on my XP laptop, and use it? I have tried to turn my laptop into a Gateway, and it still will not even see the laptop.

I'm quite new to Ubuntu, obviously.  It would be much easier to experiment with if I can get a connection from my room and not have to haul the desktop to my router and hard wire it.

---

### Post by cabbiinc on 2008-12-28
> **hougSTAR said:**
> Hi.

I have read the how-to on internet connection sharing, but I am getting no love for an internet connection:(   

My set up that I am trying to get to work is as follows:


[Ubuntu desktop] - Ethernet Cable - [Windows XP laptop] - Wireless Connection - [Wireless Router] - [ADSL modem] - [La la land]


Is there any way to get my Ubuntu box to recognize the wireless card on my XP laptop, and use it? I have tried to turn my laptop into a Gateway, and it still will not even see the laptop.

I'm quite new to Ubuntu, obviously.  It would be much easier to experiment with if I can get a connection from my room and not have to haul the desktop to my router and hard wire it.

It may very well be your Windows machine. I had a similar problem but mine was all wired and using Vista as a server. I don't know if XP is the same (in fact I think it's not) but I had to go into the connection sharing center and add both my USB (to my DSL modem) and my ethernet (to Ubuntu) to a bridge. I then had to go into the properties of the bridge and update (which gave me a warning that the updated driver was not signed but I did it anyways) and that unlocked a lot of what was the problem.

Can you ping XP from Ubuntu? I used [http://www.majorgeeks.com/PingEasy_d5696.html](http://www.majorgeeks.com/PingEasy_d5696.html) from my Windows machine. You can ping an entire range (compared to just one address) and find the IP address of your modem and XP and possibly your Ubuntu box.

---

