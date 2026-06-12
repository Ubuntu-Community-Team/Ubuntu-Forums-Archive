---
title: "Lost internet when upgrading to hoary..."
date: 2005-02-28
forum: Networking &amp; Wireless
---

### Post by psyko-lefse on 2005-02-28
Just installed a fresh copy of ubuntu. The first thing i did was to upgrade it to hoary. When it was done with that, I rebooted. Now I dont have connection to the network. 
I try to activate the network-card in system/network, but it just stay activated for a sec, then the mark disappers. I tried setting up a new connection, but I still have the same problem. Help?

---

### Post by alastair on 2005-02-28
Who knows? You give no information to help diagnose.

At least supply :

- a description of your network
- how you connect - router? DSL modem? modem?
- ethernet card, wired/wireless etc.
- DHCP? static IP?

- output of :

ifconfig -a
route -n
cat /etc/network/interfaces

---

### Post by psyko-lefse on 2005-02-28
Sorry ](*,) 

> a description of your network-
Its a broadband connection to the web
>  how you connect - router? DSL modem? modem?
DSL modem via ethernet
> DHCP? static IP?
DHCP

My point is, it worked fine without any configuration before i upgraded to Hoary, now it dont ](*,) 

Will try upload the output tomorow, its a bit difficult without internet and only one computer :D

---

