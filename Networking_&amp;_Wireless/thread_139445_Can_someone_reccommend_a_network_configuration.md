---
title: "Can someone reccommend a network configuration?"
date: 2006-03-04
forum: Networking &amp; Wireless
---

### Post by JamesNorris on 2006-03-04
At the moment, I have two comps in my network, my girlfriend's windows XP box, and my ubuntu box. They're linked by a crossover cable and my comp connects to the internet directly through the modem. 
It's not the best solution, as CUPS won't share my usb printer with her windows box and she can't view my shares, no matter what guide I follow or anything, it simply doesn't work. 

In a few weeks, I'm getting a third comp, and old 800Mhz Athlon from my sister I plan on using to build LFS on. Catherine is also planning on getting a laptop for uni, so there may be as many as four comps on this network soon, and crossover will only work for the two. 

I want to get a wireless network up and running, and not have any of the comps connecting to the internet as a gateway, if possible, as it uses twice the electricity needed. I would also like to take the printer off of the comps and have all the computers access it remotely, if possible.

Can anyone reccommend a physical setup for this that would allow all these comps on the internet at the same time, access shares and printer and not have me need to play with ndiswrapper?

---

### Post by spd106 on 2006-03-05
Get a wireless router w/ ADSL modem, have a look at this wiki page for compatible [wifi cards]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards").
Unfortunately, you'll have to leave the USB printer attached to a PC, unless you get a printer server.

---

### Post by mips on 2006-03-05
As spd106 suggested get one of those all singing, dancing, Wireless Ethernet Routers + 4port switch & with Built in ADSL modem.

Might want to consider a seperate print server for the printer and just maybe there is a multifunction router out there that has this built in too.

[http://www-uk.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=UK%2FLayout&cid=1127783372760&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www-uk.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=UK%2FLayout&cid=1127783372760&pagename=Linksys%2FCommon%2FVisitorWrapper)
[http://www-uk.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=UK%2FLayout&cid=1129751864505&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www-uk.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=UK%2FLayout&cid=1129751864505&pagename=Linksys%2FCommon%2FVisitorWrapper)
[http://www-uk.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=UK%2FLayout&cid=1123521944127&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www-uk.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=UK%2FLayout&cid=1123521944127&pagename=Linksys%2FCommon%2FVisitorWrapper)
[http://www-uk.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=UK%2FLayout&cid=1127783373300&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www-uk.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=UK%2FLayout&cid=1127783373300&pagename=Linksys%2FCommon%2FVisitorWrapper)
[http://www-uk.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=UK%2FLayout&cid=1123521939273&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www-uk.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=UK%2FLayout&cid=1123521939273&pagename=Linksys%2FCommon%2FVisitorWrapper)
[http://www.netgear.co.uk/wireless_adsl_routers.php](http://www.netgear.co.uk/wireless_adsl_routers.php)
[http://www.netgear.co.uk/netgear_print_servers.php](http://www.netgear.co.uk/netgear_print_servers.php)
[http://www.billion.uk.com/product/wireless/bipac7202gr2.htm](http://www.billion.uk.com/product/wireless/bipac7202gr2.htm)

---

### Post by jamesr on 2006-03-05
Some of the Dlink / linksys Wifi router include a printer server. But be aware of the following problem.  I have a GVC router with a built printer server and getting it to work with CUPS, I have been singlularly unsuccessful so far. Although I have heard of successes with the Dlink amd Linksys routers.

---

