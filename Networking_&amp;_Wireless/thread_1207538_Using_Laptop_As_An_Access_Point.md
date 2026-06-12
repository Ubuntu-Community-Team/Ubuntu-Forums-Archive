---
title: "Using Laptop As An Access Point"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by konqueror7 on 2009-07-08
okay, how would i make my laptop (Intel PRO/Wireless 2915ABG) with internet connection through ethernet and and router, to be used as an access point? i'm thinking of using it for my psp...i've read several posts here, but seems to be outdated (edgy)...

any replies, redirections, or a quick howto would be greatly appreciated :)

---

### Post by konqueror7 on 2009-07-08
bump...

---

### Post by konqueror7 on 2009-07-09
anyone? i know this problem could be fixed by just by buying a wireless router, but it costs me money, so i wanted to look for alternatives...

---

### Post by ernstblaauw on 2009-07-09
In [this]("http://ubuntuforums.org/showthread.php?t=398771") thread, it is said you can just create a new wireless network with the NetworkManager applet, by just clicking 'create new wireless network'.

---

### Post by konqueror7 on 2009-07-09
thanks for the reply, i already read it before i posted it. what i wanted is to create an access point via my wifi card, in excahange of having a dedicated wireless router. thanks anyway,,,;)

---

### Post by aesis05401 on 2009-07-09
Hey, 

How many physical network adapters do you have total?  If you are only using the wireless you will not see very good performance because of the way that Linux bridging works (if you can even do it). 

Basically, you can set the physical network adapters (ie: your wireless&/or wired cards) to spoof addresses for virtual network adapters, and you can have as many virtual network addresses as you have the processor power/RAM to simulate.  

In order to do this you usually need to set the physical interface to a promiscuous mode, and I know there are some problems doing this on many models of wireless cards.  

If you have two physical adapters, one being wired, then you can do things more simply. 

[http://www.linux-foundation.org/en/Net:Bridge]("http://www.linux-foundation.org/en/Net:Bridge")

---

### Post by konqueror7 on 2009-07-10
> **aesis05401 said:**
> Hey, 

How many physical network adapters do you have total?  If you are only using the wireless you will not see very good performance because of the way that Linux bridging works (if you can even do it). 

Basically, you can set the physical network adapters (ie: your wireless&/or wired cards) to spoof addresses for virtual network adapters, and you can have as many virtual network addresses as you have the processor power/RAM to simulate.  

In order to do this you usually need to set the physical interface to a promiscuous mode, and I know there are some problems doing this on many models of wireless cards.  

If you have two physical adapters, one being wired, then you can do things more simply. 

[http://www.linux-foundation.org/en/Net:Bridge]("http://www.linux-foundation.org/en/Net:Bridge")

yes, i do have 2 adapters, one being wired (which i connected my internet from a router) and one being my wifi...thanks for the link, going to read this trough now...

---

