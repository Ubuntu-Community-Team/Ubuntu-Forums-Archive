---
title: "Trying to get an old PCMCIA SMC wireless card to work"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by alikmodi on 2012-03-20
Hi all,
I am a total Ubuntu newbie, I installed 11.10 on an old laptop and have been having a blast poking around and learning the interface. 

However I am running into a problem with getting my old wireless card to be recognized by the OS. I have done some Goggling and have found some articles that talks about some drivers and kernel updates but nothing on the model of card I have. 

Do I need to get a special driver or is there a universal driver I can use? 

Any help would be great! Thanks a lot.

SMC Card: 
EZ Connect Wireless
Model No.SMC2632W

---

### Post by gordintoronto on 2012-03-20
It's admirable that you are trying to extend the working life of an 11-year-old card, but just barely realistic. If you have the Windows driver, you could try ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Bear in mind that the old card is very slow, and it may slow down your entire network.

On the other hand, I bought a dandy 802.11N USB adapter for $20....

---

