---
title: "Internet sharing like Windows possible?"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by nlsthzn on 2010-08-30
Hello all,

Just took the plunge and removed Windows 7 from my desktop rig and I am currently using Ubuntu 10.04 :)

I was using this PC to share my Internet (DSL) connection to any and all other PC's on my network, wired and wireless, and I am attempting to set this up in Ubuntu.

My desktop, other wired PC's, a wireless AP and my DSL modem are all connected to a 8 port Ethernet switch and I was using ICS in Windows 7 to share my Internet connection once I established the connection from my desktop.

Can this be done in Ubuntu?  As soon as I make the DSL connection it says that Auto eth0 disconnects (which I set to share to all in IPv4 settings which I read on the forum is the way to share)... thus nothing is currently shared :/

Any assistance would be greatly appreciated!


Neil

*Edit - In this [document]("https://help.ubuntu.com/community/Internet/ConnectionSharing")* it states that the sharing computer needs two network interfaces... but in Windows I only used the one...

---

### Post by gorbeich on 2010-08-30
you can share your internet connection creating an adhoc (or infraestructure) network, this is wireless. you can do this from the network tray icon -- create new connection. assign same name and password for every device you want to connect with wifi

hope this helps you!!

---

### Post by nlsthzn on 2010-08-30
> **gorbeich said:**
> you can share your internet connection creating an adhoc (or infraestructure) network, this is wireless. you can do this from the network tray icon -- create new connection. assign same name and password for every device you want to connect with wifi

hope this helps you!!

Hi,

Nope sorry, this is of no help currently... my wireless AP is connected to the same switch that my desktop is and currently my desktop is not connecting to Auto eth0 when I connect to the Internet via my DSL modem...

Thanks anyhow :popcorn:

---

### Post by nlsthzn on 2010-09-06
Hmmm... just got home after a week in hospital and no other replies?  Oh well... Guess all computers are just going to have to dial in seeing as for once Windows 7 does something network related much better and easier than Linux :/

---

### Post by BkkBonanza on 2010-09-06
I'm not sure if there's a quick easy way but certainly you can add a few config settings to your machine to set it up as a gateway/router for everyone else on your network. If you don't find a one-click solution then let me know and I can help do a full-on gateway config. I've done it on my Ubuntu based home router box. Same thing but not a desktop. It only takes a few minutes to do but probably longer to explain it.

---

### Post by bobbob1016 on 2010-09-06
> **nlsthzn said:**
> Hello all,

Just took the plunge and removed Windows 7 from my desktop rig and I am currently using Ubuntu 10.04 :)

I was using this PC to share my Internet (DSL) connection to any and all other PC's on my network, wired and wireless, and I am attempting to set this up in Ubuntu.

My desktop, other wired PC's, a wireless AP and my DSL modem are all connected to a 8 port Ethernet switch and I was using ICS in Windows 7 to share my Internet connection once I established the connection from my desktop.

Can this be done in Ubuntu?  As soon as I make the DSL connection it says that Auto eth0 disconnects (which I set to share to all in IPv4 settings which I read on the forum is the way to share)... thus nothing is currently shared :/

Any assistance would be greatly appreciated!


Neil

*Edit - In this [document]("https://help.ubuntu.com/community/Internet/ConnectionSharing")* it states that the sharing computer needs two network interfaces... but in Windows I only used the one...

From your first post, I get the picture, Internet->DSL->Your Rig->Switch->Wireless Router/AP

In the above scenario, you do have 2 network interfaces.  The DSL modem is a network interface, as is your network card.  That is why gorbeich suggested what s/he did.

From your next post I get the picture Internet->DSL->Switch->Your Rig (and Wireless Router/AP)

In this second scenario, you your computer doesn't, and can't really, share your internet connection.  Unless they are requiring you to sign on your one computer, the second scenario is better.

I might even suggest getting a router instead of a switch, or if that Wireless AP can be a router, that might be better (and you won't have to buy anything).  Most routers can do PPPoE which is what DSL uses in most cases.  I would suggest this, even if you go back to Windows 7, since it is a cleaner/easier setup, and doesn't require your computer to be on for the internet to work, and will save you money on electricity.

---

### Post by mprokolo on 2010-09-06
From [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
> 
GUI Method via Network Manager (Ubuntu 9.10 and up)

In order to share an Internet connection, the computer that will do the sharing must have two network cards or ports. This assumes that you are using at least one Ethernet port and that it is identified as "eth0" (edit: it is not clear in this guide if this is the port that is connected to the internet or to the computer with whom we want to share the connection).

When you are logged in:

    * Go to "System" on your top bar
    * Navigate to "Preferences" and select "Network Connections"
    * When that window opens, select "Auto eth0" and press "Edit" 

A new window will open. Navigate to the tab titled "IPv4 Settings" and change the Method to "Shared to other computers". After restarting the computer you should now be able to plug in any computer into your other Ethernet port or share through your wireless card. 


---

### Post by BkkBonanza on 2010-09-06
He wants to do this with one interface in the PC. I don't think Windows will do that either unless the modem has a usb connection and is hooked up that way. I thought this was weird as I never had ICS work with a single interface, and I went to research it and could find no info that said ICS works with one interface. 

DSL modems are usually PPP which means that the ethernet port doesn't get an IP address. However, some modems can support a NAT mode, ad then it would likely be possible since the modem device can have an IP on the LAN.

I'd love to see a link to a page that describes how ICS on Windows can do that on one interface only. That would be interesting.

---

