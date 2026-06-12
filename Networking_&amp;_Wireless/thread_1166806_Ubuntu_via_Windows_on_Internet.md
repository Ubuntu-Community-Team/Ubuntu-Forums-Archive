---
title: "Ubuntu via Windows on Internet"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by ADV on 2009-05-22
Hi.

I have lots of problems with my Notebook in combination with my wifi BCM94311 (broadcom). 
I am solving this problem, but i need a wired internet connection..

The problem is that i am in a students home and one room where the modem and
router are standing is not always accessible.. O_o
So i want to create a wired connection through my windwos machine.
The problems is that i do not know how to do that, with all the properties and ip adresses
ect ect.. Can someone help me out?

I have drawed my situation :

[IMG]http://sites.google.com/site/javildesign/Home/mijnomgeving.JPG?[/IMG]

Thanks for you help!

ADV

---

### Post by puppywhacker on 2009-05-22
you need on the windows box the Internet Connection Sharing, problem is that microsoft has hardcoded to use 192. address ranges for it and won't allow 10. 

I think it is more beneficial to focus on getting your wireless to work. Apparently it can use bcm43xx as a driver.

---

### Post by ADV on 2009-05-22
> I think it is more beneficial to focus on getting your wireless to work.That is what i'm focusing on. But there for i need the internet running on my Ubuntu Notebook. 

So i need to connect through my windows PC.
The room next door is not accesible at the moment. 
So i want to create a permanently wired connection possibility.
Also i have more reasons to have a possiblity to have wired internet sometimes, and
that is what i'm asking.

Is there someone that can teach me how to setup this config? The do's and don't ect ect?

Thanks.

ADV

---

### Post by dandnsmith on 2009-05-22
I'd remove Router2 from the picture, and connect laptop directly to Windows PC.

You can use Internet Connection Sharing to do the necessary proxy stuff, but you won't be able to use the Windows 'wizard' on the ubuntu to set it up, so it'll be a bit more trial and error stuff.

I can't remember all the details - been a long while since I had to do it.

---

### Post by ADV on 2009-05-22
> I'd remove Router2 from the picture, and connect laptop directly to Windows PC.
Then i need a cross-over cable..
I did it like this, because people said that ubuntu don't like the direct connection.
So there for i setup a second router..

---

### Post by mrog on 2009-05-22
A couple points here:

If either computer has a gigabit ethernet interface (i.e. most newer computers), there is no need for a crossover cable. Any ethernet cable will do.

The internal subnet that you're trying to use is 10.0.0.0 but, by default, Windows will try to use subnet 192.168.0.0. (see: [http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126) ) So if you're going to use the existing setup then make sure the Windows computer is plugged into the incoming port on router2. Other wise plug both computers in to a standard router2 port and configure the router to not act as a DHCP server. 

In both cases, configure Ubuntu to obtain an ip address automatically.

---

### Post by dandnsmith on 2009-05-23
> **mrog said:**
> A couple points here:

If either computer has a gigabit ethernet interface (i.e. most newer computers), there is no need for a crossover cable. Any ethernet cable will do.

The internal subnet that you're trying to use is 10.0.0.0 but, by default, Windows will try to use subnet 192.168.0.0. (see: [http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126) ) So if you're going to use the existing setup then make sure the Windows computer is plugged into the incoming port on router2. Other wise plug both computers in to a standard router2 port and configure the router to not act as a DHCP server. 

In both cases, configure Ubuntu to obtain an ip address automatically.

Now I'm confused - what is an incoming port: the whole point of router ports is that traffic goes both ways. A point to note is that some routers are modem/routers with no stacking facility - it could be one of these.

If you don't use DHCP, then there will be a bit of a problem acquiring the IP address etc.

---

