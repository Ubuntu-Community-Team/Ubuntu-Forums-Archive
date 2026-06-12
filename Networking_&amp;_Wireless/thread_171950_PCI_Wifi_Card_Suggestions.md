---
title: "PCI Wifi Card Suggestions?"
date: 2006-05-07
forum: Networking &amp; Wireless
---

### Post by yoink23 on 2006-05-07
Hello all.  I need a wireless card for the summer to connect to an 802.11b wireless router.  I have a desktop, so I'm looking for a PCI card.

Here's the question.  Which is the cheapest desktop 802.11b wireless card that is natively supported in ubuntu and where should I look to buy it?  I've looked at the compatibility list but it doesn't always say whether the cards are pci or not, nor are the cards on the list always easy to find for sale.  

Thanks in advance all!

---

### Post by Sendervictorius on 2006-05-08
My advice is don't go cheap. I bought cheap, my wifi card worked for 2 weeks, then died. I was trying to get WEP working at the time. I spent the next 2 weeks fiddling with my ubuntu settings, thinking I had done something. Turned out that the card was borked.

Sadly, card manufacturers keep changing the chips sets. I now have a Dlink G520 which has an atheros chipset, and it works fine. Others have had problems with theirs. All you can do is buy a common card, which others have had no problems with, which uses a chipset that is supported out of the box, then hope it works.

The good news is that most cards can be made to work, using ndiswrpper - its just a lot more hassle. Also, things can get hard when you try to set up WEP or WPA encryption.

---

### Post by yoink23 on 2006-05-08
Thank's for the advice, Sendervictorius.  I just got a 	D-Link AirPlus DWL-520+ from ebay for $21.50 USD.  According to the linux compatibility list that the wiki refers to ( [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/) ), it is green (supported) using the ACX111 driver.  I guess we'll see how smoothly it goes in a few days!

---

### Post by Sendervictorius on 2006-05-09
You might be ok with this card. According to the ubuntu wiki:
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards#head-61bb23b68e5f4b9db28f4ef0cc6287ea9a71783c](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards#head-61bb23b68e5f4b9db28f4ef0cc6287ea9a71783c)
the  DWL-520+ has an acx100 chipset, which just works.

But do a search on this forum for DWL-520+, and you will see others have had problems. It seems that when it comes to WEP, people get stuck. However, that may be their access point setup, and not their wifi cards.

---

### Post by yoink23 on 2006-05-09
Ok, good to know.  I'm not all that worried about WEP encryption.  We all know it can be cracked easily anyway.  

I know, I know, I should still set it up just to be safer.

---

### Post by Sendervictorius on 2006-05-10
You can do things like restricting MAC addresses on your access point to keep slightly secure - easily done, and probably more secure than WEP, given the snooping software available today! 

WPA in theory should be much better, but hard (but not impossible) to get working on ubuntu.

---

### Post by wezza on 2006-05-10
Hi, I know you have made your choice allready, but I would like to recommend a card, maybe for the other people reading this topic. I just bought an Edimax EW-7128g which uses the ralink rt61 chipset. Ralink has open source drivers, but are not included in breezy, maybe they are in dapper... But you can download the linux-drivers from the ralink website and compile them yourself, which is explained in the readme file. Not at all that hard.
It was the cheapest card on the marked here (17 euro), and is has a detachable remote antenna, which is nice if you ask me. Right now it's working just fine, with WPA-AES.

Good luck!

---

### Post by bionnaki on 2006-05-11
I recommend the linksys wmp54
follow my instructions for getting it work & setting up wap: [http://www.ubuntuforums.org/showthread.php?t=161376&highlight=wmp54g](http://www.ubuntuforums.org/showthread.php?t=161376&highlight=wmp54g)

---

### Post by yoink23 on 2006-05-11
Thanks for all the suggestions everyone! I'm sure they are helpful to other people so they can buy cards that won't give them headaches in the future.

---

### Post by Sendervictorius on 2006-05-12
I would be interested to know what chipset your 520+ has. Could you post an lspci when you install the card?

---

### Post by yoink23 on 2006-05-12
[QUOTE=Sendervictorius]Could you post an lspci when you install the card?[/QUOTE]

Sure will.  Unfortunately it's coming via Canada Post, and was dropped off on Wed.  I have no idea how long it will take with this service.

---

