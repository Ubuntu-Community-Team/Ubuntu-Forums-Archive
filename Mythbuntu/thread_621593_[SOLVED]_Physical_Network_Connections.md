---
title: "[SOLVED] Physical Network Connections"
date: 2007-11-23
forum: Mythbuntu
---

### Post by thorner on 2007-11-23
Okay, to most of you this will probably be a no-brainer, but apart from cursing I.T. when the office network goes down, I've NO experience with networks (be it wired or wireless)!

I need to physically connect my Mythbuntu frontend to my backend. 

Frontend is a K8MM-ILSR w/ VIA VT8237 10/100
Backend is an M2N-E w/ one GigabitLAN 10/100 Ethernet

Currently the backend's one jack is occupied by the internet connection.  My thoughts are to add a PCI network card and have a direct cat5e connection from that card to the frontend's VIA LAN.

Would this work to get movies/music/TV/internet from the Backend to the Frontend? Or am I completely out to lunch?

Tim

---

### Post by ubnewbie2 on 2007-11-23
> **thorner said:**
> Okay, to most of you this will probably be a no-brainer, but apart from cursing I.T. when the office network goes down, I've NO experience with networks (be it wired or wireless)!

I need to physically connect my Mythbuntu frontend to my backend. 

Frontend is a K8MM-ILSR w/ VIA VT8237 10/100
Backend is an M2N-E w/ one GigabitLAN 10/100 Ethernet

Currently the backend's one jack is occupied by the internet connection.  My thoughts are to add a PCI network card and have a direct cat5e connection from that card to the frontend's VIA LAN.

Would this work to get movies/music/TV/internet from the Backend to the Frontend? Or am I completely out to lunch?

Tim

When you say the backend's one jack is occupied by the internet connection, is that an ethernet connection to your ethernet modem/router.  If it is, then buy a cheap ethernet switch (a box with multiple ethernet ports) This will become the hub of your network. Plug the ethernet modem/router into this hub, as well all other computers on your new network - the backend computer and the frontend, and anything else (a laptop perhaps)   All will share the ethernet connection AND be able to talk to each other.

No this all supposes that you do have a typical modem/router (with a NAT firewall in it). So, what exactly is your internet connection - ADSL, DSL, Cable and what is the equipment that connects you to it?

Your idea of a second PCI network card and a cable between the 2 boxes will work also, but is fairly inflexible.  The cable needs to be a crossover type since the connection is computer to computer, and you'll need to configure the cards ip address and other parameters by hand (unless you run a DHCP server on the backend say).   I would at least connect the two computers to a hub (switch box like before) so you can connect other computers into the network if required.

---

### Post by thorner on 2007-11-24
thanks for the reply.
sounds like my idea of a second PCI network card is a lot of work, and beyond my capabilities. 

your suggestions of a switch sounds exactly what I want. I have a motorola surfboard cable modem which is connected to my Gigabit LAN on my backend machine.

so an ethernet switch is what I want? that will distribute internet to both machines and allow the backend to send media/TV/etc to the frontend. just to be sure, is this (or similar) what I should buy?

[link]("http://www.ncix.com/products/index.php?sku=5402&vpn=BEFSR41&manufacture=Linksys")

thanks

---

### Post by thorner on 2007-11-24
after doing some more research with your suggestion, I found this - [_Linksys WRT54GL]("http://www.ncix.com/products/index.php?sku=17408&promoid=1030")_
would this work for my purpose (connect a mythbuntu frontend to a backend machine, and distribute internet to both)?
I don't see any problems, and figure I would then have the availability of a wireless G network for a future laptop purchase.

Further to my question, but on the same track, anyone have experience using a pair of these - _[Linksys PLK200]("http://www.ncix.com/products/index.php?sku=27111")_ for the front/backend connection? I've been told they work well, even for HD content.

And would I see any difference adding a GigabitLAN PCI card (_[for example]("http://www.ncix.com/products/index.php?sku=24753&vpn=GA311NA&manufacture=Netgear&promoid=1030")_) into my frontend (replacing the VIA VT8237)? or is it a waste of money?

many thanks for the help!

---

### Post by ubnewbie2 on 2007-11-24
> **thorner said:**
> after doing some more research with your suggestion, I found this - [_Linksys WRT54GL]("http://www.ncix.com/products/index.php?sku=17408&promoid=1030")_
would this work for my purpose (connect a mythbuntu frontend to a backend machine, and distribute internet to both)?
I don't see any problems, and figure I would then have the availability of a wireless G network for a future laptop purchase.

Further to my question, but on the same track, anyone have experience using a pair of these - _[Linksys PLK200]("http://www.ncix.com/products/index.php?sku=27111")_ for the front/backend connection? I've been told they work well, even for HD content.

And would I see any difference adding a GigabitLAN PCI card (_[for example]("http://www.ncix.com/products/index.php?sku=24753&vpn=GA311NA&manufacture=Netgear&promoid=1030")_) into my frontend (replacing the VIA VT8237)? or is it a waste of money?

many thanks for the help!

That linksys device seems to be the ticket. It seems to have the internet sharing and firewall capability, and has a DHCP server which will hand out the ip setup to each computer (as long as they are set to use dhcp which is the normal default).

The only thing I notice is that it is a 10/100 mb switch, which means gigabit ethernet devices will only run at 100 mb through it.  Do they have a gigabit model? (although 100mb is all I run around my house anyway)  I'll let others somment on whether gigabit is necessary for HD, as I don't stream it over my network - my front and back end are the same machine.

---

### Post by thorner on 2007-11-25
Thanks for the help! I went with the WRT54GL and PKS200 PowerLine/Ethernet Adapters. Hope I can set it all up tomorrow. I'll let you know how it goes. Thanks again.

Cheers

---

### Post by thorner on 2007-12-09
Update:
I bought the Linksys WRT54GL and the Linksys Powerline Ethernet Adapter (PLK200) to connect the frontend to  the backend.  The router (with stock firmware) works great, as do the Powerline Adapters.
Thanks for the help!

Cheers,
Tim

---

