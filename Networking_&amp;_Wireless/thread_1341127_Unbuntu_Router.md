---
title: "Unbuntu Router"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by fanchao on 2009-11-29
hi all, i need some help please. 
 
i want to set up a network. but without internnet connection, basically 4 PCs talking to each other. 
 
my network diagram looks like this: 
client( 1 pc) ----> firewall/router( another pc)------> servers ( 2 pcs ) 

i am headache with the firewall/router part, because of that, my project cant even get started. 
reason: i can not use internet to configure it. this is totally LAN envrionment,
i tried IPcop. but my school does not have compatible 3com nic card. 
i tried Pfsense, clarkconnect,ebox all do not work. becasue they need web GUI to configure...

can ubuntu do the router part for me without intennet connection?
 
thank you!

---

### Post by Rinzwind on 2009-11-29
PC1 -> 
PC2 ->     router  (-> modem -> internet)
PC3 -> 
etc.
PC9 ->

With the part in between () it would be a normal setup with internet connection,

You can use a PC that is connected to the router with an UTP cable.
The router will be on 192.168.1.1 (or it should say otherwise in the manual that came with the router).

And you do not need internet for this to work :)

You can have a PC act like a router to if that is what you meant.
[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

---

### Post by iponeverything on 2009-11-29
> **fanchao said:**
> 
can ubuntu do the router part for me without intennet connection?
 

ubuntu can do the router thing better than most routers.

---

### Post by Iowan on 2009-11-29
[Here]("https://help.ubuntu.com/community/Router") is another Ubuntu router page for you to check.

---

### Post by capscrew on 2009-11-29
> **fanchao said:**
> hi all, i need some help please. 
 
i want to set up a network. but without internnet connection, basically 4 PCs talking to each other. 
 
my network diagram looks like this: 
client( 1 pc) ----> firewall/router( another pc)------> servers ( 2 pcs ) 

i am headache with the firewall/router part, because of that, my project cant even get started. 
reason: i can not use internet to configure it. this is totally LAN envrionment,
i tried IPcop. but my school does not have compatible 3com nic card. 
i tried Pfsense, clarkconnect,ebox all do not work. becasue they need web GUI to configure...

can ubuntu do the router part for me without intennet connection?
 
thank you!

No need for a router if all if all you are going to have is a LAN.  If you did build a router and put it in the LAN it wouldn't route anything.  Routing is TCP/IP.  LAN is layer 2 Ethernet. A simple 4 or 8 port switch is all you need.  If later you want to connect to the internet, you can get or build a router.

---

### Post by dmizer on 2009-11-29
> **capscrew said:**
> No need for a router if all if all you are going to have is a LAN.  If you did build a router and put it in the LAN it wouldn't route anything.  Routing is TCP/IP.  LAN is layer 2 Ethernet. A simple 4 or 8 port switch is all you need.  If later you want to connect to the internet, you can get or build a router.

Yup. All you need is a switch or hub and give all your machines static IP addresses on the same subnet, and you have a LAN only network with no Internet access.

No need for a firewall if there's not going to be any Internet access.

---

### Post by capscrew on 2009-11-29
> **dmizer said:**
> ...
No need for a firewall if there's not going to be any Internet access.
To explain a little more.  Firewalls work on TCP/IP (Layer3) and above.

---

