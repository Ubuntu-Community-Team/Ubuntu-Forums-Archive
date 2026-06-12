---
title: "Air Crack"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by bumder on 2010-09-28
hi,

has anyone had any success with aircrack and ubuntu?

i used to use kismac on my macbook, but with no packet injection.  Still managed to crack a wep key, but it took days of collecting packets :(

i'm currently using a samsung nc10 netbook with ubuntu, so maybe someone knows of a different/better app than aircrack?

thanks

---

### Post by Telémakhos on 2010-09-28
All the Samsung NC10 are shipped with the Atheros 5007. You can run "lspci" to be sure about that. So the aircrack-ng suite is all you need.

You've really good installation tuts **[here]("http://aircrack-ng.org/doku.php?id=install_aircrack")**

---

### Post by louis--taylor on 2010-09-28
I think aircrack-ng is the best around. I personally have had much success with the entire suite, so as said before, the aircrack-ng suite is probably all you need.

---

### Post by bumder on 2010-09-29
awesome, does that mean i can inject packets with an atheros 5007 chipset as well?
 
its a shame aircrack-ng can't handle wpa yet :(
 
cheers
:KS

---

### Post by louis--taylor on 2010-10-04
> **bumder said:**
> awesome, does that mean i can inject packets with an atheros 5007 chipset as well?
 
its a shame aircrack-ng can't handle wpa yet :(
 
cheers
:KS
 
Sorry for the long wait for a reply, aircrack-ng does handle wpa, the only difference with cracking wep and wpa is you must use a dictionary based attack on the key, meaning that you must either try every possible key, or be very lucky with a weak key, making it much slower.

---

