---
title: "Cable Modem issues with Ubuntu"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by csete on 2010-03-21
I've recently been attempting to switch from DSL over to Cable modem to increase my internet speeds.  Unfortunately, the connection has been very unstable.  At first, I was pointing fingers at the cable company (Charter), but I'm beginning to believe it may actually be something with my network setup and possibly with Ubuntu.  

My setup is something like the following:

Cable
<-->  Cable Modem <--> NIC1 <--> Ubuntu <--> NIC2 <--> Private Network

The specifics of this setup:
* Cable Modem = Motorola Surfboard 6120
* NIC1 = Netgear GA311 Gigabit Ethernet
* Ubuntu = 9.10 = Linux setera 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
* NIC2 = nVidia Corporation CK804 Ethernet Controller (rev a3) (onboard ethernet)

The symptoms are that the network will be fine for some period of time (8m down/1m up).  After that period, the cable modem network will either:

* Drop to a very slow (< 1m down) speed
* Lose the connection altogether

Rebooting the cable modem will do nothing.  However, in some cases (not always), rebooting the Ubuntu box *will* solve the problem.  In some cases, the only way to get the cable modem to connect again is to remove the Ubuntu box from the cable modem and direct connect another machine.  In many of these cases, the cable modem is showing errors that make it appear that the problem is on the cable network, however I think that may be a red herring.

I work from home and depend on stable internet.  I really need to understand what is going on and could use any thoughts on how to proceed.  At the moment, I've replaced NIC1 with a Linksys LNE100TX (10/100) adapter in the Ubuntu box to see if that provides any further stability.  However, I'm not hopeful.

I could really use some help on this one.
Thanks,
Craig

---

### Post by csete on 2010-03-21
New NIC didn't help.  In fact, switching out the Ubuntu box didn't help either.  I threw a cheap Dynex 10/100M router in place of the Ubuntu box and it ended up in the same situation.  I'm losing my mind on this one and don't really know what the heck I can do next.  If I direct connect my Mac to the cable modem, all is well.  If I put a router in the connection, it won't stay stable despite the fact that it was stable all weekend long up until this point.

Help!

---

### Post by csete on 2010-03-21
Direct connect with my work Mac laptop and the same thing happened.  I'm at the point where I don't think I can blame anything on my internal network at this point. It is either something on the cable company's side or a bad cable modem.  Any suggestions still appreciated.

---

