---
title: "ICS for Ubuntu?"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by flintflake on 2006-06-20
I'm having fits getting my Netgear WG311v2 card to work with Ubuntu.  After 3 reinstalls, following several wiki's, and several choice words, it still doesn't work.  However, I have an idea...

I have an old IBM 765 laptop sitting around collecting dust.  It's like a P100 with 80MB RAM running Win98SE so there's not really much use for it.   I have several open PCI slots on my docking station and I was thinking about putting my wireless card and another NIC in the docking station and let my Ubuntu box use a "wired" connection.   How would I configure the NIC's so accomplish this?

Is it even possible?  I'm eager to learn Linux but I can't because I can't get it to see my network.

---

### Post by goodmaj on 2006-06-20
Neither Ubuntu or Xbuntu are going run well in 80 Megs of RAM.  I suggest that you look at Damn Small Linux(DSL).  It runs from a Live CD and offers the opportunity to install on your hard drive.  It is a Debian Linux like Ubuntu, but is a bare bones approach with out a lot graphics.  It uses very lean applications which will njot over tax the P100.

[http://damnsmalllinux.org](http://damnsmalllinux.org)

You will have to use ndiswrapper to get your wireless card working in DSL.

---

### Post by flintflake on 2006-06-20
I don't want to install Linux on the laptop.  I want to use Win98 as a bridge so I can access my network on Linux without using wireless.

Laptop = wired NIC and wireless NIC
Ubuntu = onboard NIC on board that will plug into wired NIC on laptop.  I'd like to be able to "see" my network through this connection.

Is that a better explanation?

---

