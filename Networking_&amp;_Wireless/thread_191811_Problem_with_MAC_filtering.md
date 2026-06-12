---
title: "Problem with MAC filtering"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by gammagoat on 2006-06-08
I'm trying to connect my Linux PC to a wireless net being served by a Linksys WRT54G router. The administrator is not using encryption, but he is using MAC address filtering to grant permission only to PCs in his list. When the filtering is disabled, I connect just fine. When he turns on filtering, with my Hawking wifi device's MAC address entered properly onto his permission list, I cannot connect. In both cases the KDE desktop wireless assistant sees his network with plenty of strength.
Any tips on how to fix this MAC filtering issue? Is it possible for wireless assistant to grab the wrong MAC address on my side? 
Many thanks.

---

### Post by nanotube on 2006-06-08
[QUOTE=gammagoat]I'm trying to connect my Linux PC to a wireless net being served by a Linksys WRT54G router. The administrator is not using encryption, but he is using MAC address filtering to grant permission only to PCs in his list. When the filtering is disabled, I connect just fine. When he turns on filtering, with my Hawking wifi device's MAC address entered properly onto his permission list, I cannot connect. In both cases the KDE desktop wireless assistant sees his network with plenty of strength.
Any tips on how to fix this MAC filtering issue? Is it possible for wireless assistant to grab the wrong MAC address on my side? 
Many thanks.[/QUOTE]
well, you could try running "ifconfig" from a terminal, and look what is listed under the "hwaddr", and compare it to what is listed in the MAC list on the router...

---

