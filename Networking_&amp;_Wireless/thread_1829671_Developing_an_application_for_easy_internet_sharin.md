---
title: "Developing an application for easy internet sharing"
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by r.darwish on 2011-08-20
I couldn't notice that sharing an internet connection in Windows is easy compared to Ubuntu. Being a developer that wants to help the Ubuntu community, I consider to start developing a GUI application that will make setting up a bridge, NAT and a wireless hotspot easy with a click of a button.

I am not very experienced with Ubuntu so it's important for me to hear suggestions from the community before I start developing, and this is why I post this message.

First of all, I really don't wish to re-invent the wheel. A googled a bit and didn't found any software which seems to fulfill my vision, but maybe there's an application that I am not aware of.

Secondly, I have some technical questions. First of all, I don't plan to implement the desired functionality by myself, my application should be a GUI controlling bridge-utils, hostapd and the other great tools which sadly lacks a good GUI. I think the best platform will be GTK# with Mono, are there any drawbacks which I should aware of?

I will be glad to hear any other opinions or suggestions.

---

### Post by dave01945 on 2011-08-20
whenever i've needed to share an internet connection i've done it through network manager either create and ad-hoc network or set the ip4 setting to shared to other computers and it's always worked fine

---

### Post by r.darwish on 2011-08-20
> **dave01945 said:**
> whenever i've needed to share an internet connection i've done it through network manager either create and ad-hoc network or set the ip4 setting to shared to other computers and it's always worked fine
Is the network manager able to create a non ad-hoc network? Android devices, for example, can't connect to ad-hoc networks.
Also, is it capable to share an Internet connection both ways? (For example: using a laptop to share a wireless Internet connection with a computer which does not have a wireless network card)

---

### Post by dave01945 on 2011-08-20
yeah the wireless internet connection can be shared through the ethernet by setting the ethernet ip4 to shared to other computers and it can share through wireless the same way without being ad-hoc i used to do this on my ps3 and i was unable to do this easily with windows. with windows i could only create a ad-hoc network

ps3 won't detect ad-hoc networks

---

### Post by r.darwish on 2011-08-20
I just tried to do what you suggested, but I can't figure out how to create a non ad-hoc wireless network. When I click on "Create a new wireless network" the only parameters that I can set are the network name and security method.
When I go to that network's properties in network manager, the only 2 available modes are "infrastructure" and "ad-hoc"

---

### Post by dave01945 on 2011-08-20
leave it on infrastructure and then go to ip4 and set that to shared to other computers

--edit-- 

i tried this again myself and can't get it to function without bein in adhoc mode when i done it previously i must have done it some other way

i enjoy using the command line myself but i do think any new gui's to make things easier are always a good idea it' makes it alot friendlier for people just coming from windows, it's can be daunting having to use the command line for the first time

---

