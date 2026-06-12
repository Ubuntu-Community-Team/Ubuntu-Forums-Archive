---
title: "Uses of a two ethernet port motherboard?"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by Platinumjam on 2009-04-14
I recently acquired a MSI motherboard from a friend and it has two ethernet ports. I'm going to use it as a torrent computer and my original computer to do everything else. The two will be sitting side by side so I was wondering if it is possible to get an internet connection to both by running internet to the MSI board and running either a cross over cable or a normal ethernet cable to my main desktop using the second ethernet port. If this is possible could some one please tell me how to do it or even better suggest a simpler yet similar option. What I want to avoid doing is running two ethernet cables from the router. Both computers are running Ubuntu 8.10 Intrepid. Thank you in advance.

---

### Post by Therion on 2009-04-14
I assume there are reasons you don't want to simply use a wireless connection from your router?

---

### Post by pbpersson on 2009-04-14
The topic to which you are referring is using the two-Ethernet port machine as a network bridge.

This means the machine will basically act as a tunnel - the machine on the other side will still need to get an IP address from the DHCP server.

[This is the only article I could find on this]("http://wiki.openzaurus.org/HowTos/Bridging_with_Ubuntu")

---

### Post by Platinumjam on 2009-04-14
> **Therion said:**
> I assume there are reasons you don't want to simply use a wireless connection from your router?

Yes the reception in my room is terrible. 

@ pbpersson: I tried this and it still doesn't work right. Does anyone know if a crossover cable is required to go from the first to the second computer?

---

### Post by pbpersson on 2009-04-14
Yes, you need a crossover cable - a regular cable will not work

---

### Post by Platinumjam on 2009-04-14
> **pbpersson said:**
> Yes, you need a crossover cable - a regular cable will not work

Thank you very much I just wanted to check before I went out and bought one. If I get the cable hooked up and running before this thread is gone I will report back on how its working. Thank you very much:D

---

