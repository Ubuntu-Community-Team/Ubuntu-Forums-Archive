---
title: "Driver for Edimax cards"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by Chris62 on 2009-06-24
Hi,

I am thinking of installing WiFi in my dual boot (Windows XP/Ubuntu 9.04) machine and my laptop and have ordered an EdimaxEW-7128G PCI card for my desktop machine and an Edimax EW-7108PCG for my laptop. I have also ordered a PCMCIA card for my ADSL modem which is supplied by my ISP who set the card up on line. Edimax supply a driver which is in source code. Would some kind person tell me how to turn the source code into a driver, please?

I won't be able to do anything until the various cards arrive but would like to be prepared fro them by having a driver for the Edimax cards.

---

### Post by jerrrys on 2009-06-25
check this out

"Hi, I have exactly the same card (Edimax EW-7128g) and it works 'out of the box' on Ubuntu (tried it on Dapper, Edgy and Feisty). If you're concerned about the driver, it uses the rt2500 open source driver from [serialmonkey]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page"), but as long as its recognized 'out of the box' by ubuntu, who cares about the driver" quote from [http://ubuntuforums.org/showthread.php?t=490345](http://ubuntuforums.org/showthread.php?t=490345)

found it here

[http://www.google.com/search?q=EdimaxEW-7128G+driver+linux&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=EdimaxEW-7128G+driver+linux&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Tofu_Madness on 2009-08-03
> **jerrrys said:**
> check this out

"Hi, I have exactly the same card (Edimax EW-7128g) and it works 'out of the box' on Ubuntu (tried it on Dapper, Edgy and Feisty). If you're concerned about the driver, it uses the rt2500 open source driver from [serialmonkey]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page"), but as long as its recognized 'out of the box' by ubuntu, who cares about the driver" quote from [http://ubuntuforums.org/showthread.php?t=490345](http://ubuntuforums.org/showthread.php?t=490345)

found it here

[http://www.google.com/search?q=EdimaxEW-7128G+driver+linux&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=EdimaxEW-7128G+driver+linux&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Hey, thanks for the info. I was looking for EDiMAX EW-7128G driver installation guide and stumbled upon your post. Tried it out right a way, and hey what do you know it works out-of-the-box just like you said. 

However, for some strange reason the wireless signal strength is only ~75% even when the router is right next to the antenna. Although I'm not sure if this has anything to do with the lack of a driver, I might try to install the official EDiMAX driver sometime later today (I get full bars in Windows Vista with the EDiMAX driver...)

Thanks again! :D

---

