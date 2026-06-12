---
title: "Complete Networking Novice"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by Beej on 2006-06-02
I will be moviong into a shared flat shortly with a friend who I managed to turn to ubuntu a little while ago. We both currently have wired connections to cable internet.

When we move into the new place we will want wireless networking set up to share the internet connection, and possibly a shared Network drive.

My mini ITX board will take a laptop style PCMCIA card, my mates machine will take a standard PCI card. I think I have found suitable hardware here

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

Firstly I am a little worried about hardware support after reading around the forums. Do these look like good wireless options that will work out of the box? What will need to be done to set them up?

Secondly it is likely the new flat will have the same Cable internet connection. I assume I need a wireless router (going from what I have read) I plug the modem into the router with the ethernet cable and turn it on after installing the cards in the PCs and then what? It just works? or do I have to do something to get them to talk to each other? 

Thirdly, can anybody recommend a good wireless router?

Thanks,

Beej.

---

### Post by Dr. Nick on 2006-06-02
Cant comment on the cards, If you have seen good linux reviews on them you should be ok. I have only set up 1 wireless card which was a linksys wusb11 whihc is 802.11b, It wasnt to bad to do. Just search the forums and see if people have trouble with the ones you like.

You will need a wireless router, Which one you want will depend on whicc cards you use. If you are using 802.11b then a g router is a waste really, If you have g cards then a b router is a waste due to the speed differences. I have a b linksys and it has been good to me, Lately it appears to be messing up a tad though. Just keep your eye out for a good price and try to stay with linksys, netgear and the like. Most all routers will work with any os so you dont have to worry about linux compatabality, All configuration is done through a web browser. 

The modem will plug into to the uplink on the router via ethernet, If your cards are deteced correctly then just use the network tools to conenct, should be to big a deal. Once you are sure it all works i might look into some of the security options to implement such as wep or better yet wpa if possible.

---

### Post by almahtar on 2006-06-03
WPA and WEP are encryption methods for wireless signals.  They keep other people from intercepting your network traffic (credit card numbers, e-mail and forum passwords, etc), so they're a good idea.

Some wireless cards don't have WPA support, so you may want to stick with WEP at first and as you get braver switch to WPA because it's much stronger.  

As far as configuring your network:  I know it may sound elitist and dissmisive, but read the manual for the router (at least for the "setting up your network" section).  It'll help you understand some of the basic concepts of wireless networking so if you have questions you can know what to ask, and people will help you more quickly since they know what you're talking about.  In short, you're probably going to need to connect to your router with a cable at first, and give it a network name by pointing your web browser at it (its address is likely to be 192.168.1.1, but it varies between routers- this is where the manual comes in handy), and setting its wireless network name (often called its "essid").

Next you'll want to tell your computers what wireless network (or "essid") to connect to by pointing them at the same name.  In Ubuntu this is done through the network manager (the system menu at top-> administration->networking-> click "wireless network" and then "configure").

When you're running without encryption (like WEP, WPA, etc), you at least know that your network is working without it.  The next step is to enable WEP encryption on the router(using the web interface just like before), and then enable it in the computers you want on the network.  If you make a mistake and you can't get into the administration page (192.168.1.1 usually, as addressed above) with your wireless, plug a computer in to the router with a cable and you can reset the settings and try again.

I tried to be as detailed as I could but if you have any questions feel free to ask for elaboration, of course.

---

### Post by Dr. Nick on 2006-06-03
The above is correct and helpfull. Didnt think about it. All your initial config must be done with a ethernet connection from computer to router to save alot of headache. When you are configuring the wireless portion of the router through a wireless conection when you change settings you will be kicked out of the router until you make the corect adjustments to your system.

---

### Post by Beej on 2006-06-03
Thanks, all this is really helpfull and sounds relatively straightforward. Looking at the cards I have linked, they only have WEP not WPA. Do I need WPA?

---

### Post by Dr. Nick on 2006-06-03
[quote=Beej]Thanks, all this is really helpfull and sounds relatively straightforward. Looking at the cards I have linked, they only have WEP not WPA. Do I need WPA?[/quote]

WPA would be better just because it is a bit more secure then wep, Though I believe wpa is a bit harder to set up then wep at the moment. If you are going to live in a area with alot of other wireless users you may consider hooking up your computer to a wired connection when you are dealing with sensitive data just to be safest.

---

