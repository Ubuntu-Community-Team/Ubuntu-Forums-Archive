---
title: "Encore Wireless N / Ralink 2680 confusion"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by il_M50 on 2009-07-01
Hello-

I am a new user who started using ubuntu 9.04 as a way to help my son put together a computer he bought with "garage sale" parts on the cheap.  I was so impressed, I set it up as a dual boot on my laptop, and have found it a great alternative to Vista64.  Much more stable.  It has been fun getting it up and running, kind of like getting a new computer myself....  

My question relates to the wireless connection capabilities of the encore elwi-n pci card.  I am running a DLink dir-825 router, and my laptop has the intel 5100 card.  The intel card will connect at N speeds in both the 2.4 and 5 ghz modes using the default ubuntu driver and network manager.  I installed the encore pci card in the desktop we are building, and jaunty recognized it right away and gave it the ra2860 driver.  The signal strength and connection were very good, however the network manager reports a 54 mbs connection, and my router reports a "wireless g" connection.  I have tried switching from network manager to wicd, and that didn't work out so well (Wicd froze contantly, and couldn't establish any connection).  I made sure the wpa supplicant is in place, etc.  I have tried to get the ndis wrapper working with the windows driver, but haven't got that quite right yet.

It seems that others have reported similar issues with this card, but the threads i found all seemed to terminate without any real resolution.  Has anyone been able to successfully get this card to connect as the N card it should be, or am I stuck with it in G for now?  I don't mind spending more time working on it, if it is indeed possible, but I don't want to beat a dead horse, either.

Any advice greatly appreciated!

Scott

---

### Post by il_M50 on 2009-07-04
Ok, I havo seem gotten the windows driver to work with NDIS wrapper (thanks to the tutorial and the info about conflicting drivers).  Network manager shows a connection at 130 mbps with NDISwrapper as the driver, which I would be happy with.  My router, however, still reports this as a "G" connection, and shows a slower speed.  

Am I on the right track here, or might I still be missing something?

---

