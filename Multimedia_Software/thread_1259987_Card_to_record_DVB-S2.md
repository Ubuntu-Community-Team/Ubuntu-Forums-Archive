---
title: "Card to record DVB-S2"
date: 2009-09-07
forum: Multimedia Software
---

### Post by Fafler on 2009-09-07
I've been asked to build a setup for recording sattelite pay-TV. I need two DVB-S2 cards with CI interfaces that are well supported MythTV. The supplier is danish Canal Digital, if that has any influence.

---

### Post by Fafler on 2009-09-10
Bump!

---

### Post by chinoy on 2009-09-10
Im trying something similar.
Its not going to be easy trust me.
When it comes to the hardware this is what I have chosen.

Dell XPS M1530 with Nvida GPU
Fly TV Expresscard M5 T2A2
This card has two tuners that can be configured as 
2x Digital
2x Analogue
1XDigital and 1x Analogue
You can record from both chanells at the same time.
Has Built in FM card.

The hardware is all set but Ubuntu is not 

Id be very interested in what Card you pick. It will have to be something that sits on the PCI bus.
Chk out this link. Shows you how flaky and nascent support for TV tuners in Linux is.
Also post up any good links you find on the subject ie.
You may be better off asking on this list
[http://www.linuxtv.org/pipermail/linux-dvb/](http://www.linuxtv.org/pipermail/linux-dvb/)

---

### Post by Fafler on 2009-09-10
I know, i'm just tired of mailing lists. Seems like a clumsy and outdated way to  ask for support. But i guess theres no way around it.

---

### Post by chinoy on 2009-09-10
well you wont get much help here.
The guys who are in the know dont hang out on this forum.
Thats the feeling I get based on the lack of responses to my posts.

In fact across the internet I cant find much info on ExpressCards.
Even Dell the guys who made my laptop are clueless or at least the guys on their support team.
They couldnt even tell me which Intell Chip drives my Express card.

---

### Post by Fafler on 2009-09-10
Well thats true.

Anyway, I wrote to the list and got some usefull feedback.

I don't think you have a ExpressCard chip. ExpressCard is just a PCIe lane and a USB 2.0 port in the same connector. All the hotswap and resource allocation stuff is handled by the chipsset as with usual PCIe and USB devices. Thats why you can get cheap devices like this: [http://cgi.ebay.co.uk/PCI-E-PCI-Express-To-Expresscard-34-54-Card-Adapter-C95_W0QQitemZ350201448738QQcmdZViewItemQQptZUK_Computing_ComputerComponents_InterfaceCards](http://cgi.ebay.co.uk/PCI-E-PCI-Express-To-Expresscard-34-54-Card-Adapter-C95_W0QQitemZ350201448738QQcmdZViewItemQQptZUK_Computing_ComputerComponents_InterfaceCards)

---

