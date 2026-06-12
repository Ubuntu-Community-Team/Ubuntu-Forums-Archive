---
title: "CUPS with Avahi; printer keeps disappearing"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by skullmunky on 2009-08-22
I have a CUPS printer attached to a server running Kubuntu 9.04.  In the web cups interface, I enabled printer sharing.  I have Avahi running. 

I try to print from my mac laptop - when I try to add the printer, it does appear in the list, but then soon after, it disappears.  When I try to add it on the mac laptop, it sits for a while gathering printer information, then disappears.

In avahi-discover on the server it remains listed for longer.  Sometimes I can even get a printout or two to go through from the laptop, but eventually it always stops working.

Where does CUPS actually put the avahi service it's publishing?  I don't see it in /etc/avahi/services.  :confused:

Both computers are connecting over wifi.  Server has a static IP on the LAN.

EDIT: oh, I think I just solved it.  In the network settings on my server, I had the two DNS servers for my ISP entered.  I added my router at the top of the list, apparently you have to have that for mDNS to work!  Also a bunch of my other Avahi stuff now works that didn't work before.  Hoorah!  :)  (Why isn't that documented anywhere, though?)

---

