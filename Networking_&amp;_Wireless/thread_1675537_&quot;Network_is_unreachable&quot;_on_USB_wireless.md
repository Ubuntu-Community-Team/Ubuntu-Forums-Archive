---
title: "&quot;Network is unreachable&quot; on USB wireless"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by hodad on 2011-01-25
Having trouble getting my Netgear WNA1000 working thru wireless router.

Have tried lots of suggestions from other threads to no avail.  

Someone suggested that th routing table isn't set correctly, so have been trying to use the follwing to make the proper entry in the routing table:

sudo route add -net 192.168.0.1 netmask 255.255.255.0 dev wlan0

Result: error message stating with:
"route: netmask does not match route address"
followed by "Usage" instructions which tell me to do what I just did.

Any ideas on how I can populate my routing table with correct entry for my wireless card?

Not to complicate matters, but I temporarily turned off encryption on my router to eliminate that as a possibility until I get connected.  So maybe it'still trying to connect via encrypted mode - do I need to turn off encryption on my (client) end?

Thanks

---

### Post by grahammechanical on 2011-01-25
If you have turned off encryption in the router, you should also turn off encryption for that connection in Network manager. Otherwise it will be like trying to have a conversation with someone who not only speaks another language but is also talking nonsense as well.

Regards

---

### Post by hodad on 2011-01-25
That much I did do, still no connection. Seems that the terminal (command line) likes to fight with the GUI network manager, so I've been trying to stick with command line, but I did check the GUI network manager, and it seemed to be OK...

---

