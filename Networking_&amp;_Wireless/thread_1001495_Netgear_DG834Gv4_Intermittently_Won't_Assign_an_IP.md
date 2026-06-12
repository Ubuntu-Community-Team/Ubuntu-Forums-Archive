---
title: "Netgear DG834Gv4 Intermittently Won't Assign an IP Adress (Ubuntu 8.10)"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by qwijibo on 2008-12-04
Hi, 
I'm still kind of new at the whole Linux thing (about six months or so) but I'm thoroughly enjoying it and have so far prided myself on the fact that, despite no previous knowledge, I haven't needed to ask anyone for help (Well other than Google ;)), but this is driving me up the wall...
I'm having a problem between my Netgear DG834Gv4 (Latest firmware) and my Belkin F5D5073 wireless card (Ralink chipset, using RT2860 in ndiswrapper) - every now and then I can connect to my network with zero hassle, but usually it takes many, many attempts to be assigned an IP from the router; if it even works, which is rarely...
I can get connected every time without encryption enabled, yet if WEP or WPA are enabled it starts to go through this rigmarole where it hangs on "Requesting a network address from the wireless network" until the connection is terminated.
When running dhclient in the terminal while trying to connect, it informs me that I have received no DHCP offers and goes back to sleep, yet the router and card are obviously communicating (Probably just to laugh at me or something).
I have tried both MAC address filtering and assigning a static IP to my machine to see if they help, but the only thing it did was help me to learn how to set them up.
I would just go without encryption if the connection never worked at all, but since it sometimes does I almost feel it's a matter of principle that I *fix. this. problem.*
I have literally *scraped* the internet trying to see if anyone else has had a similar problem, but to no avail, and I was hoping you guys might be able to help.
Just let me know if you need any more info about my setup, or anything else that can help me get to the bottom of this.

Cheers.

---

### Post by qwijibo on 2008-12-09
Anyone???

---

