---
title: "home network + router"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by jmore9 on 2009-11-11
I have a winxp pro machine and a 9.10 that i wish to connect via a router.

The internet is on the 9.10.  I do not want the winxp pro machine to access the internet.

I have another ethernet card - Fast Ethernet 10/100 Network card , which has a NC100 ver 2.1 chipset.

When i connect the ubuntu machine to the router using the second ethernet card  ( the fast ethernet above ) , using auto dhcp on the router i should not have to many problems talking to the winxp machine.  Have i got this correct ?

Also with the 2nd ethernet card connected to the router which is not on the internet it should not try to connect via the 1st ethernet port ?

Thanks in advance for any info or help

---

### Post by dandnsmith on 2009-11-11
Are you saying that both machines connect to the router, and that the Ubuntu machine is accessing the internet, but not via the router - if so, then you can block the Windows machine easily.
If, however, the Ubuntu machine accesses the internet via the router, then you'll have a big problem, unless you can set up specific routes in the router so that the Windows machine can only talk to the other (not all can do this easily).

---

### Post by Iowan on 2009-11-11
> **jmore9 said:**
> When i connect the ubuntu machine to the router using the second ethernet card  ( the fast ethernet above ) , using auto dhcp on the router i should not have to many problems talking to the winxp machine.  Have i got this correct ? Depends on your definition of "talking"...  file sharing will probably require Samba. (Also assumes no driver problem with the card.)

Internet connection sharing would need to be set up to share the internet with the XP machine, so blocking it *should* be no problem.

---

