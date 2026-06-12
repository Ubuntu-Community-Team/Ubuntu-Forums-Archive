---
title: "Ethernet, or USB modem?"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by xmastree on 2006-07-09
I have installed 5.10 on this (my dad's) computer. He's currently on a dial-up, using the winmodem which I can't get working.
He's thinking about going to broadband.
My home setup has a modem which connects to the ethernet port, and works fine with ubuntu. I believe some, if not all of the UK providers prefer to use a USB modem (can't think why).
How well are these supported? Would I be better to find a provider who will give us an ethernet connection instead?

---

### Post by coffeecat on 2006-07-09
I don't think UK providers prefer to use USB modems, they're simply cheap, nasty things that the average non-computer literate Windows user can set up relatively easily. It's probably also easier for the muppets who staff the so-called help-lines at some of the bigger ISPs (no names - no pack-drill).

My advice? Sign up with a smaller, but better ISP and buy an ethernet modem-router. You can get one for about £20-25 if you don't need wireless. Less hassle to set up in Linux (using a web-browser) and you get a good firewall/NAT built in.

Oh, and throw the Thomson Speedtouch in the bin when it arrives. :wink:

Do you know about [www.adslguide.org.uk]("http://www.adslguide.org.uk") ? I'm presuming your father lives in the UK.  The site has a comparator for ISPs - including quality of service. Useful for avoiding the muppet-staffed ones.

---

### Post by mips on 2006-07-09
Just go for Ethernet and your live should be reletively painless. Brands like Linksys,Netgear,Billion would be a good choice.

---

### Post by cyberlite on 2006-07-09
I agree with coffeecat ethernet is better and easyer to install, plus lots of support here.:cool:

---

### Post by xmastree on 2006-07-09
That's what I'm thinking. BTW, ignore the location, I *am* at my father's here in the UK.
So, any ethernet modem will work with any provider? That's useful yo know.
This is encouraging:
[http://www.adslguide.org/qanda.asp?faq=speedtouch#Q61](http://www.adslguide.org/qanda.asp?faq=speedtouch#Q61)
but the problem is, this PC only has two ports, both in use. there are more headers on the mobo, but no connections. Not a huge problem to get round, but I would still prefer to use ethernet if possible. That's what it's for, surely... ;)

---

### Post by coffeecat on 2006-07-09
> **xmastree said:**
> So, any ethernet modem will work with any provider? That's useful yo know.
This is encouraging:
[http://www.adslguide.org/qanda.asp?faq=speedtouch#Q61](http://www.adslguide.org/qanda.asp?faq=speedtouch#Q61)
but the problem is, this PC only has two ports, both in use. there are more headers on the mobo, but no connections. Not a huge problem to get round, but I would still prefer to use ethernet if possible. That's what it's for, surely... ;)

First point - be careful of the cheapest package from some ISPs. They only 'allow' you to use one PC - that's perhaps why they hand out SpeedTouches. But how they can tell and how they can stop you running more than one simultaneously from behind an ethernet router I have no idea.

Second point - if you are a complete masochist :wink: [here is a link]("http://www.linux-usb.org/SpeedTouch/") for setting up the Speedtouch in various flavours of Linux. Best of British! :)

What do you mean by two ports? If you mean USB ports, you can get USB PCI cards fairly cheaply if you are really determined to go the USB route. Or, if you haven't got an ethernet port on the PC, you can also get an ethernet PCI card. OR - ( :wink: ), Maplins (for one) do a USB to ethernet converter dongly thingy. The £25 one comes with Windows drivers but it works out of the box with Dapper. I know because I've got one - isn't it wonderful when something 'just works' in Linux but you have to muck around installing drivers in Windows?

---

### Post by xmastree on 2006-07-09
> **coffeecat said:**
> They only 'allow' you to use one PC

how they can stop you running more than one simultaneously My isp in the Philippines gave me an ethernet modem, so I made my ubuntu box into a router. ;) 

> What do you mean by two ports? If you mean USB ports, you can get USB PCI cards fairly cheaply if you are really determined to go the USB route.Yes, two USB ports, but four more on headers on the motherboard. I just need sockets for them. What makes you think I'm determined to go the USB route? That would be silly... :rolleyes: 

> Or, if you haven't got an ethernet port on the PC,There is an ethernet port, and I want to use it as I know it will work right away.

> isn't it wonderful when something 'just works' in Linux but you have to muck around installing drivers in Windows?Yep. It's nice that it goes online and checks the time *before* it's finished booting. :cool:

---

