---
title: "Using PC as a Router  to share internet: Laptop connects but Desktop PC doesn't"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by Angel_Caido on 2010-10-15
Since I have 3 Network cards in my Desktop PC I've configured it to act as a Router using GNU/Linux Ubuntu Lucid in combination with Samba so I could share my internet connection. It works on any laptop a connect to it using any of the network cards ports [regardless of the operating system installed on the Laptops], but when I plug that same network cable to any Desktop PC [regardless of the operating System installed] it doesn't even light the LED in the netcards. From the Client PC seems like nothing is plugged in the the netcards. Any feed back on this issue?

Edit:
i'm using a crossover cable.

---

### Post by omelette on 2010-10-15
Sounds like you're using a network cable rather than a patch-cable...

---

### Post by psusi on 2010-10-15
Yea, bad cable or bad network card.

Technically you need to use a crossover cable to connect a card to another card instead of a switch, but most modern cards can detect this and automatically swap their polarity.  Not all can though.

---

### Post by Angel_Caido on 2010-10-15
I edited the original post to clarify that I'm using a crossover cable. 
The netcards in my PC work fine when I connect a Laptop to them, but if I connect a Desktop PC [with a working network card] to them that one PC won't connect to the internet at all.
I've tried direct connection between those Desktop Pc and the cable modem and it works, but if a use my Desktop computer as a router they can't connect but laptops do. That's what makes it strange and I'm asking for help here.

---

### Post by psusi on 2010-10-15
"Won't connect to the Internet" or doesn't get a link light?  You seemed to say you weren't even getting a light before, which is a lot different than getting a link, and just not being able to browse to a web site.

---

### Post by Angel_Caido on 2010-10-16
Edit 2:
The Client's Network Card won't even light up when I plug the [Crossover] cable to my PC working as a Router. That same cable makes the network card light up  and recognizes the network. I've read something about the Client's NetCard not supporting the "auto MDI/MDIX". Any Other Ideas?

---

### Post by psusi on 2010-10-16
Sounds like the network card does not support automatic polarity detection and reversal, and you are not using a crossover cable.

---

### Post by Angel_Caido on 2010-10-17
I repeat, **I am using a crossover cable**. 
I'm not sure if the client's network card supports automatic polarity detection and reversal, though. How could I find that out?

---

### Post by psusi on 2010-10-17
You check the manual.  If you plug the card into a switch with that cable and it works, but doesn't if you plug it into another card that you know works, then it isn't a crossover cable.

---

