---
title: "wifi hotspot"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by sanozuke02 on 2011-09-17
i have a laptop with wired connection... how can i make my laptop as a wifi hotspot so that i can connect my ipod touch to the internet....just like what i am doing in my windows.


thnks for the help guys

---

### Post by Rubi1200 on 2011-09-17
Moved to Networking & Wireless as a more appropriate forum for this question.

Thanks.

---

### Post by maul9999 on 2011-09-17
> **sanozuke02 said:**
> i have a laptop with wired connection... how can i make my laptop as a wifi hotspot so that i can connect my ipod touch to the internet....just like what i am doing in my windows.


thnks for the help guys

Hard to say.  It is rare wireless card that have router abilities.  For ubuntu? it is not going work.  You will want to buy wireless router or verizon MiFi as well.

---

### Post by sanozuke02 on 2011-09-17
i see thnks guys for helping me maybe i'll just install windows on my free memory spaces.. its so easy for me to use ubuntu that's why i cant remove this Os.. thanks again guys..

---

### Post by maul9999 on 2011-09-17
> **sanozuke02 said:**
> i see thnks guys for helping me maybe i'll just install windows on my free memory spaces.. its so easy for me to use ubuntu that's why i cant remove this Os.. thanks again guys..

To be clear for english.  I think you mean free spaces hard drive instead of free memory spaces.  Most geeks called their RAM as memory.

---

### Post by Lisiano on 2011-09-17
ACTUALLY you can use your WiFi adapter as a hotspot. If your iPod uderstands Ad-hoc you can use that. If not, wait until Ubuntu 11.10 is out, in the 3.0 kernel there is a cool feature that let's even non-ad-hoc aware devices see the networks (My phone can't connect to Ad-hoc yet it connected to that, never did before).
To make a Ad-hoc network just click the Network Manager icon and select Create new wireless connection then set it up as you want to, by default it's set to share your current internet connection.

---

### Post by haqking on 2011-09-17
+1 as above

Create a new wirless connection from network manager and then as long as the device support ad-hoc you should be good

---

### Post by maul9999 on 2011-09-17
> **Lisiano said:**
> ACTUALLY you can use your WiFi adapter as a hotspot. If your iPod uderstands Ad-hoc you can use that. If not, wait until Ubuntu 11.10 is out, in the 3.0 kernel there is a cool feature that let's even non-ad-hoc aware devices see the networks (My phone can't connect to Ad-hoc yet it connected to that, never did before).
To make a Ad-hoc network just click the Network Manager icon and select Create new wireless connection then set it up as you want to, by default it's set to share your current internet connection.

I don't think so.  It won't work that way.  unless you have wired and wireless.

---

### Post by haqking on 2011-09-17
> **maul9999 said:**
> I don't think so.  It won't work that way.  unless you have wired and wireless.


the OP stated he has a wired connection.


[http://jaap.haitsma.org/2010/08/17/make-portable-hotspot-with-gnome-network-manager/](http://jaap.haitsma.org/2010/08/17/make-portable-hotspot-with-gnome-network-manager/)

---

### Post by maul9999 on 2011-09-17
> **haqking said:**
> the OP stated he has a wired connection.


[http://jaap.haitsma.org/2010/08/17/make-portable-hotspot-with-gnome-network-manager/](http://jaap.haitsma.org/2010/08/17/make-portable-hotspot-with-gnome-network-manager/)

Ah! I miss it!  Thank for make clear with me.  Alot of wireless device can't connection to computer's ad-hoc.  My psp can't connection to my wireless card.

---

### Post by haqking on 2011-09-17
> **maul9999 said:**
> Ah! I miss it!  Thank for make clear with me.  Alot of wireless device can't connection to computer's ad-hoc.  My psp can't connection to my wireless card.


No worries, yeah i mentioned in my post #7 as long as the device supports ad-hoc.

peace

---

### Post by followurdrmz on 2011-11-13
I am having the same issue. Im using Lubuntu 11.10. My wifi card is BCM4311 b/g. I tried sharing my internet connection via adhoc to my ipod Touch 3G. I created the adhoc network but i cant find it on my ipod Touch. I am able to connect via wifi to a router.
I have completely switched to Ubuntu and this is the only issue im left over with.

---

### Post by bkratz on 2011-11-13
Do you have a wired connection to the router, unless I misunderstand you are trying to use the wireless in both the managed mode to connect to the router and ad-hoc as an AP?

---

### Post by followurdrmz on 2011-11-14
> **bkratz said:**
> Do you have a wired connection to the router, unless I misunderstand you are trying to use the wireless in both the managed mode to connect to the router and ad-hoc as an AP?

No actually i am using a dsl modem for my internet connection. I also have a DSL wifi router which is not working well. Only the wifi is working. i just used the wifi router to check if my ipod can see the wifi router. ipod can recognize the wifi router but not the adhoc connection. I used adhoc wifi in windows to share connection with ipod. So i think my wifi card is supported for adhoc connections.
So my laptop is connected to internet via ethernet to the dsl modem (with no wifi) and I want to share that internet connection thru adhoc wifi to my ipod.

---

### Post by followurdrmz on 2011-11-15
bump!!!

---

### Post by Garzo on 2011-11-18
All the guides to creating an ad-hoc network say that you left-click on the network-manager applet and select 'create new network'. However, that option doesn't appear on my Ubuntu 10.04. Any thoughts?

---

### Post by followurdrmz on 2011-11-26
> **followurdrmz said:**
> I am having the same issue. Im using Lubuntu 11.10. My wifi card is BCM4311 b/g. I tried sharing my internet connection via adhoc to my ipod Touch 3G. I created the adhoc network but i cant find it on my ipod Touch. I am able to connect via wifi to a router.
I have completely switched to Ubuntu and this is the only issue im left over with.

My problem got solved. I tried all the guides i saw with no result. No matter what i did, my ipod couldn't see the adhoc. Recently I updated my Lubuntu kernel to 3.0.0-13. Now i can connect my iTouch to adhoc. Thanks for the kernel update.

Now im using adhoc with firestarter app. Figured out that I need to add ipod's ip in firestarter app to allow connections and yes the internet is shared and it works...

---

