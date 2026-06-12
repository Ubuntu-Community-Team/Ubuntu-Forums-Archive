---
title: "Network manager stopped recognizing my card"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by Hanj on 2006-07-11
I have an Atheros card (AR5212 chipset) which worked fine out of the box with Dapper. I installed Network manager, and that worked fine too. But then some time ago, for no apparent reason, network manager stopped recognizing the card. 

Now it just says "No network devices have been found" when I click on it. The card is still working fine though, and I can connect from the CLI. I have tried reinstalling network manager, but I still get the same problem.

---

### Post by Reb on 2006-10-09
Same deal, worked with Dapper but not Edgy. CLI works, it's an Atheros card in a new MacBook.

---

### Post by KingArthur10 on 2006-10-10
I have the exact same problem as the grandparent.  Still using Dapper, but one day, NM stopped recognizing the card.  The Network Admin applet still works.

---

### Post by KingArthur10 on 2006-10-10
Found the answer in another thread.

you'll need to edit /etc/network/interfaces

Comment out everything except "auto lo" and "iface lo inet loopback".

Restart and everything should work like a charm again.  Did for me!  *Does a happy dance*

---

### Post by ratman99uk on 2006-10-17
> **KingArthur10 said:**
> Found the answer in another thread.

you'll need to edit /etc/network/interfaces

Comment out everything except "auto lo" and "iface lo inet loopback".

Restart and everything should work like a charm again.  Did for me!  *Does a happy dance*

This worked for me thanks for the help

---

### Post by KingArthur10 on 2006-10-17
No problem.  Glad I could help ya :-).  Just trying to spread the wealth of info.

---

### Post by gothike on 2006-10-18
> **KingArthur10 said:**
> No problem.  Glad I could help ya :-).  Just trying to spread the wealth of info.


Didnt worked for me can anyone of you help me please!?!?!

---

