---
title: "Need help with wireless routers"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by dwcbrq on 2011-06-14
Hello,

I just helped a friend install Ubuntu 10.10 on his computers in his home office.  He has a RICOH Aficiado 1515MF that I am helping him put on the network.

Currently, he is sharing wireless with his neighbor.  Also, his neighbor is running a network cable through his wall, so he can plug it into his Vonage box.

I have a Netgear Rangemax not in use.

So, what I am trying to do (or think I should be doing) is set up his NETGEAR in his office for his computers to connect to, as well as the printer.  Then I need to configure the NETGEAR to route any traffic that wants to get out to his neighbor's router.

Does anyone know how I should configure the NETGEAR?  Should the Vonage box sit between the neighbor's router and the NETGEAR?  Or, should it sit inside the NETGEAR?

I appreciate any help!

---

### Post by dandnsmith on 2011-06-14
I'm not entirely sure I have the picture, as I don't know what part the vonage box plays.
My setup is netgear router#1 connects to internet (and also some wired PCs) and is connected on the LAN side to netgear router#2 (on it's LAN side).
#2 has DHCP off, and has a static IP address outside the range which #1 allocates (but on the same subnet). #2 has (mostly) wireless PCs talking to it.

It all seems to work fine, once set up.

I couldn't get it to work using wireless between the 2 routers - probably because there is a facility lacking which some routers have.

HTH

---

### Post by dwcbrq on 2011-06-14
> **dandnsmith said:**
> I'm not entirely sure I have the picture, as I don't know what part the vonage box plays.
My setup is netgear router#1 connects to internet (and also some wired PCs) and is connected on the LAN side to netgear router#2 (on it's LAN side).
#2 has DHCP off, and has a static IP address outside the range which #1 allocates (but on the same subnet). #2 has (mostly) wireless PCs talking to it.

It all seems to work fine, once set up.

I couldn't get it to work using wireless between the 2 routers - probably because there is a facility lacking which some routers have.

HTH

He has a phone and fax machine plugged into a Vonage box.  Currently, the cable he shares with his neighbor, from his neighbor's wireless router, plugs into the Vonage box, and his computers hop on his neighbor's wireless.

---

### Post by dwcbrq on 2011-06-14
Also, I forgot to mention, his neighbor's wireless will connect to the NETGEAR via the internet cable.

---

### Post by dandnsmith on 2011-06-15
So, connect all your friends equipment to your netgear rangemax.
Connect the neigbours netgear to the rangemax via cable.
Ensure the rangemax DHCP is off.
See if it works - if it doesn't, then it's some routing adjustment to be done, but I don't think there will be any.

---

