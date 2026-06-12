---
title: "Do Not Understand How to Set Up Wireless"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by Uadebisi on 2009-11-30
Hi,

Here my situation...I just ordered a new laptop with Ubuntu 9.1 pre-installed. I presently have a three year old Gateway running XP on which I ran the Ubuntu Live CD. Everything worked fine after downloading a printer plugin & fiddling with the sound settings. 

My desktop is hard wired so I will be getting a new wireless modem & router for the laptop & to be used with the desktop. My concern is with the wireless connection with the desktop. I have been reading about the potential issues, many of which seem a bit over my head. There is talk of installing a ndiswrapper or ndisgtk pack to be sure I have the necessary drivers to work my my wireless network card. Do I even have a wireless network card? How do I know? And if I do, what is the simplest way to get  the wireless connection working?

From what I have been reading, 9.10 is having far more problems connecting to wireless networks that 9.04. I was reading something in the Ubuntu help docs about using Windows drivers. That really confused me. If I wipe out Windows with an install of Ubuntu, how can I use Windows drivers if Windows no longer exists? Perhaps I can connect wireless to the laptop & hard wired to the desktop. I will need to check the options of the wireless routers available. If this is possible, this certainly seems like the simplest approach.

I would appreciate any feedback...constructive feedback that is ;-) Thanks!!

---

### Post by peepingtom on 2009-11-30
Hi,

Wireless in Ubuntu really isn't that scary :) Many of the problems in this forum were caused by people fiddling with settings they didn't understand and then upgrading.

NDISwrapper is just a compatibility layer. It emulates the part of windows that loads Network drivers, and translates commands so that Linux can control devices using drivers that were made for windows.

Generally you don't have to use NDISwrapper. If you're going to buy a wireless device based on whether it is compatible with Linux, you'll want Intel, Ralink or Atheros chipsets. Broadcom or Marvell are most likely to have complications, avoid them! Their chipsets are kind of junky anyway.
If you plan on buying a USB wifi adapter, just google around first so you can try and determine which chipset is in it. If you want, post in this thread about the adapter you want to buy. I'll subscribe to this thread, and someone will tell you if the device you want to buy is likely to be compatible.

---

### Post by Uadebisi on 2009-11-30
Thanks for the reply. I am sorry to say that I am very lost :confused:

> so that Linux can control devices using drivers that were made for windows.

Aren't the wireless drivers part of Windows? And if so, if Windows is not on the machine, what good would its drivers do?

Since I have always been hardwired, I am a bit confused. When you say,

>  If you're going to buy a wireless device based on whether it is compatible with Linux, you'll want Intel, Ralink or Atheros chipsets.

Are you referring to my buying a wireless router & modem? And why would I need a USB adapter if I am only running one desktop & one laptop preinstalled with Ubuntu & all the necessary wireless devices?](*,)

And, one of my original embarrasing questions, "Do I even have a wireless network card?" Believe it or not, I have been working with computers since DOS...apparently never with any of this stuff though ;)

---

### Post by steveneddy on 2009-11-30
If Ubuntu came pre-installed the wireless should work out of the box. If not call the company that you purchased the laptop from.

On the wireless router there will be Ethernet ports for your hardwired desktop.

Just follow the instructions that come with the wireless router and you should be just fine.

EDIT:

buy this and you'll be OK.

[http://www.linksysbycisco.com/US/en/products/WRT54GL](http://www.linksysbycisco.com/US/en/products/WRT54GL)

---

### Post by Uadebisi on 2009-12-01
stevenneddy,

WOW...THANK YOU! That was easy.

I was hoping that the wireless router would also have the Ethernet ports so as to avoid all the possible challenges of setting up a wireless connection, I just thought I would post here & be proactive. Or, if you look at it another way, just so I could waste everyone's time ;) And as you said, the new laptop will come ready out of the box, which is why I bought it! 

**Edit- I checked that link you sent for the router but that is for a G network, which I am told is slow. My new laptop works with agn.** And what about all this chip talk to which peepingtom was referring? Again, I realize that my lack of wireless experience does not necessarily pertain to Ubuntu so forgive my ignorance, I've just never had the need to set up a wireless system in my home or office. What I am realizing is that using a wireless router eliminates the need for a wireless modem, that I would only need a wireless modem if I did not have a router. This should keep thing even simpler for me. 

peepingtom or stevenneddy,

I know this may be pointless for the time being but I would still appreciate it if one of you wouldn't mind answering my questions from my last entry...just so that I can learn something today :popcorn:

---

### Post by bkratz on 2009-12-01
> **Uadebisi said:**
> 

Aren't the wireless drivers part of Windows? And if so, if Windows is not on the machine, what good would its drivers do?

Are you referring to my buying a wireless router & modem? And why would I need a USB adapter if I am only running one desktop & one laptop preinstalled with Ubuntu & all the necessary wireless devices?](*,)

And, one of my original embarrasing questions, "Do I even have a wireless network card?" Believe it or not, I have been working with computers since DOS...apparently never with any of this stuff though ;)


The wireless drivers are written by the creators of the card: usually specifically for Windows since they have the market share. Ndiswrapper allows you to use those drivers even though they were written for Windows. The Ubuntu developers have made their best effort duplicating the functionality for some devices so they become natively supported.  Not all have been duplicated, hence the need for Ndiswrapper in some cases.

Some wireless cards are on different internal computer busses. My card plugs into an available USB port and is not internal. Many are, usually on the PCI bus.

The easiest way to identify you wireless card would be through the terminal. If you go to Applications---Accessories---terminal a small window will open and if you type in lspci (that is LSPCI in lowercase it is case sensitive) a list of PCI devices will be displayed.  You can copy and paste this here and someone will identify your card for you, or you probably can just be looking.

Hope this has been of some help.

---

### Post by Uadebisi on 2009-12-01
bkratz,

Thank you! Big help as I need to learn. I learn about computers & such as is needed & now it's time to learn about wireless & Ubuntu :) Sounds kind of odd that I know so little of basic wireless connections & configurations but I have never had the need, therefore I never learned.

> Some wireless cards are on different internal computer busses. My card plugs into an available USB port and is not internal. Many are, usually on the PCI bus.

So, does this explain the need for a USB WiFi adapter? Is that what your external card is, a USB adapter that resembles a flash drive?

I look forward to hearing back from steveneddy as well ;)

---

### Post by bkratz on 2009-12-01
> **Uadebisi said:**
> bkratz,

Thank you! Big help as I need to learn. I learn about computers & such as is needed & now it's time to learn about wireless & Ubuntu :) Sounds kind of odd that I know so little of basic wireless connections & configurations but I have never had the need, therefore I never learned.



So, does this explain the need for a USB WiFi adapter? Is that what your external card is, a USB adapter that resembles a flash drive?

I look forward to hearing back from steveneddy as well ;)



Yes, it is just a little bit bigger though!

---

