---
title: "panic, going abroad and no wlan"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by An3Azz on 2006-07-07
Hi, I'm pretty new at linux and ubuntu and I tried to install it on my laptop, with sucess. Everything worked except the Belkin f5d7011 wireless pcmcia card that I've got. A little bit of googling did the trick and I came up with info that my card had bmc43xx chipset. Well searched ubuntu's site for answers, stumbled on to a guide. Did everything by the book, the card is recognized and I guess it's started up and works (one of the green light's is on) But the damn thing wont connect to my router (D-link 624+). Is there something that I can do? If it's not which wlan pcmica cards work right out of the box with ubuntu? I am going to buy one today if there is no way to get my bmc43xx based card going, because I really need my wlan because I'm going abroad to work on Monday. :mrgreen:

---

### Post by raldz on 2006-07-07
Have you tried installing ndiswrapper?

```
sudo apt-get install ndiswrapper-utils
```

---

### Post by An3Azz on 2006-07-07
Yes but when I do that I get a lot of error msgs, Cant describe them atm because I'm not at my own computer. Is'nt there some step by step guide to ndiswrapper under 6.06 for n00bs such as myself?

---

### Post by raldz on 2006-07-07
Just what kind of errors do you get? Could you post it here? At the moment, try reading the Howto's of ndiswrapper in the wiki page of Ubuntu:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by An3Azz on 2006-07-08
> **raldz said:**
> Just what kind of errors do you get? Could you post it here? At the moment, try reading the Howto's of ndiswrapper in the wiki page of Ubuntu:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I have managed to solve the poblem thanks to this forum, I'm using the driver included in ubuntu now and it works fine, except for a little packetloss when using the wlan.

---

