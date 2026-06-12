---
title: "Wired network issues"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by snkiz on 2009-09-02
This is going to be a bad explanation but here goes. I have a server with two network cards, that I'm trying to connect to with my desktop. If I plug my desktop into either port I get nothing, "no network connection" but if I plug my desktop into my netbook the network comes up, if I plug the netbook into the server the network comes up, if I plug my desktop direct to the internet the network comes up. so basically everything works except the way I want it to.

---

### Post by dbalascak on 2009-09-02
So the netbook will bring up the link to the server or desktop. Most likely the netbook has an interface that is auto sensing.  I automatically switches the transmit and receive pair depending on what type of network element you connect it to.  You will need a rollover ethernet cable cable to go between the server and desktop. This is a cable that has the transmit and receive pairs rolled inside the cable.

---

### Post by snkiz on 2009-09-02
I used the same cable for the desktop as I did for the netbook(Two tries actualy one was cat5 and one was cat6.). I used to have my server and desktop going through a router everything worked great then, but thats not possible at the moment.

---

### Post by Crafty Kisses on 2009-09-03
What are the results of the following?
```
route
```

---

### Post by ShutterAce on 2009-09-03
What dbalascak is saying is that you need a special cable to connect PC to PC because of the way it is wired at the plug. i think we used to call them patch cables.

---

### Post by Iowan on 2009-09-03
AKA crossover cables... I've read that some of the gigabit cards can auto-sense...

---

### Post by ShutterAce on 2009-09-03
> **Iowan said:**
> AKA crossover cables

Yeah! That's them!

---

