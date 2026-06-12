---
title: "Custom Network, can it be done?"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by AoSteve on 2009-06-19
Windows.. as stupid as it is, won't allow me to connect to my router on one ethernet port while holding my modem on the other and STILL share that connection.   Every time I share the connection it simply screws the subnet and no system can see another on the network and nothing can be shared whatsoever.  

First, anyone know a way around that in Vista Ultimate x64?

Second, and the more important side as I'm almost always in Ubuntu..  Can ubuntu handle this and is there anything special I need to do?   

I would like this PC to share the internet connection with the router and it's client systems over the LAN.  Not sure how I can get it to work.  If I had a cisco router it'd be easy, but using an oldschool Belkin 54g router...  I just don't know what to go about doing to get it to work in either OS.

---

### Post by jonobr on 2009-06-19
Hello

Are you trying to connect your router (the belkin 54g) to an ubuntu box and then have the ubuntu box act as a router to the lan?

Ie two interfaces on the ubuntu system- maybe have that ubuntu system allocate internal IPs to the clients ?

Is this what your trying?

---

### Post by AoSteve on 2009-06-19
Basically,  This is how I want it to work

LAN systems -> Router -> This Box -> Modem

Basically, I want to be the "host" for the internet connection.   I have a limited amount of bandwidth on a per 24 hour period.  I'd like to be able to watch how much bandwidth is going through the network through one of the ethernet ports (i.e. My modem).  This way, I could use conky to "track" how much is going out and coming in through my modem.

Basically, this machine needs to be the router for the modem and use the actual router to share the internet connection through other PC's.    

This DOES work with other types of connections.  Like my dad's network.  He's got a USB connected cable modem and the same router I have.  With it's lack of options, I had to use windows ICS (Internet Connection Sharing) to allow his laptop access to the internet.  It works like this...

Laptop -> Wireless Router -> Desktop Machine -> Modem via USB cable

Mine would be similar, but I need to use Eth0 for the modem and Eth1 for the network.

Also, with this setup, would I have to setup a different subnet?   Such as 192.168.0.1 (my modem) and 192.168.1.1 for my router?

Cisco routers can easily track the bandwidth through each port, but this home router cannot do this.  So I'm trying to find a way around this without having to buy a $200 router.

Thanks ahead of time!

---

### Post by jonobr on 2009-06-19
Hello


The person who posted [This thread]("http://ubuntuforums.org/showthread.php?t=1187611T") provided a lot of information on performing similar functions which may be of use to you?

You could also drop him a note as he seems to have had time "at the coal face"

---

### Post by AoSteve on 2009-06-19
Sweet, thanks for the link.  I got some reading to do there.  I think my biggest problem is going to be the routing with the router.  This thing has a lack of features...  to say the least.   I'll have to see what I can do with it there.  I don't think it can handle subnets at all correctly.  LOL   Most likely I'll have to run two subnets to get this to work correctly.  The same way a cisco router would have to function to allow this ability.   I can setup the cisco router (as the CCNA classes have taught me) but this el cheapo router, I may not be able to at all.

---

### Post by jonobr on 2009-06-19
Hello


I dont think the belkin will handle anything outside of the address range thats its in,

I.e. if you set it to a class C thats all it can operate on.

You wont (im sure) be able to subnet that down to create larger network,
hence my thinking of using the ubuntu box with muilple nics to have different subnets hanging off the lan you create.

at that point the world is your ashtray.
I do believe the ubuntu box will handle routing a lot better then the belkin and the important thing for you is that all traffic will go through your system meaning that your in the way of the iP stream, hopeully meaning you can monitor whatever you need to monitor

---

### Post by AoSteve on 2009-06-19
So, do you think setting the router up for say..  192.168.2.0 : 255.255.255.240  would work? 

Once that works set my NIC for the router's lan up to DCHP to it, then the second lan for the modem which has to be set to 192.168.0.1 : 255.255.255.0 ?   My modem cannot be changed for anything, another one of those "brick walls" I've come to with thier system, I hate it.   

This would effectively establish two subnets, and then share the connection over the Eth1 port which is where the modem would reside?

---

